# ak.wwise.core.sourceControl.revert

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Revert changes to files in source control.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| files | array | 是 | — | Single file or array of files to revert. File paths must be absolute. |
| files[...] | string | — | — | 要 revert 的文件的绝对路径。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| log | array (必填) | Array of log entries generated during the request. |
| log[...] | object | A log entry（包含 severity, time, messageId, message）。 |

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
            "messageId": "SourceControlReverted",
            "message": "File reverted in source control."
        }
    ]
}
```

## 注意事项

- 文件路径必须使用**绝对路径**。
- Revert 会丢弃本地修改，将文件恢复到版本控制中的最新版本。
- 对应 Perforce 的 "Revert"（p4 revert）操作。

## 相关函数

- ak.wwise.core.sourceControl.checkOut
- ak.wwise.core.sourceControl.commit
- ak.wwise.core.sourceControl.add

## 相关 Topic

- 版本控制（Source Control）
- Perforce 集成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_revert.html
