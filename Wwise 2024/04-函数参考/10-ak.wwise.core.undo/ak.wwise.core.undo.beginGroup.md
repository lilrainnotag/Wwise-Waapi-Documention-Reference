# ak.wwise.core.undo.beginGroup

▎ **命名空间**: ak.wwise.core.undo

## 概述

Begins an undo group. Make sure to call ak.wwise.core.undo.endGroup exactly once for every ak.wwise.core.beginUndoGroup call you make. Calls to ak.wwise.core.undo.beginGroup can be nested. When closing a WAMP session, a check is made to ensure that all undo groups are closed. If not, a cancelGroup is called for each of the groups still open.

## 参数

（无需参数）

## 返回值

（官网未提供）

## JSON-RPC 请求示例

```json
{}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 每个 `beginGroup` 调用必须有一个对应的 `endGroup` 调用来关闭。
- Undo 组支持**嵌套**，即可以在一个 undo 组内部再开始一个新的 undo 组。
- 当 WAMP session 关闭时，会自动检查并 `cancelGroup` 所有未关闭的 undo 组。
- 使用 undo 组的典型工作流：`beginGroup` → 执行一系列 WAAPI 操作 → `endGroup`。之后可以通过单个 `undo` 调用撤销整个组的操作。

## 相关函数

- ak.wwise.core.undo.endGroup
- ak.wwise.core.undo.cancelGroup
- ak.wwise.core.undo.undo

## 相关 Topic

- Undo/Redo 系统

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_undo_begingroup.html
