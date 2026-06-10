# Wwise Authoring API (WAAPI) 参考文档

> **Wwise 版本**: 2024.1.14.9084  
> **文档来源**: [Audiokinetic Public Library](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_index.html)  
> **构建日期**: 2026-06-10  
> **文档语言**: 简体中文

---

## 📋 文档导航

本参考文档库完整覆盖 Wwise Authoring API (WAAPI) 的所有功能，按模块化层级组织。

### 🏁 [01-概述与入门](01-概述与入门/)
- [01-WAAPI简介](01-概述与入门/01-WAAPI简介.md) — 什么是 WAAPI、适用场景、架构概览
- [02-启用与配置](01-概述与入门/02-启用与配置.md) — 启用 WAAPI、端口配置
- [03-快速入门](01-概述与入门/03-快速入门.md) — 第一个 WAAPI 调用（Ping → 获取项目信息 → 查询对象）
- [04-版本说明](01-概述与入门/04-版本说明.md) — 2024.1 版本变更、迁移注意事项

### 🔌 [02-协议与通信](02-协议与通信/)
- [01-WAMP协议详解](02-协议与通信/01-WAMP协议详解.md) — WebSocket/WAMP: 连接、RPC、Pub/Sub、会话管理
- [02-HTTP协议详解](02-协议与通信/02-HTTP协议详解.md) — HTTP POST/JSON-RPC: 请求格式、响应格式
- [03-URI命名规范](02-协议与通信/03-URI命名规范.md) — `ak.<namespace>.<category>.<function>` 命名体系
- [04-环境变量参考](02-协议与通信/04-环境变量参考.md) — 所有 `$(Waapi*)` 变量及使用场景

### 📐 [03-核心概念](03-核心概念/)
- [01-JSON-RPC格式规范](03-核心概念/01-JSON-RPC格式规范.md) — 请求/响应/错误格式、id 管理、批量调用
- [02-错误码与异常处理](03-核心概念/02-错误码与异常处理.md) — 标准 JSON-RPC 错误码、WAAPI 特有错误
- [03-Wwise对象模型](03-核心概念/03-Wwise对象模型.md) — 对象层级、WorkUnit、类型系统、属性/引用/列表
- [04-标识符体系](03-核心概念/04-标识符体系.md) — GUID、ShortID、路径、名称搜索的对比与选择
- [05-平台与语言概念](03-核心概念/05-平台与语言概念.md) — 平台 Link/Unlink、语言管理

### 📚 [04-函数参考](04-函数参考/)
按命名空间组织的完整函数参考，每个函数一个独立文档：

