# ak.wwise.core.profiler.getVoices

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the voices at a specific profiler capture time.

在指定的 Profiler 捕获时间点获取 Voice 信息。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for voices, or a Time Cursor. 查询时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 范围: [0,*] |
| time | string | — | — | 可选值: `user`, `capture` |
| voicePipelineID | integer | 否 | — | The pipeline ID of a single voice to get. 要获取的单个 Voice 的 Pipeline ID。无符号 32 位整数。范围: [0, 4294967295] |

## Options

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | [pipelineID, gameObjectID, objectGUID] | Members to return for each voice. 每个 Voice 要返回的成员。 |
| return[...] | string | — | — | 可选值: `pipelineID`, `playingID`, `soundID`, `gameObjectID`, `gameObjectName`, `objectGUID`, `objectName`, `playTargetID`, `playTargetGUID`, `playTargetName`, `baseVolume`, `gameAuxSendVolume`, `envelope`, `normalizationGain`, `lowPassFilter`, `highPassFilter`, `priority`, `isStarted`, `isVirtual`, `isForcedVirtual` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of voices. Voice 数组。 |
| return[...] | object | A playing voice. 一个正在播放的 Voice。 |
| return[...].pipelineID | integer (32-bit) | Pipeline ID of the voice. 范围: [0, 4294967295] |
| return[...].playingID | integer (32-bit) | Playing ID of the voice. |
| return[...].soundID | integer (32-bit) | Short ID of the sound object. |
| return[...].gameObjectID | integer (64-bit) | Game Object ID corresponding to the voice. |
| return[...].gameObjectName | string | Game Object Name. |
| return[...].objectGUID | string | Object GUID (格式: {aabbcc00-...}). |
| return[...].objectName | string | Object Name. |
| return[...].playTargetID | integer (32-bit) | Short ID of the play target object. |
| return[...].playTargetGUID | string | GUID of the play target object. |
| return[...].playTargetName | string | Name of the play target object. |
| return[...].baseVolume | number | Voice volume in dB (including HDR attenuation). |
| return[...].gameAuxSendVolume | number | Volume send to auxiliary bus in dB. |
| return[...].envelope | number | Current analyzed envelope value in dB. |
| return[...].normalizationGain | number | Loudness normalization and make-up gain in dB. |
| return[...].lowPassFilter | number | Low-Pass Filter applied to the voice. |
| return[...].highPassFilter | number | High-Pass Filter applied to the voice. |
| return[...].priority | integer (8-bit) | Priority given to the voice. 范围: [-128, 127] |
| return[...].isStarted | boolean | True if the voice has started playing. |
| return[...].isVirtual | boolean | True if the voice is virtual. |
| return[...].isForcedVirtual | boolean | True if the voice was forced as virtual. |

## JSON-RPC 请求示例

### 示例：查询指定时间点的 Sound 名称

Querying the sound names at a point in time

```json
{
    "function": "ak.wwise.core.profiler.getVoices",
    "params": {
        "time": "capture"
    },
    "options": {
        "return": [
            "objectName"
        ]
    }
}
```

## JSON-RPC 响应示例

```json
{
    "return": [
        {
            "objectName": "Explosion"
        },
        {
            "objectName": "Footstep"
        }
    ]
}
```

## 注意事项

- `return` options 默认返回 pipelineID、gameObjectID 和 objectGUID
- `voicePipelineID` 可用于过滤单个 Voice
- 需要先调用 `startCapture` 进行数据捕获

## 相关函数

- [ak.wwise.core.profiler.getBusses](./getBusses.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.getVoiceContributions](./getVoiceContributions.md)
- [ak.wwise.core.profiler.getAudioObjects](./getAudioObjects.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getvoices.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getvoices.html)
