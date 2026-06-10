# ak.soundengine.registerGameObj

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::RegisterGameObj`

## 概述

Register a game object. Registering a game object twice does nothing. Unregistering it once unregisters it no matter how many times it has been registered. See AK::SoundEngine::RegisterGameObj.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| gameObject | integer | 是 | （无） | ID of the game object to be registered. Valid range is [0, 0xFFFFFFFFFFFFFFDF]. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| name | string | 是 | （无） | Name of the game object (for monitoring purpose). |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.registerGameObj",
  "params": {
    "gameObject": 1,
    "name": "MyGameObject"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 注册游戏对象是使用大多数声音引擎功能的前提条件
- 重复注册同一游戏对象不会产生额外效果
- 取消注册只需要调用一次 `unregisterGameObj`，无论注册了多少次
- `name` 参数用于监控/调试目的，在 Profiler 中显示

## 相关函数

- [ak.soundengine.unregisterGameObj](ak.soundengine.unregisterGameObj.md)
- [ak.soundengine.postEvent](ak.soundengine.postEvent.md)
- [ak.soundengine.setPosition](ak.soundengine.setPosition.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_registerGameObj.html
