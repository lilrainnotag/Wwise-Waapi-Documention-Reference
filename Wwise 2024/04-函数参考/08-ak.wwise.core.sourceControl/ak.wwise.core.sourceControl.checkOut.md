# ak.wwise.core.sourceControl.checkOut

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Check out files from source control. Equivalent to Check Out for Perforce.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| files | array | 是 | — | Array of files to check out. File paths must be absolute. |
| files[...] | string | — | — | 要 checkout 的文件的绝对路径。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| log | array (必填) | Array of log entries generated during the request. |
| log[...] | object | A log entry. |
| log[...].severity | string (必填) | 日志级别。可选值：Message、Warning、Error、Fatal Error。 |
| log[...].time | integer (必填) | UTC 时间戳。 |
| log[...].messageId | string (必填) | The message ID for the log item. |
| log[...].message | string (必填) | The description message of the log item. |

## JSON-RPC 请求示例

```json
{
    "files": [
        "C:\\MyProject\\Actors\\Player.akd"
    ]
}
```

## JSON-RPC 响应示例

```json
{
    "log": [
        {
            "severity": "Message",
            "time": 1574290800,
            "messageId": "SourceControlCheckedOut",
            "message": "File checked out from source control."
        }
    ]
}
```

## 注意事项

- 文件路径必须使用**绝对路径**。
- 对应 Perforce 的 "Check Out"（p4 edit）操作。
- Checkout 后文件变为可编辑状态。

## 相关函数

- ak.wwise.core.sourceControl.add
- ak.wwise.core.sourceControl.commit
- ak.wwise.core.sourceControl.revert

## 相关 Topic

- 版本控制（Source Control）
- Perforce 集成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_checkout.html
