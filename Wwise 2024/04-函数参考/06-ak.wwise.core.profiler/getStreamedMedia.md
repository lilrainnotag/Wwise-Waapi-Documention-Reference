# ak.wwise.core.profiler.getStreamedMedia

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the streaming media at a specific profiler capture time. This data can also be found in the Advanced Profiler, under the Streams tab. To ensure the Streams data is received, refer to ak.wwise.core.profiler.enableProfilerData.

在指定的 Profiler 捕获时间点获取流媒体信息。此数据也可在 Advanced Profiler 的 Streams 标签页中查看。需要先通过 `enableProfilerData` 启用 stream 数据类型。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for media, or a Time Cursor. 查询时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of Streams. 流媒体数组。 |
| return[...] | object | Information about how each stream is managed by the Wwise sound engine. |
| return[...].deviceName | string | The name of the device from which the stream emanates. 设备名称。 |
| return[...].streamName | string | The name given to the stream. 流名称。 |
| return[...].fileSize | integer | The size of the file being streamed. 文件大小。 |
| return[...].filePosition | number | The position of the stream within the file (percentage). 流在文件中的位置（百分比）。 |
| return[...].priority | integer | The priority of the stream. 流优先级。 |
| return[...].bandwidthTotal | integer | Total transfer rate in the last profiling frame (includes cache transfers). 总带宽（含缓存传输）。 |
| return[...].bandwidthLowLevel | integer | Low-level device transfer rate in the last profiling frame. 低级别设备带宽。 |
| return[...].referencedMemory | integer | Amount of memory referenced by the stream. 流引用的内存量。 |
| return[...].estimatedThroughput | integer | The estimated throughput of the stream. 流的估计吞吐量。 |
| return[...].active | boolean | True if the stream was active during the last profiling frame. 流在上个 Profiling 帧中是否活跃。 |
| return[...].targetBufferSize | integer | The streaming device's target buffer length. 目标缓冲区长度。 |
| return[...].bufferStatusBuffered | number | Portion of requested data buffered (percentage of target buffer). 已缓冲数据比例（目标缓冲百分比）。 |

## JSON-RPC 请求示例

### 示例：查询指定时间点的流媒体信息

Querying the Streamed Media at a point in time.

```json
{
    "function": "ak.wwise.core.profiler.getStreamedMedia",
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
            "deviceName": "Default",
            "streamName": "Music.wem",
            "fileSize": 5242880,
            "filePosition": 45.2,
            "priority": 50,
            "bandwidthTotal": 102400,
            "bandwidthLowLevel": 96000,
            "referencedMemory": 262144,
            "estimatedThroughput": 128000,
            "active": true,
            "targetBufferSize": 65536,
            "bufferStatusBuffered": 78.5
        }
    ]
}
```

## 注意事项

- 必须先通过 `enableProfilerData` 启用 `stream` 数据类型
- `bandwidthTotal` 包含所有传输（含 Stream Manager 缓存），而 `bandwidthLowLevel` 仅包含低级别设备传输
- `bufferStatusBuffered` 以百分比表示目标缓冲区已填充的比例

## 相关函数

- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.getLoadedMedia](./getLoadedMedia.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getstreamedmedia.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getstreamedmedia.html)
