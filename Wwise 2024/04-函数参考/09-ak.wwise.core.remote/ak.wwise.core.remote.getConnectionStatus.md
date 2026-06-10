# ak.wwise.core.remote.getConnectionStatus

▎ **命名空间**: ak.wwise.core.remote

## 概述

Retrieves the connection status.

## 参数

（无需参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| isConnected | boolean (必填) | Indicates if the Wwise Authoring application is connected to a Wwise Sound Engine process. |
| status | string (必填) | The current connection status in text. |
| console | object | Describe the remote process（仅在已连接时返回）。 |
| console.name | string (必填) | Name of the remote console. |
| console.platform | string (必填) | Platform of the remote console. |
| console.customPlatform | string | Platform as defined in the project platforms. |
| console.host | string (必填) | The IPv4 of the connected host 或 profiler 文件路径。 |
| console.appName | string (必填) | The name of the connected application. |

## JSON-RPC 请求示例

```json
{}
```

## JSON-RPC 响应示例

### 已连接状态

```json
{
    "isConnected": true,
    "status": "Connected",
    "console": {
        "name": "MyGame (Windows)",
        "platform": "Windows",
        "customPlatform": "Windows",
        "host": "192.168.1.100",
        "appName": "MyGame"
    }
}
```

### 未连接状态

```json
{
    "isConnected": false,
    "status": "Not Connected"
}
```

## 注意事项

- 在未连接状态时，`console` 字段可能不存在或为 null。
- 可用于轮询检查连接状态是否发生变化。

## 相关函数

- ak.wwise.core.remote.connect
- ak.wwise.core.remote.getAvailableConsoles

## 相关 Topic

- Remote Connection（远程连接）

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_remote_getconnectionstatus.html
