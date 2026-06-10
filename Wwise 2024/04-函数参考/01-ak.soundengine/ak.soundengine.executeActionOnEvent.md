# ak.soundengine.executeActionOnEvent

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::ExecuteActionOnEvent`

## 概述

Executes an action on all nodes that are referenced in the specified event in a Play action. See AK::SoundEngine::ExecuteActionOnEvent.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| event | any of: string, string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name or Short ID of the event. string: The name of the object. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. integer: The Short ID of a Wwise Object. Unsigned Integer 32-bit. Range: [0,4294967295] |
| actionType | integer | 是 | （无） | Action to execute on all the elements that were played using the specified event. Uses values from AK::SoundEngine::AkActionOnEventType. Range: [0,4] |
| gameObject | integer | 是 | （无） | Associated game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| transitionDuration | integer | 是 | （无） | Fade duration (ms). Integer 32-bit. Range: [-2147483648,2147483647] |
| fadeCurve | integer | 是 | （无） | Use values from AkCurveInterpolation. Range: [0,9] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.executeActionOnEvent",
  "params": {
    "event": "{aabbcc00-1122-3344-5566-77889900aabb}",
    "actionType": 0,
    "gameObject": 1,
    "transitionDuration": 0,
    "fadeCurve": 0
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 所有参数均为必填
- `actionType` 取值范围 [0,4]，对应 `AK::SoundEngine::AkActionOnEventType` 枚举值
- `fadeCurve` 取值范围 [0,9]，对应 `AkCurveInterpolation` 枚举值
- `gameObject` 为64位无符号整数
- `event` 参数支持三种形式：GUID字符串、名称字符串、Short ID整数

## 相关函数

- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)
- [ak.soundengine.stopPlayingID](ak.soundengine.stopPlayingID.md)
- [ak.soundengine.postEvent](ak.soundengine.postEvent.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_executeActionOnEvent.html