| # | 命名空间 | 函数数 | 说明 |
|---|---------|--------|------|
| 01 | [ak.soundengine](04-函数参考/01-ak.soundengine/) | 26 | 声音引擎 — 运行时控制 |
| 02 | [ak.wwise.core](04-函数参考/02-ak.wwise.core/) | 4 | 核心功能 — Ping/Info/Lua 脚本 |
| 03 | [ak.wwise.core.object](04-函数参考/03-ak.wwise.core.object/) | 24 | ⭐ 对象操作 — CRUD/查询/属性管理 |
| 04 | [ak.wwise.core.audio](04-函数参考/04-ak.wwise.core.audio/) | 8 | 音频导入与转换 |
| 05 | [ak.wwise.core.soundbank](04-函数参考/05-ak.wwise.core.soundbank/) | 5 | SoundBank 生成与管理 |
| 06 | [ak.wwise.core.profiler](04-函数参考/06-ak.wwise.core.profiler/) | 18 | 性能分析与数据捕获 |
| 07 | [ak.wwise.core.transport](04-函数参考/07-ak.wwise.core.transport/) | 6 | 传输控制（播放/停止/暂停） |
| 08 | [ak.wwise.core.sourceControl](04-函数参考/08-ak.wwise.core.sourceControl/) | 9 | 版本控制集成（Perforce/Git） |
| 09 | [ak.wwise.core.remote](04-函数参考/09-ak.wwise.core.remote/) | 4 | 远程连接管理 |
| 10 | [ak.wwise.core.undo](04-函数参考/10-ak.wwise.core.undo/) | 5 | 撤销/重做管理 |
| 11 | [ak.wwise.core.plugin](04-函数参考/11-ak.wwise.core.plugin/) | 3 | 插件信息查询 |
| 12 | [ak.wwise.core.sound](04-函数参考/12-ak.wwise.core.sound/) | 1 | 声音对象操作 |
| 13 | [ak.wwise.core.gameParameter](04-函数参考/13-ak.wwise.core.gameParameter/) | 1 | 游戏参数设置 |
| 14 | [ak.wwise.core.blendContainer](04-函数参考/14-ak.wwise.core.blendContainer/) | 4 | 混合容器与混合轨道 |
| 15 | [ak.wwise.core.switchContainer](04-函数参考/15-ak.wwise.core.switchContainer/) | 3 | Switch 容器分配管理 |
| 16 | [ak.wwise.core.audioSourcePeaks](04-函数参考/16-ak.wwise.core.audioSourcePeaks/) | 2 | 音频波形峰值数据 |
| 17 | [ak.wwise.core.log](04-函数参考/17-ak.wwise.core.log/) | 3 | 日志管理 |
| 18 | [ak.wwise.core.project](04-函数参考/18-ak.wwise.core.project/) | 1 | 工程保存 |
| 19 | [ak.wwise.ui](04-函数参考/19-ak.wwise.ui/) | 3 | UI 操作（选中对象/截图） |
| 20 | [ak.wwise.ui.commands](04-函数参考/20-ak.wwise.ui.commands/) | 4 | 命令注册与执行 |
| 21 | [ak.wwise.ui.layout](04-函数参考/21-ak.wwise.ui.layout/) | 13 | 窗口布局管理 |
| 22 | [ak.wwise.ui.project](04-函数参考/22-ak.wwise.ui.project/) | 3 | 工程 UI 操作 |
| 23 | [ak.wwise.waapi](04-函数参考/23-ak.wwise.waapi/) | 3 | WAAPI 内省（元数据查询） |
| 24 | [ak.wwise.debug](04-函数参考/24-ak.wwise.debug/) | 8 | 调试与测试辅助 |
| 25 | [已废弃函数](04-函数参考/25-已废弃函数/) | 3 | ak.wwise.console.* (→ ak.wwise.ui.project) |

### 🔍 [05-WAQL查询语言](05-WAQL查询语言/)
- [01-快速入门](05-WAQL查询语言/01-快速入门.md) — 第一个 WAQL 查询
- [02-语法参考](05-WAQL查询语言/02-语法参考.md) — from/where/select/transform 完整语法
- [03-关键字详解](05-WAQL查询语言/03-关键字详解.md) — 对象表达式 + 值表达式 + 内置访问器
- [04-变换操作](05-WAQL查询语言/04-变换操作.md) — Transform 链式处理与典型模式
- [05-高级查询模式](05-WAQL查询语言/05-高级查询模式.md) — 复杂查询与性能优化

### 📡 [06-Topics订阅事件](06-Topics订阅事件/)
- [01-对象事件](06-Topics订阅事件/01-对象事件.md) — ak.wwise.core.object.* (12个topic)
- [02-工程事件](06-Topics订阅事件/02-工程事件.md) — ak.wwise.core.project.* (4个topic)
- [03-SoundBank事件](06-Topics订阅事件/03-SoundBank事件.md) — ak.wwise.core.soundbank.* (2个topic)
- [04-Profiler事件](06-Topics订阅事件/04-Profiler事件.md) — ak.wwise.core.profiler.* (6个topic)
- [05-Transport事件](06-Topics订阅事件/05-Transport事件.md) — ak.wwise.core.transport.* (1个topic)
- [06-UI与其他事件](06-Topics订阅事件/06-UI与其他事件.md) — ui/audio/log/switchContainer/debug (9个topic)

