# ak.wwise.core.profiler.getPerformanceMonitor

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the Performance Monitor statistics at a specific profiler capture time. Refer to Wwise Authoring Performance Monitor Counter Identifiers for the available counters.

在指定的 Profiler 捕获时间点获取 Performance Monitor 统计数据。可用计数器请参考 Wwise Authoring Performance Monitor Counter Identifiers。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for Performance Monitor data, or a Time Cursor. 查询时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of Performance Monitor counters. Performance Monitor 计数器数组。 |
| return[...] | object | Performance Monitor counter values. |
| return[...].name | string | name of the counter as shown in Wwise Authoring. 计数器名称。 |
| return[...].id | string | unique Id of the counter. 计数器唯一标识。 |
| return[...].value | number | value of counter at given time. 指定时间的计数器值。 |

## JSON-RPC 请求示例

### 示例：查询指定时间点的 Performance Monitor

Querying the Performance Monitor at a point in time.

```json
{
    "function": "ak.wwise.core.profiler.getPerformanceMonitor",
    "params": {
        "time": 30000
    }
}
```

## JSON-RPC 响应示例

```json
{
    "return": [
        {
            "name": "Number of Active Voices",
            "id": "activeVoices",
            "value": 42
        }
    ]
}
```

## 注意事项

- 可用计数器 ID 请参考 [Wwise Authoring Performance Monitor Counter Identifiers](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=globalcountersids.html)

## 相关函数

- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)

## 相关 Topic

- [Wwise Authoring Performance Monitor Counter Identifiers](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=globalcountersids.html)
- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getperformancemonitor.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getperformancemonitor.html)
