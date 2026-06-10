# ak.soundengine.seekOnEvent

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SeekOnEvent`

## 概述

Seeks inside all playing objects that are referenced in Play Actions of the specified Event. See AK::SoundEngine::SeekOnEvent.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| event | any of: string (name), string (GUID), integer (Short ID) | 否 | （官网未提供） | Either the ID (GUID), name, or Short ID of the Event. string: The name of the object. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. integer: The Short ID of a Wwise Object. Unsigned Integer 32-bit. Range: [0,4294967295] |
| gameObject | integer | 否 | （官网未提供） | Associated game object ID; use AK_INVALID_GAME_OBJECT to affect all game objects. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| position | integer | 否 | （官网未提供） | Desired position where playback should restart, in milliseconds. Integer 32-bit. Range: [-2147483648,2147483647] |
| percent | number | 否 | （官网未提供） | Desired position where playback should restart, expressed in a percentage of the file's total duration, between 0 and 1.f. See note above about infinite looping sounds. |
| seekToNearestMarker | boolean | 否 | （官网未提供） | If true, the final seeking position is made equal to the nearest marker. |
| playingId | integer | 否 | （官网未提供） | Specifies the playing ID for which the seek is to be applied. This results in the seek being applied only to active actions of the playing ID. Use AK_INVALID_PLAYING_ID or nothing, to seek on all active Actions of this Event ID. Unsigned Integer 32-bit. Range: [0,4294967295] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.seekOnEvent",
  "params": {
    "event": "Play_MyMusic",
    "gameObject": 1,
    "position": 1000
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 所有参数均为可选
- `position` 单位为毫秒，`percent` 为 0~1 之间的比例值
- `seekToNearestMarker` 设为 true 时会将最终位置对齐到最近的标记点
- `playingId` 用于精确控制哪个播放实例进行 seek，使用 `AK_INVALID_PLAYING_ID` 或不传则影响所有正在播放该 Event 的实例
- `gameObject` 使用 `AK_INVALID_GAME_OBJECT` 可影响所有游戏对象

## 相关函数

- [ak.soundengine.postEvent](ak.soundengine.postEvent.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)
- [ak.soundengine.stopPlayingID](ak.soundengine.stopPlayingID.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_seekOnEvent.html
