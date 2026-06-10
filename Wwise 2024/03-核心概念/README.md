# 03-核心概念

Wwise Authoring API (WAAPI) 核心概念章节，涵盖 JSON-RPC 通信协议格式、错误处理、Wwise 对象模型、标识符体系以及平台与语言概念。

## 文件索引

| 文件 | 内容 |
|------|------|
| [01-JSON-RPC格式规范.md](01-JSON-RPC格式规范.md) | JSON-RPC 2.0 请求/响应/错误格式、params 模式、批量调用 |
| [02-错误码与异常处理.md](02-错误码与异常处理.md) | 标准错误码、WAAPI 特有错误、重试策略、调试技巧 |
| [03-Wwise对象模型.md](03-Wwise对象模型.md) | Wwise 对象层级、类型系统、属性/引用/列表、对象关系 |
| [04-标识符体系.md](04-标识符体系.md) | GUID、ShortID、Path、Name 四种标识方式对比与转换 |
| [05-平台与语言概念.md](05-平台与语言概念.md) | 平台 Link/Unlink 机制、语言本地化、平台特定属性操作 |

## 关键概念速览

### 通信协议
WAAPI 支持三种通信方式：
- **WAMP** (WebSocket, 端口 8080)：支持 RPC 调用和发布/订阅，性能最优
- **HTTP POST** (端口 8090)：仅支持 RPC 调用
- **AK::Wwise::Plugin::Host::WaapiCall()**：在 Wwise 插件内调用

### 数据格式
所有数据以 JSON 格式传输，遵循类 JSON-RPC 2.0 的请求/响应模式。

### Wwise 对象
Wwise 工程中的所有元素都是对象，包括 Sound、Bus、Event、SoundBank 等 70+ 种类型，每种对象具有属性(Property)、引用(Reference)和列表(List)。

### 标识符
WAAPI 支持四种对象标识方式：GUID（最稳定）、Short ID（运行时）、Path（人类可读）、Name（不唯一）。

### 平台与语言
Wwise 支持多平台属性管理（Link/Unlink 机制）和多语言音频本地化。
