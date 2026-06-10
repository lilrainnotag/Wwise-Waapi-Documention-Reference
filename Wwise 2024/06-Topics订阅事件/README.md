# Topics 订阅事件

## 概述

Wwise Authoring API (WAAPI) 支持 **Pub/Sub（发布/订阅）** 模式。除了远程过程调用（RPC），客户端还可以订阅 Topics，当 Wwise 中发生特定事件时，会主动推送通知给所有订阅者。这使 WAAPI 客户端能够与 Wwise 进程实时同步数据。

### WAMP Pub/Sub 机制

WAAPI 使用 **WAMP (Web Application Messaging Protocol)** 协议实现 Pub/Sub：

1. **订阅 (Subscribe)**：客户端通过 WAMP 协议订阅一个 Topic（如 `ak.wwise.core.object.created`）
2. **发布 (Publish)**：当 Wwise 内部触发对应事件时，自动发布消息
3. **回调 (Callback)**：所有订阅该 Topic 的客户端收到通知，执行指定的回调函数

### Return Options（返回选项）

大部分 Topic 支持 `return` 选项，可以在订阅时指定需要返回的数据字段，避免不必要的查询：

```json
{
    "return": ["id", "name", "path"]
}
```

订阅后，每次事件触发时只返回 `id`、`name`、`path` 三个字段。支持的 return 表达式包括：
- 内置访问器：`id`, `name`, `notes`, `type`, `path`, `parent`, `owner`, `isPlayable` 等
- 属性访问器：`@Volume`, `@Pitch` 等（单 `@` 返回对象属性值，双 `@@` 返回 override 源的值）
- 引用访问器：`TransitionRoot`, `PlaylistRoot` 等

## 订阅代码示例

### Python (waapi-client)

```python
from waapi import WaapiClient

client = WaapiClient()

# 定义回调函数
def on_object_created(channel, **kwargs):
    obj = kwargs.get("object", {})
    print(f"对象已创建: {obj.get('name')} (ID: {obj.get('id')})")

# 订阅 topic，指定返回字段
sub_id = client.subscribe(
    "ak.wwise.core.object.created",
    options={"return": ["id", "name", "type", "path"]},
    callback=on_object_created
)

# ... 执行其他操作 ...

# 取消订阅
client.unsubscribe(sub_id)

client.disconnect()
```

### JavaScript / WAMP

```javascript
// 使用 autobahn.js 等 WAMP 库
connection.session.subscribe(
    'ak.wwise.core.object.created',
    function (args, kwargs) {
        console.log('对象已创建:', kwargs.object);
    },
    { return: ['id', 'name', 'type', 'path'] }
);
```

## 取消订阅

- **手动取消**：调用 `unsubscribe()` 方法，传入订阅时返回的订阅 ID
- **自动取消**：当工程关闭时，大部分订阅会自动取消。但以下 Topic 例外，支持跨工程加载保持订阅：
  - `ak.wwise.core.project.loaded`
  - `ak.wwise.core.project.preClosed`
  - `ak.wwise.core.project.postClosed`

## 订阅最佳实践

1. **及时取消订阅**：不再需要监听事件时，务必调用 `unsubscribe()` 取消订阅，释放回调资源
2. **指定 return 字段**：使用 `return` 选项只请求必要的字段，减少数据传输量和 Wwise 内部查询开销
3. **避免在回调中执行耗时操作**：回调在 Wwise 的事件线程中执行，耗时操作会阻塞 Wwise UI。如需执行复杂逻辑，应将数据放入队列异步处理
4. **处理订阅失败**：订阅可能在工程未加载或 Wwise 未运行时失败，应妥善处理异常
5. **注意订阅生命周期**：工程关闭时大部分订阅自动失效，工程重新加载后需重新订阅（除上述 3 个豁免 Topic）
6. **propertyChanged 需要指定对象和属性**：`ak.wwise.core.object.propertyChanged` 在订阅时必须指定要监听的 `object` 和 `property`

## 章节索引

| 文件 | 内容 | Topic 数量 |
|------|------|-----------|
| [01-对象事件](01-对象事件.md) | ak.wwise.core.object.* | 12 |
| [02-工程事件](02-工程事件.md) | ak.wwise.core.project.* | 4 |
| [03-SoundBank事件](03-SoundBank事件.md) | ak.wwise.core.soundbank.* | 2 |
| [04-Profiler事件](04-Profiler事件.md) | ak.wwise.core.profiler.* | 6 |
| [05-Transport事件](05-Transport事件.md) | ak.wwise.core.transport.* | 1 |
| [06-UI与其他事件](06-UI与其他事件.md) | ak.wwise.ui.* / ak.wwise.core.audio.* / ak.wwise.core.log.* / ak.wwise.core.switchContainer.* / ak.wwise.debug.* | 7 |

## 官方文档链接

- [Topics 索引页](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics_index.html)
- [Subscribing to Topics 说明](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_subscribe.html)
- [Wwise Authoring API Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi.html)
