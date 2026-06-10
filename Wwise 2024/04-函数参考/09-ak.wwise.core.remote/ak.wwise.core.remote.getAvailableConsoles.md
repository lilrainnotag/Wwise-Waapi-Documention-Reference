# ak.wwise.core.remote.getAvailableConsoles

▎ **命名空间**: ak.wwise.core.remote

## 概述

Retrieves all consoles available for connecting Wwise Authoring to a Sound Engine instance.

## 参数

（无需参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| consoles | array (必填) | An array of remote consoles available. |
| consoles[...] | object | Describe the remote process. |
| consoles[...].name | string (必填) | Name of the remote console as returned by the executable. |
| consoles[...].platform | string (必填) | Platform of the remote console as returned by the executable. |
| consoles[...].customPlatform | string | Platform, as defined in the project platforms of the remote console. |
| consoles[...].host | string (必填) | The IPv4 of the connected host. 也可能是本地 profiler 文件路径。 |
| consoles[...].appName | string (必填) | The name of the connected application. 连接时用作区分不同 Sound Engine 实例。 |
| consoles[...].commandPort | integer (必填) | The command port. Unsigned Integer 16-bit，范围: [0, 65535]。 |

## JSON-RPC 请求示例

```json
{}
```

## JSON-RPC 响应示例

```json
{
    "consoles": [
        {
            "name": "MyGame (Windows)",
            "platform": "Windows",
            "customPlatform": "Windows",
            "host": "192.168.1.100",
            "appName": "MyGame",
            "commandPort": 24024
        }
    ]
}
```

## 注意事项

- 在调用 `ak.wwise.core.remote.connect` 之前，可以使用此函数获取可用的 Sound Engine 实例列表。
- 返回的 `appName` 和 `commandPort` 可以直接用于 `connect` 函数来连接特定实例。

## 相关函数

- ak.wwise.core.remote.connect
- ak.wwise.core.remote.disconnect
- ak.wwise.core.remote.getConnectionStatus

## 相关 Topic

- Remote Connection（远程连接）

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_remote_getavailableconsoles.html
