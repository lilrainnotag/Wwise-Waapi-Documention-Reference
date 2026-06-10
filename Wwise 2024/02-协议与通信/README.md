# 02-协议与通信

Wwise Authoring API (WAAPI) 的协议与通信章节，涵盖 WAAPI 支持的通信协议、URI 命名规范和环境变量配置。

## 章节文件

| 文件 | 说明 |
|------|------|
| [01-WAMP协议详解.md](./01-WAMP协议详解.md) | WebSocket/WAMP 协议完整说明，包括连接建立、RPC 调用、订阅/发布模式 |
| [02-HTTP协议详解.md](./02-HTTP协议详解.md) | HTTP POST/JSON-RPC 协议说明，包括端点、请求/响应格式 |
| [03-URI命名规范.md](./03-URI命名规范.md) | WAAPI 函数 URI 命名体系，命名空间和分类说明 |
| [04-环境变量参考.md](./04-环境变量参考.md) | WAAPI 相关的环境变量、端口配置和安全设置参考 |

## 协议选择指南

| 特性 | WAMP | HTTP POST |
|------|------|-----------|
| 远程过程调用 (RPC) | ✅ 支持 | ✅ 支持 |
| 发布与订阅 (Pub/Sub) | ✅ 支持 | ❌ 不支持 |
| 双向通信 | ✅ 支持 | ❌ 单向 |
| 连接复用 | ✅ 单连接复用 | ❌ 每次请求新建 |
| 性能 | 最优 | 一般 |

> **来源**: [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)

## 默认端口

| 协议 | 默认端口 |
|------|----------|
| WAMP (WebSocket) | 8080 |
| HTTP POST | 8090 |

> **来源**: [Preparing to use the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html)
