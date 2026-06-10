# ak.wwise.core.sourceControl.add

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Add files to source control. Equivalent to Mark for Add for Perforce.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| files | array | 是 | — | Array of files to add. File paths must be absolute. |
| files[...] | string | — | — | 要添加的文件的绝对路径。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| log | array (必填) | Array of log entries generated during the request. |
| log[...] | object | A log entry. |
| log[...].severity | string (必填) | 日志级别。可选值：Message、Warning、Error、Fatal Error。 |
| log[...].time | integer (必填) | UTC 时间戳（自 1970-01-01 午夜以来的秒数）。 |
| log[...].messageId | string (必填) | The message ID for the log item. |
| log[...].message | string (必填) | The description message of the log item. |
| log[...].platform | object | The platform ID and name for which the log item was reported（包含 id, name 等完整属性）。 |

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
            "messageId": "SourceControlAdded",
            "message": "File added to source control."
        }
    ]
}
```

## 注意事项

- 文件路径必须使用**绝对路径**。
- 对应 Perforce 的 "Mark for Add" 操作。

## 相关函数

- ak.wwise.core.sourceControl.checkOut
- ak.wwise.core.sourceControl.commit
- ak.wwise.core.sourceControl.revert

## 相关 Topic

- 版本控制（Source Control）
- Perforce 集成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_add.html
