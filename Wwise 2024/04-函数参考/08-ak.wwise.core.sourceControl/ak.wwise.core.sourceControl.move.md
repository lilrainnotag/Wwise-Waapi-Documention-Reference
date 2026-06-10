# ak.wwise.core.sourceControl.move

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Move or rename files in source control. Always pass the same number of elements in files and newFiles. Equivalent to Move for Perforce.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| files | array | 是 | — | Array of files to rename or move. File paths must be absolute. |
| files[...] | string | — | — | 要移动/重命名的源文件绝对路径。 |
| newFiles | array | 是 | — | Array of new files. File paths must be absolute. |
| newFiles[...] | string | — | — | 目标文件绝对路径。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| log | array (必填) | Array of log entries generated during the request. |
| log[...] | object | A log entry（包含 severity, time, messageId, message）。 |

## JSON-RPC 请求示例

```json
{
    "files": [
        "C:\\MyProject\\Actors\\Player_old.akd"
    ],
    "newFiles": [
        "C:\\MyProject\\Actors\\Player_new.akd"
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
            "messageId": "SourceControlMoved",
            "message": "File moved/renamed in source control."
        }
    ]
}
```

## 注意事项

- `files` 和 `newFiles` 数组必须具有**相同数量的元素**，一一对应。
- 文件路径必须使用**绝对路径**。
- 对应 Perforce 的 "Move"（p4 move / p4 rename）操作。

## 相关函数

- ak.wwise.core.sourceControl.add
- ak.wwise.core.sourceControl.delete

## 相关 Topic

- 版本控制（Source Control）
- Perforce 集成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_move.html
