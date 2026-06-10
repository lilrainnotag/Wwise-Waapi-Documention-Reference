# ak.wwise.core.profiler.getVoiceContributions

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves all parameters affecting voice volume, highpass and lowpass for a voice path, resolved from pipeline IDs.

通过 Pipeline ID 解析 Voice 路径，获取影响 Voice 音量、高通和低通滤波的所有参数。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| voicePipelineID | number | 是 | — | The pipeline ID of the voice to get contributions from. 要获取贡献的 Voice Pipeline ID。范围: [0,*] |
| bussesPipelineID | array | 否 | — | An array of bus pipeline IDs. Bus Pipeline ID 数组。 |
| bussesPipelineID[...] | number | — | — | The pipeline IDs of busses belonging to a common voice path. Empty array defaults to dry path. 范围: [0,*] |
| time | one of: | 是 | — | Time in milliseconds to query, or a Time Cursor. 查询时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 范围: [0,*] |
| time | string | — | — | 可选值: `user`, `capture` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | object | The hierarchy of objects with parameters contributing to the voice. |
| return.volume | number | The volume difference applied as a contribution. |
| return.LPF | number | The LPF difference applied as a contribution. |
| return.HPF | number | The HPF difference applied as a contribution. |
| return.objects | array | A tree of contribution objects. |
| return.objects[...] | object | Identifies a Voice Inspector contribution. |
| return.objects[...].name | string | The name of the contribution. |
| return.objects[...].volume | number | The volume difference applied. |
| return.objects[...].LPF | number | The LPF difference applied. |
| return.objects[...].HPF | number | The HPF difference applied. |
| return.objects[...].children | array | An array of child objects (recursive). |
| return.objects[...].children[...] | object | A voice contribution object. |
| return.objects[...].parameters | array | An array of contribution parameters. |
| return.objects[...].parameters[...] | object | A contribution parameter (propertyType, reason, driver, driverValue, value). |

## JSON-RPC 请求示例

```json
{
    "function": "ak.wwise.core.profiler.getVoiceContributions",
    "params": {
        "voicePipelineID": 12345,
        "time": "capture"
    }
}
```

## JSON-RPC 响应示例

```json
{
    "return": {
        "volume": -6.0,
        "LPF": 0,
        "HPF": 0,
        "objects": [
            {
                "name": "Master Audio Bus",
                "volume": -6.0,
                "LPF": 0,
                "HPF": 0,
                "children": []
            }
        ]
    }
}
```

## 注意事项

- 必须先通过 `enableProfilerData` 启用 `voiceInspector` 数据类型
- `bussesPipelineID` 为空数组时默认使用 dry path
- 返回的对象树从顶层父对象排列到 Voice 对象

## 相关函数

- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.getVoices](./getVoices.md)
- [ak.wwise.core.profiler.getBusses](./getBusses.md)
- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getvoicecontributions.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getvoicecontributions.html)
