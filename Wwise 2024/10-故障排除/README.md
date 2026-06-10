# 10-故障排除

> Wwise Authoring API (WAAPI) 故障排除指南。涵盖错误码速查、连接与配置问题诊断、以及常见问题 FAQ。基于 Wwise 2024.1.14 官方文档编写。

---

## 目录

| 序号 | 文件 | 内容简介 |
|------|------|----------|
| 1 | [01-常见错误码.md](./01-常见错误码.md) | JSON-RPC 2.0 标准错误码速查表、WAAPI 特有错误、`error.data` 字段解读、错误排查流程 |
| 2 | [02-连接与配置问题.md](./02-连接与配置问题.md) | WAMP/HTTP 连接失败诊断、端口配置、防火墙设置、IP 白名单、CORS 配置、最大连接数、Mac 路径问题、WAAPI 状态验证方法 |
| 3 | [03-常见问题FAQ.md](./03-常见问题FAQ.md) | 18 个常见问题及解答，涵盖连接配置、编程语言选择、Mac 平台、故障排除、安全配置等 |

---

## 快速导航

### 想查找错误码？
→ [01-常见错误码.md](./01-常见错误码.md)
- 收到 `-32601` Method not found？
- 收到 `-32602` Invalid params？
- 收到 `-32700` Parse error？

### 连接不上 WAAPI？
→ [02-连接与配置问题.md](./02-连接与配置问题.md)
- Wwise 是否在运行？
- 端口是否正确？
- 防火墙是否阻止？
- 远程连接是否配置了 IP 白名单？
- 浏览器连接是否配置了 Origin？

### 遇到具体使用问题？
→ [03-常见问题FAQ.md](./03-常见问题FAQ.md)
- 如何启用 WAAPI？
- 支持哪些编程语言？
- Mac 上路径怎么处理？
- 模态对话框导致 WAAPI 无响应怎么办？

---

## 关键信息速览

| 项目 | 值 |
|------|-----|
| WAMP 端口 | 8080 |
| HTTP 端口 | 8090 |
| WAMP Realm | `realm1` |
| 最大 WAMP 连接数 | 20 |
| 最大 HTTP 连接数 | 20 |
| 默认允许的 IP | localhost (127.0.0.1 / ::1) |
| 端点路径 | `/waapi` |

---

## 参考来源

- [Preparing to use the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html)
- [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)
- [Wwise Authoring API Reference - Functions](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_functions_index.html)
- [JSON-RPC 2.0 Specification](https://www.jsonrpc.org/specification)
- [WAMP Protocol](https://wamp-proto.org)
