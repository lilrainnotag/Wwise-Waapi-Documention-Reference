# ak.wwise.core.profiler.getCursorTime

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Returns the current time of the specified profiler cursor, in milliseconds.

返回指定 Profiler Cursor 的当前时间（毫秒）。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| cursor | string | 是 | — | Time Cursor from which to acquire the time. 要获取时间的 Time Cursor。可选值: `user`（用户可操作的 Cursor），`capture`（表示当前捕获的最新时间）。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | integer | The current position of the specified Time Cursor, in ms. 指定 Time Cursor 的当前位置（毫秒）。 |

## JSON-RPC 请求示例

```json
{
    "function": "ak.wwise.core.profiler.getCursorTime",
    "params": {
        "cursor": "capture"
    }
}
```

## JSON-RPC 响应示例

```json
{
    "return": 45230
}
```

## 注意事项

- `user` Cursor 是用户可在 Profiler 界面中手动拖动的时间光标
- `capture` Cursor 表示当前捕获会话的最新时间点
- （官网未提供示例）

## 相关函数

- [ak.wwise.core.profiler.getVoices](./getVoices.md)
- [ak.wwise.core.profiler.getBusses](./getBusses.md)
- [ak.wwise.core.profiler.getVoiceContributions](./getVoiceContributions.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getcursortime.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getcursortime.html)
