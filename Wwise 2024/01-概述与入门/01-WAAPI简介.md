# 01-WAAPI 简介

## 什么是 WAAPI

**WAAPI（Wwise Authoring API）** 是用于与 Wwise Authoring 应用程序进行通信的 API。它允许客户端进程调用远程过程（Remote Procedure Calls）以及订阅感兴趣的主题通知（Publish & Subscribe），实现对 Wwise 项目的远程操控。

WAAPI 支持**双向通信**（bidirectional communications），使进程既可以调用远程过程，也可以订阅 Wwise 中发生变化的通知。

## WAAPI 可以做什么

根据 Audiokinetic 官方文档，WAAPI 提供的功能覆盖四个层面：

### 1. Wwise 项目操作（Wwise Project Manipulations）
- 检索对象及其信息
- 设置对象上的信息
- 创建新对象

### 2. 通用操作（Common Operations）
- 导入音频文件
- 生成 SoundBank
- 转换音频文件
- 播放 Wwise 对象

### 3. 用户界面访问与控制（User Interface Access and Control）
- 打开视图
- 访问当前选中项并修改
- 检查对象

### 4. SoundEngine 使用（SoundEngine Usage）
- 创建 Game Object 并设置位置
- 发送 Event
- 设置 Game Parameter 值、Switch 和 State

## 适用场景

WAAPI 可以集成到以下环境中：

- **游戏引擎**（Game Engine）
- **对话管理管线**（Dialogue Management Pipeline）
- **数字音频工作站 / DAW**：用于声音设计、编辑、对话录制或音乐制作
- **各类脚本**（All kinds of scripts）

WAAPI 可以用于：

- **自动化任务**：如导入音频文件或创建 Wwise 对象
- **远程控制 Wwise**：在移动设备上远程控制
- **实现自定义 Wwise 界面**（Custom Wwise Interfaces）
- **添加自定义功能**：通过 Defining Command Add-ons 为 Wwise 增加功能

## 架构概览

### 双协议支持

WAAPI 通过以下协议对外暴露服务：

| 协议 | 传输 | 特性 |
|------|------|------|
| **WAMP** (Web Application Messaging Protocol) | WebSocket | 双向通信，支持 RPC + Pub/Sub，最佳性能 |
| **HTTP POST** | HTTP | 支持 RPC，不支持 Pub/Sub |

官方推荐使用 **WAMP** 协议，因为它复用同一个 WebSocket 连接实现全会话通信，提供最佳的性能和体验。

### 三层功能架构

WAAPI 同 Wwise 的三个层级进行交互：

1. **Wwise User Interface（Wwise 用户界面）**：视图、选中对象、命令等
2. **Wwise Authoring Core（Wwise 创作核心）**：项目与对象、SoundBank、音频文件、传输控制等
3. **Wwise Sound Engine（Wwise 声音引擎）**：Game Object、Post Event、RTPC Value 等

### API 特性对比

| API 特性 | WAMP | HTTP POST | AK::Wwise::Plugin::Host::WaapiCall() |
|----------|------|-----------|--------------------------------------|
| Remote Procedure Calls（远程过程调用）| ✅ 支持 | ✅ 支持 | ✅ 支持 |
| Publish & Subscribe（发布订阅）| ✅ 支持 | ❌ 不支持 | ❌ 不支持 |
| 最优性能 | ✅ 是 | ❌ 否 | ✅ 是 |

### WAMP 协议

WAMP 是一个开放的 WebSocket 子协议，提供统一的应用路由。WAMP 实现在大多数流行编程语言中都可用。详见 [wamp-proto.org](https://wamp-proto.org)。

### WAAPI 插件内调用

在 Wwise Authoring 插件内部，可以使用 `AK::Wwise::Plugin::Host::WaapiCall()` 直接调用 WAAPI 函数。详见官方文档中的 *Using the Wwise Authoring API in Wwise Plug-ins*。

## 与旧版 SoundFrame 的关系

官方文档未在当前页面中显式提及与 SoundFrame 的直接对比关系。WAAPI 是 Wwise 当前的现代 API 体系，提供了比旧版更丰富的功能和更好的跨语言支持。

## 支持的工具

WAAPI 可用于与以下 Wwise 工具通信：

- **Wwise Authoring（Wwise 创作工具）**：完整的 GUI 环境
- **WwiseConsole**：命令行工具，通过 WAAPI 执行项目操作

通过 `ak.wwise.console.project.*` 命名空间（2024.1 中已迁移至 `ak.wwise.ui.project.*`）可实现对 WwiseConsole 的控制。

## 编程语言支持

以下编程语言具有官方推荐的 WAAPI 使用方案：

| 语言 | 推荐方案 | 难度 |
|------|----------|------|
| **C++** | AkAutobahn（Autobahn C++ 的分支，减少依赖，简化接口，高性能） | 中级 C++ |
| **C#** | WaapiClientCore 或 WaapiClientJson | 初级 C# |
| **JavaScript / TypeScript (Node.js LTS)** | waapi-client JS（基于 Autobahn JS，支持 async/await） | 初中级 JS |
| **JavaScript (浏览器)** | autobahn-browser | 中级 JS/Web |
| **Python 3.7+** | waapi-client Python（基于 Autobahn Python，大幅简化使用） | 初级 Python |
| **其他语言** | wamp-proto.org 上的 WAMP 实现，或直接使用 HTTP | 视语言而定 |

### C# 客户端的两种选择
- **WaapiClientCore**：仅依赖 .NET 4.5，无第三方引用，API 为字符串形式，兼容 Unity 2018.1+
- **WaapiClientJson**：依赖 Json.NET (NuGet)，提供 JSON 操作便利性

### 各语言示例路径
- C++ 示例：`SDK\samples\WwiseAuthoringAPI\cpp\SampleClient\SampleClient`
- C# 示例：`SDK\samples\WwiseAuthoringAPI\cs\WaapiClientSample`
- JS (Node.js) 示例：`SDK\samples\WwiseAuthoringAPI\js\hello-wwise-node-wamp`
- JS (浏览器) 示例：`SDK\samples\WwiseAuthoringAPI\js\hello-wwise-web-wamp`
- Python 示例：`SDK\samples\WwiseAuthoringAPI\python\waapi-client-py3`

## 注意事项

- WAAPI 在 Wwise 显示模态对话框（Modal Dialog）时不可用
- 最大同时连接数：WAMP 最多 20 个，HTTP POST 最多 20 个

## 官方文档链接

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi.html)
- [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)
