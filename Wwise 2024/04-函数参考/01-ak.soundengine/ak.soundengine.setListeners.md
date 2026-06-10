# ak.soundengine.setListeners

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetListeners`

## 概述

Sets a single game object's active listeners. By default, all new game objects have no listeners active, but this behavior can be overridden with SetDefaultListeners(). Inactive listeners are not computed. See AK::SoundEngine::SetListeners.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| emitter | integer | 是 | （无） | Emitter game object. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| listeners | array of integer | 是 | （无） | Array of listener game object IDs. Game objects must have been previously registered. listeners [...] integer: A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setListeners",
  "params": {
    "emitter": 1,
    "listeners": [2, 3]
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 默认情况下，新注册的游戏对象没有活跃的监听器（可通过 `setDefaultListeners` 覆盖）
- 不活跃的监听器不会被计算，可以节省性能
- 监听器游戏对象必须事先通过 `registerGameObj` 注册

## 相关函数

- [ak.soundengine.setDefaultListeners](ak.soundengine.setDefaultListeners.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setListeners.html
