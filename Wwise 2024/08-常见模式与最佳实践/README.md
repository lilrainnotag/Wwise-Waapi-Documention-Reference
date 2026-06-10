# 08 - 常见模式与最佳实践

## 章节概述

本章节汇总了 Wwise 2024 WAAPI 在实际项目中的常见使用模式和最佳实践。每个子章节聚焦一个特定的工作流场景，提供从官方文档提取的 API 调用链和示例代码。

> **数据来源**: 所有示例代码和 API 参数均来自 Audiokinetic 官方文档 (Wwise 2024.1.14.9084)，通过浏览器直接访问官方页面提取。标注为"（官网未提供）"的内容在官方文档中未明确列出。

## 文件索引

| 文件 | 内容 |
|------|------|
| [01-项目查询模式.md](01-项目查询模式.md) | 遍历层级、按类型/名称/属性查找对象、WAQL 查询实战 |
| [02-批量操作模式.md](02-批量操作模式.md) | 使用 object.set 批量创建/修改对象、name conflict 模式、list 模式 |
| [03-音频导入工作流.md](03-音频导入工作流.md) | 编程化批量导入音频文件、创建层级结构、多语言导入 |
| [04-SoundBank生成工作流.md](04-SoundBank生成工作流.md) | 自动化 SoundBank 生成、多平台多语言、事件包含 |
| [05-性能监控模式.md](05-性能监控模式.md) | 使用 Profiler API 捕获和分析性能数据 |
| [06-事件订阅模式.md](06-事件订阅模式.md) | 实时监听工程变更、Topic 订阅实战 |
| [07-版本控制与Lua集成.md](07-版本控制与Lua集成.md) | sourceControl 工作流、executeLuaScript 使用模式 |

## 环境准备

所有示例均基于 Python WAAPI Client。首先确保正确连接：

```python
from waapi import WaapiClient

# 连接（默认 URL: ws://localhost:8080/waapi）
client = WaapiClient()

# 执行操作...

# 断开连接
client.disconnect()
```

## API 函数速查表

| 工作流 | 核心 API |
|--------|----------|
| 项目查询 | `ak.wwise.core.object.get` |
| 创建/修改对象 | `ak.wwise.core.object.set`、`ak.wwise.core.object.create` |
| 音频导入 | `ak.wwise.core.audio.import`、`ak.wwise.core.audio.importTabDelimited`、`ak.wwise.core.object.set` |
| SoundBank 生成 | `ak.wwise.core.soundbank.generate` |
| 性能监控 | `ak.wwise.core.profiler.startCapture`、`ak.wwise.core.profiler.get*` |
| 事件订阅 | `ak.wwise.core.object.created`、`ak.wwise.core.object.nameChanged` 等 Topic |
| Lua 脚本 | `ak.wwise.core.executeLuaScript` |
| 版本控制 | `ak.wwise.core.sourceControl.*` |
