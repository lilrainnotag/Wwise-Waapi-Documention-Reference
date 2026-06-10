# ak.wwise.core.sourceControl.getStatus

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Get the source control status of the specified files.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| files | array | 是 | — | Array of files for which to retrieve source control status. File paths must be absolute. |
| files[...] | string | — | — | 要查询状态的文件的绝对路径。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| result | array (必填) | Array of source control statuses. |
| result[...] | object | Source control status of a file. |
| result[...].status | string | Status of the file（文件在版本控制中的状态）。 |
| result[...].owner | string | Owner of the file（文件的当前检出者）。 |
| log | array (必填) | Array of log entries generated during the request. |

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
    "result": [
        {
            "status": "checkedOut",
            "owner": "john.doe"
        }
    ],
    "log": [
        {
            "severity": "Message",
            "time": 1574290800,
            "messageId": "SourceControlStatusSuccess",
            "message": "Status retrieved successfully."
        }
    ]
}
```

## 注意事项

- 文件路径必须使用**绝对路径**。
- `status` 字段返回文件在版本控制系统中的当前状态（如是否已检出、是否被他人锁定等）。
- `owner` 字段指示当前持有该文件的用户。

## 相关函数

- ak.wwise.core.sourceControl.getSourceFiles
- ak.wwise.core.sourceControl.checkOut

## 相关 Topic

- 版本控制（Source Control）
- Perforce 集成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_getstatus.html
