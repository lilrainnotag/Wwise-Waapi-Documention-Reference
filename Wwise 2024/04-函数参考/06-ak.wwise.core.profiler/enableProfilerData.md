# ak.wwise.core.profiler.enableProfilerData

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Specifies the type of data you want to capture. Overrides the user's profiler settings.

指定要捕获的 Profiler 数据类型，会覆盖用户在 Wwise 中的 Profiler 设置。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| dataTypes | array | 是 | — | An array of data types. 一个数据类型数组。 |
| dataTypes[...] | object | — | — | The data type and enable status. 数据类型及其启用状态。 |
| dataTypes[...].dataType | string | 是 | — | Specifies the type of data you want to capture. 指定要捕获的数据类型。Possible values（可选值）: `cpu`, `memory`, `stream`, `voices`, `listener`, `obstructionOcclusion`, `markersNotification`, `soundbanks`, `loadedMedia`, `preparedObjects`, `preparedGameSyncs`, `interactiveMusic`, `streamingDevice`, `meter`, `auxiliarySends`, `apiCalls`, `spatialAudio`, `spatialAudioRaycasting`, `voiceInspector`, `audioObjects`, `gameSyncs` |
| dataTypes[...].enable | boolean | 否 | true | Enable (true) or disable (false) capture for this type of profiler data. 启用(true)或禁用(false)对此类 Profiler 数据的捕获。默认值为 true。 |

## 返回值

(官网未提供 - 该函数无返回值，调用后返回空对象 {})

## JSON-RPC 请求示例

### 示例 1：启用 Profiler 数据

Enable "Voices Data"

```json
{
    "function": "ak.wwise.core.profiler.enableProfilerData",
    "params": {
        "dataTypes": [
            {
                "dataType": "voices",
                "enable": true
            }
        ]
    },
    "options": {}
}
```

### 示例 2：禁用 Profiler 数据

Disable "Voices Data"

```json
{
    "function": "ak.wwise.core.profiler.enableProfilerData",
    "params": {
        "dataTypes": [
            {
                "dataType": "voices",
                "enable": false
            }
        ]
    },
    "options": {}
}
```

### 示例 3：启用 getVoiceContributions 所需的 Profiler 数据

Enable "Voices Data" and "Voice Inspector Data" using the default value (true) for the enable property

```json
{
    "function": "ak.wwise.core.profiler.enableProfilerData",
    "params": {
        "dataTypes": [
            {
                "dataType": "voices"
            },
            {
                "dataType": "voiceInspector"
            }
        ]
    },
    "options": {}
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 此函数用于在开始性能分析捕获之前，指定需要收集的数据类型
- 调用 `startCapture` 之前必须先调用此函数设置需要的数据
- `dataType` 的参数值区分大小写，必须使用指定的选项值
- 未指定 `enable` 的数据类型默认启用（true）
- 该函数会覆盖用户在 Wwise Profiler 设置中的手动配置

## 相关函数

- [ak.wwise.core.profiler.startCapture](./startCapture.md)
- [ak.wwise.core.profiler.stopCapture](./stopCapture.md)
- [ak.wwise.core.profiler.getVoiceContributions](./getVoiceContributions.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_enableprofilerdata.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_enableprofilerdata.html)
