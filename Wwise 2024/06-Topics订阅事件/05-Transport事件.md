# Transport 事件

## 订阅机制

`ak.wwise.core.transport.stateChanged` 用于监听 Wwise Transport 控制器的播放状态变化。Transport 控制 Wwise 工程中音频对象的播放、停止、暂停等操作。

---

## 事件列表

### ak.wwise.core.transport.stateChanged

- **触发时机**：当 Transport 的状态发生变化时发送（如播放、停止、暂停等）
- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| transport | object | Transport 的状态信息 |
| transport.state | string | Transport 当前状态。可能的值：`"playing"`（播放中）、`"stopped"`（已停止）、`"paused"`（已暂停） |
| transport.object | object | 当前正在播放的对象信息 |
| transport.object.id | string | 播放对象的 GUID |
| transport.object.name | string | 播放对象的名称 |

- **WAMP 订阅示例**：

```python
from waapi import WaapiClient

client = WaapiClient()

def on_transport_state_changed(channel, **kwargs):
    transport = kwargs.get("transport", {})
    obj = transport.get("object", {})
    print(f"Transport 状态: {transport.get('state')} — 对象: {obj.get('name', '(无)')}")

sub_id = client.subscribe(
    "ak.wwise.core.transport.stateChanged",
    options={"return": ["transport.state", "transport.object.id", "transport.object.name"]},
    callback=on_transport_state_changed
)
```

- **WAMP 原始示例**：

```json
// 发布内容示例
{
    "transport": {
        "state": "playing",
        "object": {
            "id": "{aabbcc00-1122-3344-5566-77889900aabb}",
            "name": "Sound SFX"
        }
    }
}
```

- **注意事项**：
  - 可用于同步 Wwise Transport 状态到自定义工具或远程控制面板
  - 当 Transport 停止时，`transport.object` 可能为空（取决于具体场景）
  - 相关 API：`ak.wwise.core.transport.create`、`ak.wwise.core.transport.executeAction`、`ak.wwise.core.transport.getState`

---

## Transport 状态转换图

```
        play
  stopped ──────► playing
     ▲              │
     │  stop        │ pause
     │              ▼
     └────────── paused
           stop
```

## 官方文档链接

- [ak.wwise.core.transport.stateChanged](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_transport_statechanged.html)
