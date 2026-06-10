# ak.soundengine.unregisterGameObj

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::UnregisterGameObj`

## 概述

Unregisters a game object. Registering a game object twice does nothing. Unregistering it once unregisters it no matter how many times it has been registered. Unregistering a game object while it is in use is allowed, but the control over the parameters of this game object is lost. For example, say a sound associated with this game object is a 3D moving sound. It stops moving when the game object is unregistered, and there is no way to regain control over the game object. See AK::SoundEngine::UnregisterGameObj.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| gameObject | integer | 是 | （无） | ID of the game object to be unregistered. Valid range is [0, 0xFFFFFFFFFFFFFFDF]. Use AK_INVALID_GAME_OBJECT to unregister all game objects. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.unregisterGameObj",
  "params": {
    "gameObject": 1
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 取消注册只需调用一次，无论之前注册了多少次
- 在游戏对象仍在使用时取消注册是允许的，但会失去对该对象参数的控制
- 例如，与该游戏对象关联的 3D 移动声音在取消注册后将停止移动，且无法恢复控制
- 使用 `AK_INVALID_GAME_OBJECT` 可取消注册所有游戏对象

## 相关函数

- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_unregisterGameObj.html
