# ak.wwise.core.sourceControl.commit

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Commit files to source control. Equivalent to Submit Changes for Perforce.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| files | array | 是 | — | Array of files to commit. File paths must be absolute. |
| files[...] | string | — | — | 要提交的文件的绝对路径。 |
| message | string | 是 | — | Description message for the commit（提交说明/Changelist Description）。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| log | array (必填) | Array of log entries generated during the request. |
| log[...] | object | A log entry. |
| log[...].severity | string (必填) | 日志级别。 |
| log[...].time | integer (必填) | UTC 时间戳。 |
| log[...].messageId | string (必填) | The message ID for the log item. |
| log[...].message | string (必填) | The description message of the log item. |

## JSON-RPC 请求示例

```json
{
    "files": [
        "C:\\MyProject\\Actors\\Player.akd"
    ],
    "message": "Updated Player sound configurations"
}
```

## JSON-RPC 响应示例

```json
{
    "log": [
        {
            "severity": "Message",
            "time": 1574290800,
            "messageId": "SourceControlCommitted",
            "message": "File committed to source control."
        }
    ]
}
```

## 注意事项

- 文件路径必须使用**绝对路径**。
- `message` 参数为必填，对应 Perforce 的 Changelist Description。
- 对应 Perforce 的 "Submit Changes"（p4 submit）操作。

## 相关函数

- ak.wwise.core.sourceControl.add
- ak.wwise.core.sourceControl.checkOut
- ak.wwise.core.sourceControl.revert

## 相关 Topic

- 版本控制（Source Control）
- Perforce 集成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_commit.html
