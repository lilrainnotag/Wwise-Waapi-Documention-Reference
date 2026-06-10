# ak.soundengine.postMsgMonitor

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::PostMsgMonitor`

## 概述

Display a message in the Profiler's Capture Log view.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| message | string | 是 | （无） | The message to display. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.postMsgMonitor",
  "params": {
    "message": "My debug message"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 消息会显示在 Wwise Profiler 的 Capture Log 视图中
- 用于调试目的，在运行时向 Profiler 发送自定义消息

## 相关函数

（官网未提供）

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_postMsgMonitor.html
