# ak.wwise.core.profiler.getBusses

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the busses at a specific profiler capture time.

在指定的 Profiler 捕获时间点获取 Bus 信息。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for busses, or a Time Cursor. 查询 Bus 的时间（毫秒），或使用 Time Cursor。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |
| busPipelineID | integer | 否 | — | The pipeline ID of a single bus instance to get. 要获取的单个 Bus 实例的 Pipeline ID。无符号 32 位整数。范围: [0, 4294967295] |

## Options

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | [pipelineID, gameObjectID, objectGUID] | Members to return for each bus. 每个 Bus 要返回的成员。 |
| return[...] | string | — | — | 可选值: `pipelineID`, `mixBusID`, `objectGUID`, `objectName`, `gameObjectID`, `gameObjectName`, `deviceID`, `volume`, `downstreamGain`, `voiceCount`, `effectCount`, `depth` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of busses. Bus 数组。 |
| return[...] | object | Bus item. 一个 Bus 对象。 |
| return[...].pipelineID | integer (32-bit) | Pipeline ID of the bus. 范围: [0, 4294967295] |
| return[...].mixBusID | integer (64-bit) | Unique ID assigned to a mixing bus. 范围: [0, 18446744073709551615] 或 [-9223372036854775808, 9223372036854775807] |
| return[...].objectGUID | string | Object GUID corresponding to the bus. 格式: {aabbcc00-1122-3344-5566-77889900aabb} |
| return[...].objectName | string | Object Name corresponding to the bus. |
| return[...].gameObjectID | integer (64-bit) | Game Object ID corresponding to the voice. |
| return[...].gameObjectName | string | Game Object Name corresponding to the voice. |
| return[...].deviceID | integer (64-bit) | Audio Output device ID. 范围: [0, 18446744073709551615] |
| return[...].volume | number | Gain of the bus in dB. Bus 的增益（dB）。 |
| return[...].downstreamGain | number | Gain from current bus down to output in dB. 从当前 Bus 到输出的下游增益（dB）。 |
| return[...].voiceCount | integer (32-bit) | Number of voices routed to the bus. 路由到此 Bus 的 Voice 数量。 |
| return[...].effectCount | integer (32-bit) | Number of effects on the bus. Bus 上的 Effect 数量。 |
| return[...].depth | integer | Depth level of the bus in the pipeline. Bus 在管线中的深度级别。 |

## JSON-RPC 请求示例

### 示例：查询指定时间点的 Bus 名称

Querying the bus names at a point in time.

```json
{
    "function": "ak.wwise.core.profiler.getBusses",
    "params": {
        "time": 30000
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
            "objectName": "Master Audio Bus"
        },
        {
            "objectName": "Environmental"
        }
    ]
}
```

## 注意事项

- 必须在 `startCapture` 完成后才能调用
- `time` 参数可以是具体毫秒值或 `user`/`capture` Cursor
- `busPipelineID` 用于过滤特定的 Bus 实例
- `return` options 默认返回 pipelineID、gameObjectID 和 objectGUID

## 相关函数

- [ak.wwise.core.profiler.getVoices](./getVoices.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.getVoiceContributions](./getVoiceContributions.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getbusses.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getbusses.html)
