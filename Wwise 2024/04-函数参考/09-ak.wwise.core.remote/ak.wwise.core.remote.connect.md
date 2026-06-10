# ak.wwise.core.remote.connect

▎ **命名空间**: ak.wwise.core.remote

## 概述

Connects the Wwise Authoring application to a Wwise Sound Engine running executable or to a saved profile file. The host must be running code with communication enabled. If only "host" is provided, Wwise connects to the first Sound Engine instance found. To distinguish between different instances, you can also provide the name of the application to connect to.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| host | string | 是 | — | The host to connect to. 可以是计算机名、IPv4 地址、IP:PORT 对、或已保存的 capture 文件（.prof）的完整路径。使用 127.0.0.1 连接本地。 |
| appName | string | 否 | — | The Application Name（来自 Remote Connection 对话框或 ak.wwise.core.remote.getAvailableConsoles）。当运行多个 Sound Engine 实例时用于区分。 |
| commandPort | integer | 否 | — | The command port. 当多个 Sound Engine 实例共享相同 appName 时用于区分。Unsigned Integer 16-bit，范围: [0, 65535]。需与 appName 配合使用。 |
| notificationPort | integer | 否 | — | Unused（未使用）。Unsigned Integer 16-bit，范围: [0, 65535]。 |

## 返回值

（官网未提供 — 连接成功时不返回特定数据）

## JSON-RPC 请求示例

### 连接到本地游戏

```json
{
    "host": "127.0.0.1"
}
```

### 连接到指定的 Sound Engine 实例

```json
{
    "host": "192.168.1.100",
    "appName": "MyGame"
}
```

### 连接到已保存的 profiler 文件

```json
{
    "host": "C:\\Captures\\session.prof"
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 目标主机必须运行启用了通信的 Wwise Sound Engine 代码。
- 如果只提供 `host` 参数，Wwise 会连接到找到的第一个 Sound Engine 实例。
- 使用 `ak.wwise.core.remote.getAvailableConsoles` 可获取可用控制台列表，其中包含 `appName` 和 `commandPort` 信息。
- `host` 参数支持连接本地 profiler 文件（.prof），用于离线分析。

## 相关函数

- ak.wwise.core.remote.disconnect
- ak.wwise.core.remote.getAvailableConsoles
- ak.wwise.core.remote.getConnectionStatus
- ak.wwise.core.profiler.saveCapture

## 相关 Topic

- Remote Connection（远程连接）
- Sound Engine 实例

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_remote_connect.html
