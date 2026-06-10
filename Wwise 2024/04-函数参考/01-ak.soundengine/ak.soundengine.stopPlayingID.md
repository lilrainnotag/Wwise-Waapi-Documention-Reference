# ak.soundengine.stopPlayingID

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::StopPlayingID`

## 概述

Stops the current content, associated to the specified playing ID, from playing. See AK::SoundEngine::StopPlayingID.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| playingId | integer | 是 | （无） | Playing ID to be stopped. Unsigned Integer 32-bit. Range: [0,4294967295] |
| transitionDuration | integer | 是 | （无） | Fade duration (ms). Integer 32-bit. Range: [-2147483648,2147483647] |
| fadeCurve | integer | 是 | （无） | Curve type to be used for the transition. Uses values from AkCurveInterpolation. Range: [0,9] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.stopPlayingID",
  "params": {
    "playingId": 42,
    "transitionDuration": 500,
    "fadeCurve": 4
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `playingId` 来自 `postEvent` 的返回值
- `transitionDuration` 为淡出时长（毫秒）
- `fadeCurve` 取值来自 `AkCurveInterpolation` 枚举，范围 [0,9]
- 所有参数均为必填

## 相关函数

- [ak.soundengine.postEvent](ak.soundengine.postEvent.md)
- [ak.soundengine.executeActionOnEvent](ak.soundengine.executeActionOnEvent.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_stopPlayingID.html
