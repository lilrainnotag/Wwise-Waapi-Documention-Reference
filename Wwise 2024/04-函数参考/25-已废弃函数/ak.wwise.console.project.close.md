# ak.wwise.console.project.close

## 命名空间
ak.wwise.console.project

## 状态
已废弃，替代函数: ak.wwise.ui.project.close

> **注意**：官方文档页面未标注此函数为 deprecated，但根据 Wwise 2024 文档结构，此函数已迁移至 `ak.wwise.ui.project.close`。

## 概述

Closes the current project. This operation is synchronous.

## 参数

无参数。

## 参数 Schema

（无）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| hadProjectOpen | boolean | True if there was a project open, false otherwise. Note that if there was no project open, no ak.wwise.core.project.preClosed or ak.wwise.core.project.postClosed event is issued. |

## 返回值 Schema

（官网未提供独立 Schema）

## JSON-RPC 请求示例

（官网示例页面未提供）

## JSON-RPC 响应示例

（官网示例页面未提供）

## 注意事项

- 此操作为同步操作
- 如果没有打开的项目，返回 hadProjectOpen = false，且不会发出 preClosed/postClosed 事件
- 建议使用替代函数 `ak.wwise.ui.project.close`

## 相关函数

- ak.wwise.console.project.open
- ak.wwise.console.project.create
- ak.wwise.core.project.save
- ak.wwise.core.project.preClosed (topic)
- ak.wwise.core.project.postClosed (topic)
- ak.wwise.ui.project.open（替代）
- ak.wwise.ui.project.close（替代）

## 相关 Topic

- Using the Wwise Authoring API (WAAPI)

## 官方文档链接

- [ak.wwise.console.project.close](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_console_project_close.html)
