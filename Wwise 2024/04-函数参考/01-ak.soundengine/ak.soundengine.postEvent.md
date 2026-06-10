# ak.soundengine.postEvent

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::PostEvent`

## 概述

Asynchronously post an Event to the sound engine (by event ID). See AK::SoundEngine::PostEvent.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| event | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or Short ID of the Event. string: The name of the object. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. integer: The Short ID of a Wwise Object. Unsigned Integer 32-bit. Range: [0,4294967295] |
| gameObject | integer | 否 | （官网未提供） | The unique ID of the game object. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | integer | The playing ID of the Event launched, or AK_INVALID_PLAYING_ID if posting the event failed. Unsigned Integer 32-bit. Range: [0,4294967295] |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.postEvent",
  "params": {
    "event": "Play_MySound",
    "gameObject": 1
  }
}
```

## JSON-RPC 响应示例

```json
{
  "return": 42
}
```

## 注意事项

- `event` 参数为必填，支持三种形式：名称字符串、GUID字符串、Short ID整数
- `gameObject` 参数可选，指定关联的游戏对象
- 返回的 playing ID 可用于后续 `stopPlayingID`、`seekOnEvent`、`executeActionOnEvent` 等操作
- 如果 Event 发送失败，返回 `AK_INVALID_PLAYING_ID`

## 相关函数

- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)
- [ak.soundengine.executeActionOnEvent](ak.soundengine.executeActionOnEvent.md)
- [ak.soundengine.seekOnEvent](ak.soundengine.seekOnEvent.md)
- [ak.soundengine.stopPlayingID](ak.soundengine.stopPlayingID.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_postEvent.html
