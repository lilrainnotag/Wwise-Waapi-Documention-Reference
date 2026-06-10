# 05-WAQL查询语言

> **Wwise Authoring Query Language (WAQL)** — Wwise 创作查询语言

## 章节概述

WAQL 是 Wwise 专有的查询语言，用于在 Wwise 项目中查询和筛选对象。WAQL 不是 SQL，而是一门专为 Wwise 对象模型设计的领域特定语言。

## WAQL 的用途

WAQL 可以在以下场景中使用（来源：官方文档）：

- **Wwise 工具栏搜索（Toolbar Search）**：在 Wwise 主界面顶部的搜索框中直接使用 WAQL
- **列表视图搜索（List View Search）**：在 List View 的搜索字段中进行精确查询
- **原理图视图搜索（Schematic View Search）**：在 Schematic View 中使用 WAQL 定位对象
- **WAAPI**：通过 `ak.wwise.core.object.get` 函数在 API 调用中使用 WAQL

## WAQL 能做什么

- 枚举 Wwise 对象：Sound、Container、Bus、Event、SoundBank 等
- 按属性筛选：名称（name）、备注（notes）、ID、音量（volume）、音高（pitch）、输出总线（output bus）等
- 追踪对象引用：Event 的 Target、OutputBus 等
- 链式查询：通过点号运算符组合多个属性进行跨引用查询

## 章节导航

| 文件 | 内容 |
|------|------|
| [01-快速入门](01-快速入门.md) | 第一个 WAQL 查询、基本概念、$ 前缀、查询结构 |
| [02-语法参考](02-语法参考.md) | from/where/select/transform 完整语法、字符串规则 |
| [03-关键字详解](03-关键字详解.md) | this/parent/children/descendants/ancestors/referencesTo 等关键字 |
| [04-变换操作](04-变换操作.md) | transform 链、skip/take/orderby/distinct 用法 |
| [05-高级查询模式](05-高级查询模式.md) | 复杂查询示例、正则表达式、性能优化建议 |

## 数据来源

本章内容来源于 Audiokinetic Wwise 2024.1.14 官方文档：

- [Using the Wwise Authoring Query Language (WAQL)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waql_introduction.html)
- [Getting Started with WAQL](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waql_getting_started.html)
- [Glossary](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waql_glossary.html)
- [Important Keywords and Concepts](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waql_important_keywords_and_concepts.html)
- [Wwise Authoring Query Language (WAQL) Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waql_reference.html)