### 📤 [07-返回选项](07-返回选项/)
- [01-通用返回属性](07-返回选项/01-通用返回属性.md) — id/name/type/path/parent/children/notes 等内置访问器
- [02-音频属性返回](07-返回选项/02-音频属性返回.md) — @Volume/@Pitch/@OutputBus 等
- [03-特殊返回选项](07-返回选项/03-特殊返回选项.md) — platform/language 参数、audioPeaks、workunit 等

### 💡 [08-常见模式与最佳实践](08-常见模式与最佳实践/)
- [01-项目查询模式](08-常见模式与最佳实践/01-项目查询模式.md)
- [02-批量操作模式](08-常见模式与最佳实践/02-批量操作模式.md)
- [03-音频导入工作流](08-常见模式与最佳实践/03-音频导入工作流.md)
- [04-SoundBank生成工作流](08-常见模式与最佳实践/04-SoundBank生成工作流.md)
- [05-性能监控模式](08-常见模式与最佳实践/05-性能监控模式.md)
- [06-事件订阅模式](08-常见模式与最佳实践/06-事件订阅模式.md)
- [07-版本控制与Lua集成](08-常见模式与最佳实践/07-版本控制与Lua集成.md)

### 📦 [09-对象类型参考](09-对象类型参考/)
- [01-声音对象](09-对象类型参考/01-声音对象.md) — Sound/Sound SFX/Sound Voice
- [02-容器对象](09-对象类型参考/02-容器对象.md) — Random/Sequence/Switch/Blend Container
- [03-音乐对象](09-对象类型参考/03-音乐对象.md) — MusicSegment/Playlist/Switch Container
- [04-总线与效果器](09-对象类型参考/04-总线与效果器.md) — AudioBus/AuxBus/Effect
- [05-事件与动作](09-对象类型参考/05-事件与动作.md) — Event/Action
- [06-游戏同步与工程对象](09-对象类型参考/06-游戏同步与工程对象.md) — GameParameter/State/Switch/Trigger/WorkUnit

### 🔧 [10-故障排除](10-故障排除/)
- [01-常见错误码](10-故障排除/01-常见错误码.md)
- [02-连接与配置问题](10-故障排除/02-连接与配置问题.md)
- [03-常见问题FAQ](10-故障排除/03-常见问题FAQ.md)

---

## 🚀 快速开始

### 测试连接
```json
{"id": 1, "jsonrpc": "2.0", "method": "ak.wwise.core.ping", "params": {}}
```

### 获取工程信息
```json
{"id": 1, "jsonrpc": "2.0", "method": "ak.wwise.core.getProjectInfo", "params": {}}
```

### 查询对象
```json
{
    "id": 1, "jsonrpc": "2.0",
    "method": "ak.wwise.core.object.get",
    "params": {
        "from": {"path": ["\\Actor-Mixer Hierarchy"]},
        "options": {"return": ["id", "name", "type", "path"]}
    }
}
```

---

## 📊 统计概览

| 类别 | 数量 |
|------|------|
| 章节 | 10 |
| 命名空间 | 25（含1个已废弃） |
| 函数总数 | 164 |
| Topic 总数 | 32 |
| 协议 | 2（WAMP + HTTP） |
| 文档总大小 | ~800KB |

---

## 🔗 官方资源

- [Wwise Authoring API Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_index.html)
- [WAAPI Functions Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_functions_index.html)
- [WAAPI Topics Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics_index.html)
- [Using the Wwise Authoring Query Language (WAQL)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waql_introduction.html)

---

> **注意**: 本文档基于 Wwise 2024.1.14.9084 版本。API 可能在不同版本间有所变化。建议始终参考官方 Audiokinetic 文档获取最准确的信息。
