# ak.wwise.core.profiler.startCapture

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Starts the profiler capture and returns the time at the beginning of the capture, in milliseconds.

启动 Profiler 捕获，并返回捕获开始的时间（毫秒）。

## 参数

（无参数 - 该函数不需要参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | integer | The value of the Capture Time Cursor in ms. Capture Time Cursor 的值（毫秒）。 |

## JSON-RPC 请求示例

```json
{
    "function": "ak.wwise.core.profiler.startCapture"
}
```

## JSON-RPC 响应示例

```json
{
    "return": 0
}
```

## 注意事项

- 调用此函数前应通过 `enableProfilerData` 设置需要捕获的数据类型
- 返回的时间值对应 Capture Time Cursor 的初始位置
- 可通过 `ak.wwise.core.profiler.captureLog.itemAdded` Topic 订阅捕获日志事件

## 相关函数

- [ak.wwise.core.profiler.stopCapture](./stopCapture.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.getVoices](./getVoices.md)
- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)

## 相关 Topic

- [ak.wwise.core.profiler.captureLog.itemAdded](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_capturelog_itemadded.html)
- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_startcapture.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_startcapture.html)
