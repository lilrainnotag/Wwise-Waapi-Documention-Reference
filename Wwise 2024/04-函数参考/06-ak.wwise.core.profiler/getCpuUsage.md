# ak.wwise.core.profiler.getCpuUsage

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves CPU usage statistics at a specific profiler capture time. This data can also be found in the Advanced Profiler, under the CPU tab. To ensure the CPU data is received, refer to ak.wwise.core.profiler.enableProfilerData. The returned data includes "Inclusive" and "Exclusive" values, where "Inclusive" refers to the time spent in the element plus the time spent in any called elements, and "Exclusive" values pertain to execution only within the element itself.

在指定的 Profiler 捕获时间点获取 CPU 使用统计。此数据也可在 Advanced Profiler 的 CPU 标签页中找到。返回的数据包含 "Inclusive"（包含子调用）和 "Exclusive"（仅自身）两种 CPU 时间值。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for cpu data, or a Time Cursor. 查询 CPU 数据的时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of CPU statistics for each element. CPU 统计数组。 |
| return[...].elementName | string | The name of the element. 元素名称。 |
| return[...].id | integer | Class ID of the element. 元素的 Class ID。 |
| return[...].instances | integer | An estimation of the number of instances of the element. 元素实例数估计值。 |
| return[...].type | string | The type of element (e.g., Codec, Source, Effect, Mixer, Sink). 元素类型。 |
| return[...].percentInclusive | number | The percentage of CPU time spent in the element and its callees. 包含子调用的 CPU 百分比。 |
| return[...].percentExclusive | number | The percentage of CPU time spent only in the element itself. 仅自身执行的 CPU 百分比。 |
| return[...].millisecondsInclusive | number | Milliseconds spent in the element and its callees. 包含子调用的毫秒数。 |
| return[...].millisecondsExclusive | number | Milliseconds spent only in the element itself. 仅自身执行的毫秒数。 |

## JSON-RPC 请求示例

### 示例：查询指定时间点的 CPU 使用

Querying the CPU usage at a point in time.

```json
{
    "function": "ak.wwise.core.profiler.getCpuUsage",
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
            "elementName": "MySound",
            "id": 123456,
            "instances": 5,
            "type": "Source",
            "percentInclusive": 12.5,
            "percentExclusive": 3.2,
            "millisecondsInclusive": 1.25,
            "millisecondsExclusive": 0.32
        }
    ]
}
```

## 注意事项

- 必须先调用 `enableProfilerData` 启用 CPU 数据捕获才能获得结果
- Inclusive 时间包含元素自身及其调用的所有子元素的时间
- Exclusive 时间仅包含元素自身执行的时间
- 数据也可在 Wwise Advanced Profiler 的 CPU 标签页中查看

## 相关函数

- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getcpuusage.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getcpuusage.html)
