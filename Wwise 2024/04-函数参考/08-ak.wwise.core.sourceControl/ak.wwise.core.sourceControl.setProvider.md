# ak.wwise.core.sourceControl.setProvider

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Change the source control provider and credentials. This is the same setting as the Source Control option in the Project Settings dialog in Wwise.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| provider | string | 是 | — | Source control provider. 可选值：Perforce、Subversion、其他支持的版本控制系统、或空字符串（相当于 UI 中的 "No Source Control"）。 |
| server | string | 否 | localhost | Server name or address. |
| port | string | 否 | — | Server port. This value is required for Perforce. |
| username | string | 否 | — | User name. This value is required for Perforce. |
| password | string | 否 | — | User password or ticket. This value is required for Perforce. |
| workspace | string | 否 | — | Workspace name. This value is required for Perforce. |
| host | string | 否 | — | Host name. This value is required for Perforce. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| log | array (必填) | The entries of the log. |
| log[...] | object | A log entry（包含 severity, time, messageId, message）。 |

## JSON-RPC 请求示例

```json
{
    "provider": "Perforce",
    "server": "p4server.example.com",
    "port": "1666",
    "username": "john.doe",
    "password": "ticket_value",
    "workspace": "john_workspace",
    "host": "john-pc"
}
```

## JSON-RPC 响应示例

```json
{
    "log": [
        {
            "severity": "Message",
            "time": 1574290800,
            "messageId": "SourceControlProviderSet",
            "message": "Source control provider configured successfully."
        }
    ]
}
```

## 注意事项

- 此操作等同于 Wwise 中 **Project Settings → Source Control** 的设置。
- 对于 Perforce，`port`、`username`、`password`、`workspace` 和 `host` 为必填参数。
- 将 `provider` 设为空字符串 (`""`) 相当于选择 "No Source Control"（不使用版本控制）。
- 支持 Perforce 和 Subversion 以及其他 Wwise 支持的版本控制系统。

## 相关函数

- ak.wwise.core.sourceControl.getStatus
- ak.wwise.core.sourceControl.add

## 相关 Topic

- 版本控制（Source Control）
- Perforce 集成
- Subversion 集成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_setprovider.html
