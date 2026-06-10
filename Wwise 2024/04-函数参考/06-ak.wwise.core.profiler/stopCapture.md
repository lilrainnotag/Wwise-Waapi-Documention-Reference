# ak.wwise.core.profiler.stopCapture

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Stops the profiler capture and returns the time at the end of the capture, in milliseconds.

停止 Profiler 捕获，并返回捕获结束的时间（毫秒）。

## 参数

（无参数 - 该函数不需要参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | integer | The value of the Capture Time Cursor in ms. Capture Time Cursor 的值（毫秒）。 |

## JSON-RPC 请求示例

```json
{
    "function": "ak.wwise.core.profiler.stopCapture"
}
```

## JSON-RPC 响应示例

```json
{
    "return": 45230
}
```

## 注意事项

- 必须在 `startCapture` 之后调用
- 停止后可使用 `getCpuUsage`、`getVoices`、`getBusses` 等函数查询捕获的数据
- 停止后可使用 `saveCapture` 将数据保存为 .prof 文件

## 相关函数

- [ak.wwise.core.profiler.startCapture](./startCapture.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.saveCapture](./saveCapture.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_stopcapture.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_stopcapture.html)
