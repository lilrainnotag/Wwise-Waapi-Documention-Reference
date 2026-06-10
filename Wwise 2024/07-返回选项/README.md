# 07 - 返回选项（Return Options）

## 章节概述

在 Wwise WAAPI 中，`ak.wwise.core.object.get` 是最核心的函数之一。通过 `return` 选项，你可以精确指定每个查询结果对象要返回哪些数据。返回选项支持三类数据：

1. **内置访问器（Built-in Accessors）** — 如 `id`、`name`、`type`、`path`、`parent` 等通用属性
2. **对象属性（Object Properties）** — 以 `@` 或 `@@` 为前缀的属性访问，如 `@Volume`、`@Pitch`、`@OutputBus`
3. **特殊返回选项（Special Return Options）** — 如 `audioPeaks`、`sound:originalWavFilePath`、`music:transitionRoot` 等

## 文件索引

| 文件 | 内容 |
|------|------|
| [01-通用返回属性.md](01-通用返回属性.md) | 内置访问器完整列表（90+个）、`@` / `@@` 前缀含义、引用链式访问语法 |
| [02-音频属性返回.md](02-音频属性返回.md) | 对象属性访问（Volume/Pitch/OutputBus等）、`@` vs `@@` 区别、平台特定属性 |
| [03-特殊返回选项.md](03-特殊返回选项.md) | audioPeaks、文件路径、Music、SoundBank、WorkUnit、Mute/Solo、尺寸、platform/language 参数 |

## 快速参考

```json
{
  "waql": "\"\\Actor-Mixer Hierarchy\\Default Work Unit\\My Sound\"",
  "return": [
    "id",
    "name",
    "type",
    "@Volume",
    "@Pitch",
    "parent.name",
    "sound:originalWavFilePath"
  ]
}
```

### @ 与 @@ 的区别

| 前缀 | 含义 | 示例 |
|------|------|------|
| `@` | 获取属性的当前值（对于该对象） | `@Volume` → 返回该对象的音量值 |
| `@@` | 获取属性的 override 源值 | `@@Volume` → 返回 override 来源的值 |

### 引用链式访问

通过点号 `.` 可以链式访问引用对象的属性：

- `parent.name` — 父对象的名称
- `parent.parent.type` — 祖父对象的类型
- `@OutputBus.name` — 输出总线对象的名称
- `Effects.first.id` — 第一个效果器的 ID
