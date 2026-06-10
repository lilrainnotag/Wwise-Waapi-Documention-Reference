# ak.wwise.core.profiler.saveCapture

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Saves profiler as a .prof file according to the given file path.

将 Profiler 捕获数据保存为指定路径的 .prof 文件。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| file | string | 是 | — | File path to a .prof file. .prof 文件的路径。 |

## 返回值

（官网未提供 - 该函数无返回值，调用成功返回空对象 {}）

## JSON-RPC 请求示例

### 示例：保存 Profiler 捕获

Saving a profiler capture

```json
{
    "function": "ak.wwise.core.profiler.saveCapture",
    "params": {
        "file": "C:\\Captures\\MyCapture.prof"
    }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 必须在 `stopCapture` 之后调用，用于保存已停止的捕获数据
- 文件路径必须可写
- 保存的文件可在 Wwise Profiler 中重新打开查看

## 相关函数

- [ak.wwise.core.profiler.startCapture](./startCapture.md)
- [ak.wwise.core.profiler.stopCapture](./stopCapture.md)
- [ak.wwise.core.remote.connect](../../05-ak.wwise.core.remote/connect.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_savecapture.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_savecapture.html)
