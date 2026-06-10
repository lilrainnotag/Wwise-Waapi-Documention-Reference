# 04-函数参考

> **Wwise 版本**: 2024.1.14.9084  
> **函数总数**: 164  
> **命名空间**: 24（+1 已废弃）  
> **数据来源**: [Audiokinetic WAAPI Functions Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_functions_index.html)

---

## 命名空间速查表

| # | 命名空间 | 函数数 | 说明 |
|---|---------|--------|------|
| 01 | [ak.soundengine](01-ak.soundengine/) | 26 | 声音引擎 — 运行时 Game Object/Event/RTPC 控制 |
| 02 | [ak.wwise.core](02-ak.wwise.core/) | 4 | 核心功能 — Ping/GetInfo/GetProjectInfo/ExecuteLuaScript |
| 03 | [ak.wwise.core.object](03-ak.wwise.core.object/) | 24 | ⭐ 对象 CRUD / 属性管理 / WAQL 查询 |
| 04 | [ak.wwise.core.audio](04-ak.wwise.core.audio/) | 8 | 音频导入、转换、静音/独奏 |
| 05 | [ak.wwise.core.soundbank](05-ak.wwise.core.soundbank/) | 5 | SoundBank 生成与管理 |
| 06 | [ak.wwise.core.profiler](06-ak.wwise.core.profiler/) | 18 | 性能分析器 — 捕获/查询/Meter |
| 07 | [ak.wwise.core.transport](07-ak.wwise.core.transport/) | 6 | 传输控制 — 播放/停止/暂停/准备 |
| 08 | [ak.wwise.core.sourceControl](08-ak.wwise.core.sourceControl/) | 9 | 版本控制集成 — Add/CheckOut/Commit/Revert |
| 09 | [ak.wwise.core.remote](09-ak.wwise.core.remote/) | 4 | 远程连接/断开/状态查询 |
| 10 | [ak.wwise.core.undo](10-ak.wwise.core.undo/) | 5 | 撤销/重做管理 |
| 11 | [ak.wwise.core.plugin](11-ak.wwise.core.plugin/) | 3 | 插件信息查询 |
| 12 | [ak.wwise.core.sound](12-ak.wwise.core.sound/) | 1 | 活跃音频源切换 |
| 13 | [ak.wwise.core.gameParameter](13-ak.wwise.core.gameParameter/) | 1 | Game Parameter 范围设置 |
| 14 | [ak.wwise.core.blendContainer](14-ak.wwise.core.blendContainer/) | 4 | Blend Container/Track 管理 |
| 15 | [ak.wwise.core.switchContainer](15-ak.wwise.core.switchContainer/) | 3 | Switch Container 分配管理 |
| 16 | [ak.wwise.core.audioSourcePeaks](16-ak.wwise.core.audioSourcePeaks/) | 2 | 音频波形峰值数据 |
| 17 | [ak.wwise.core.log](17-ak.wwise.core.log/) | 3 | 日志添加/清除/获取 |
| 18 | [ak.wwise.core.project](18-ak.wwise.core.project/) | 1 | 工程保存 |
| 19 | [ak.wwise.ui](19-ak.wwise.ui/) | 3 | UI 操作 — 前台/截图/获取选中 |
| 20 | [ak.wwise.ui.commands](20-ak.wwise.ui.commands/) | 4 | 自定义命令注册/执行 |
| 21 | [ak.wwise.ui.layout](21-ak.wwise.ui.layout/) | 13 | 窗口布局管理 |
| 22 | [ak.wwise.ui.project](22-ak.wwise.ui.project/) | 3 | 工程 UI 操作（替代 console） |
| 23 | [ak.wwise.waapi](23-ak.wwise.waapi/) | 3 | WAAPI 内省 — getFunctions/getSchema/getTopics |
| 24 | [ak.wwise.debug](24-ak.wwise.debug/) | 8 | 调试辅助 — Assert/Automation/Tone 等 |
| 25 | [已废弃函数](25-已废弃函数/) | 3 | ak.wwise.console.project.* → ak.wwise.ui.project |

---

## 按功能域分类

### 🎮 声音引擎运行时 (ak.soundengine)
Game Object 注册、Event 发送、RTPC/Switch/State 控制、SoundBank 加载、3D 定位 — 共 26 个函数

### 📦 对象与项目管理 (ak.wwise.core.object + core + project + undo)
对象 CRUD、WAQL 查询、属性批量设置、撤销/重做 — 共 30 个函数

### 🎵 音频资产管线 (ak.wwise.core.audio + soundbank + audioSourcePeaks)
音频导入/转换、SoundBank 生成、波形数据分析 — 共 15 个函数

### 📊 分析与调试 (ak.wwise.core.profiler + debug + log)
性能捕获、CPU/内存/Voice 分析、调试辅助 — 共 29 个函数

### 🖥️ 工具集成 (ak.wwise.ui + sourceControl + remote + waapi)
UI 控制、版本控制、远程连接、API 内省 — 共 32 个函数

---

## 每个函数文件包含

- 函数概述
- 完整参数表（名称/类型/必填/默认值/说明）
- 返回值说明
- JSON-RPC 请求/响应示例（来自官网）
- 注意事项
- 相关函数与 Topic
- 官方文档链接

---

## 官方资源

- [WAAPI Functions Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_functions_index.html)
- [WAAPI Topics Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics_index.html)
- [Wwise Objects Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wwise_object_reference.html)
