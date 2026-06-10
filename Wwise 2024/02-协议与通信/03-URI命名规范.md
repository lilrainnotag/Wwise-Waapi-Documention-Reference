# 03 - URI 命名规范

## URI 格式

WAAPI 函数 URI 使用点号分隔的命名格式：

```
ak.<namespace>.<category>.<function>
```

| 组件 | 说明 | 示例 |
|------|------|------|
| `ak` | Audiokinetic 前缀，所有 WAAPI 函数均以此为前缀 | `ak` |
| `<namespace>` | 命名空间，表示功能域 | `wwise` |
| `<category>` | 类别，表示功能子域 | `core` |
| `<function>` | 函数名，使用驼峰命名法 | `getInfo` |

### 完整示例

```
ak.wwise.core.getInfo
ak.wwise.core.object.created
ak.wwise.ui.commands.execute
```

## 命名空间说明

WAAPI 的 URI 体系中，`ak` 为固定前缀，`wwise` 为固定命名空间。所有函数都位于 `ak.wwise.*` 下。

命名空间下的主要类别：

### wwise.core

核心功能，包括工程操作、对象管理、SoundBank 生成等。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.getInfo` | 获取 Wwise 版本信息 |
| `ak.wwise.core.log.get` | 获取日志 |
| `ak.wwise.core.log.itemAdded` | 日志项添加通知 (Topic) |
| `ak.wwise.core.ping` | 验证 WAAPI 连接状态 |

### wwise.core.object

对象操作函数。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.object.get` | 获取对象信息 |
| `ak.wwise.core.object.created` | 对象创建通知 (Topic) |
| `ak.wwise.core.object.nameChanged` | 对象名称变更通知 (Topic) |

### wwise.core.project

工程级别操作。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.project.loaded` | 工程加载通知 (Topic) |
| `ak.wwise.core.project.saved` | 工程保存通知 (Topic) |
| `ak.wwise.core.project.preClosed` | 工程关闭前通知 (Topic) |

### wwise.core.soundbank

SoundBank 相关操作。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.soundbank.generate` | 生成 SoundBank |
| `ak.wwise.core.soundbank.generated` | 单个 SoundBank 生成完成通知 (Topic) |
| `ak.wwise.core.soundbank.generationDone` | 全部 SoundBank 生成完成通知 (Topic) |

### wwise.core.transport

传输控制。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.transport.stateChanged` | 传输状态变更通知 (Topic) |

### wwise.core.profiler

性能分析器。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.profiler.stateChanged` | 状态变更通知 (Topic) |
| `ak.wwise.core.profiler.switchChanged` | 开关变更通知 (Topic) |
| `ak.wwise.core.profiler.captureLog.itemAdded` | 捕获日志通知 (Topic) |

### wwise.ui

用户界面操作。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.ui.commands.execute` | 执行 Wwise 命令 |
| `ak.wwise.ui.commands.executed` | 命令执行通知 (Topic) |
| `ak.wwise.ui.selectionChanged` | UI 选择变更通知 (Topic) |

### wwise.ui.commands

UI 命令相关。

### wwise.debug

调试相关。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.debug.assertFailed` | 断言失败通知 (Topic) |

### wwise.core.audio

音频操作。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.audio.imported` | 音频导入完成通知 (Topic) |

### wwise.core.switchContainer

Switch Container 操作。

| 函数示例 | 说明 |
|----------|------|
| `ak.wwise.core.switchContainer.assignmentAdded` | 分配添加通知 (Topic) |
| `ak.wwise.core.switchContainer.assignmentRemoved` | 分配移除通知 (Topic) |

## 命名规范

### 函数命名

- 采用**驼峰命名法** (camelCase)
- 函数名通常是动词或动名词短语
- RPC 函数示例：`get`, `set`, `create`, `execute`, `generate`
- Topic（通知）示例：`created`, `loaded`, `saved`, `nameChanged`, `propertyChanged`

### 类别命名

- 采用**全小写**，点号分隔
- 可以有多个层级：`core.object.propertyChanged`

### URI 在代码中的引用

WAAPI SDK 提供了预定义的 URI 常量。在 JavaScript 中：

```javascript
var ak = require('../../../../include/AK/WwiseAuthoringAPI/js/waapi.js').ak;

// 使用预定义的 URI 常量
session.call(ak.wwise.core.getInfo, [], {});

// 等同于使用字符串
session.call('ak.wwise.core.getInfo', [], {});
```

> 注意: `var ak = require('.../waapi.js').ak` 导入的是 API 路径声明文件，位于 `<Wwise installation path>/SDK/include/AK/WwiseAuthoringAPI/js/waapi.js`。

> **来源**: [JavaScript, Node.js - WAMP](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wamp_js_node.html)

## 如何获取完整函数列表

### 通过 WAAPI 函数

WAAPI 提供了自省功能来获取所有可用函数和 Topic：

- `ak.wwise.waapi.getFunctions` — 获取所有可用函数列表
- `ak.wwise.waapi.getTopics` — 获取所有可用 Topic 列表

### 通过官方文档

- [Wwise Authoring API Reference - Functions](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_functions_index.html)
- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics_index.html)
