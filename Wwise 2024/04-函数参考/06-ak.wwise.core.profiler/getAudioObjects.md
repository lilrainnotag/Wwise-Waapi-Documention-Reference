# ak.wwise.core.profiler.getAudioObjects

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the Audio Objects at a specific profiler capture time.

在指定的 Profiler 捕获时间点获取 Audio Object 信息。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for Audio Objects, or a Time Cursor from which to acquire the time. 查询 Audio Object 的时间（毫秒），或使用 Time Cursor 获取时间。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |
| busPipelineID | integer | 否 | — | The pipeline ID of a Bus instance for which to get Audio Objects. 要获取 Audio Object 的 Bus 实例 Pipeline ID。无符号 32 位整数。范围: [0, 4294967295] |

## Options

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | [audioObjectID, busPipelineID, instigatorPipelineID, effectClassID] | Members to return for each Audio Object. 每个 Audio Object 要返回的成员列表。 |
| return[...] | string | — | — | 可选值: `busName`, `effectPluginName`, `audioObjectID`, `busPipelineID`, `gameObjectID`, `gameObjectName`, `audioObjectName`, `instigatorPipelineID`, `busID`, `busGUID`, `spatializationMode`, `x`, `y`, `z`, `spread`, `focus`, `channelConfig`, `effectClassID`, `effectIndex`, `metadata`, `rmsMeter`, `peakMeter` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of Audio Objects. Audio Object 数组。 |
| return[...] | object | An audio object. 一个 Audio Object。 |
| return[...].audioObjectID | integer (64-bit) | The ID of the Audio Object. |
| return[...].busPipelineID | integer (32-bit) | The Pipeline ID of the Bus instance. |
| return[...].gameObjectID | integer (64-bit) | The Game Object ID of the Bus instance. |
| return[...].gameObjectName | string | The name of the Game Object. |
| return[...].audioObjectName | string | The name of the Audio Object. |
| return[...].instigatorPipelineID | integer (32-bit) | The pipeline ID of the instigator. |
| return[...].busID | integer (32-bit) | The short ID of the Bus. |
| return[...].busGUID | string | The GUID of the Bus (格式: {aabbcc00-1122-3344-5566-77889900aabb}). |
| return[...].busName | string | Name of the bus instance. |
| return[...].effectPluginName | string | Name of the effect plug-in. |
| return[...].spatializationMode | integer (32-bit) | The spatialization mode (use `Ak3DSpatializationMode`). |
| return[...].x | number | The X value of the Audio Object position. |
| return[...].y | number | The Y value of the Audio Object position. |
| return[...].z | number | The Z value of the Audio Object position. |
| return[...].spread | number | The spread value (normalized). |
| return[...].focus | number | The focus value (normalized). |
| return[...].channelConfig | integer (32-bit) | The channel configuration. |
| return[...].effectClassID | integer (32-bit) | The Class ID of the effect. |
| return[...].effectIndex | integer (32-bit) | The index of the effect. |
| return[...].metadata | array | Array of metadata objects. |
| return[...].metadata[...].metadataClassID | integer (32-bit) | The class ID of the metadata. |
| return[...].metadata[...].metadataName | string | The name of the metadata. |
| return[...].metadata[...].sourceID | string | The ID (GUID) of the source object. |
| return[...].metadata[...].sourceShortID | integer (32-bit) | The short ID of the source object. |
| return[...].metadata[...].sourceName | string | The name of the source object. |
| return[...].rmsMeter | array of number | Array of RMS meter volume values (dB) per channel. |
| return[...].peakMeter | array of number | Array of Peak meter volume values (dB) per channel. |

## JSON-RPC 请求示例

### 示例 1：查询指定时间点的 Audio Object

Query instigator ID (pipeline ID) for the Audio Objects in the current capture session at 30 secs (30,000 milliseconds).

```json
{
    "function": "ak.wwise.core.profiler.getAudioObjects",
    "params": {
        "time": 30000
    },
    "options": {
        "return": [
            "audioObjectName"
        ]
    }
}
```

## JSON-RPC 响应示例

```json
{
    "return": [
        {
            "audioObjectName": "MyObject"
        },
        {
            "audioObjectName": "MyOtherObject"
        }
    ]
}
```

## 注意事项

- 必须在调用 `startCapture` 并完成捕获后才能获取 Audio Object 数据
- `time` 参数可以使用具体毫秒值或预定义的 Cursor (`user` 或 `capture`)
- `return` options 用于指定需要返回的 Audio Object 属性，默认返回 audioObjectID、busPipelineID、instigatorPipelineID 和 effectClassID
- 可以通过 `busPipelineID` 参数过滤特定 Bus 实例的 Audio Object

## 相关函数

- [ak.wwise.core.profiler.getBusses](./getBusses.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.getVoiceContributions](./getVoiceContributions.md)
- [ak.wwise.core.profiler.getVoices](./getVoices.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getaudioobjects.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getaudioobjects.html)
