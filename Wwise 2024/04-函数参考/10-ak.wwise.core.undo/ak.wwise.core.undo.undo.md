# ak.wwise.core.undo.undo

▎ **命名空间**: ak.wwise.core.undo

## 概述

Undoes the last operation in the Undo stack.

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

- Undo 会撤销 Undo 栈中的最后一个操作（或 undo 组）。
- 如果使用了 undo 组（beginGroup/endGroup），单个 undo 调用会撤销整个组内的所有操作。
- 可以与 redo 配合使用实现完整的撤销/重做功能。

## 相关函数

- ak.wwise.core.undo.redo
- ak.wwise.core.undo.beginGroup
- ak.wwise.core.undo.cancelGroup
- ak.wwise.core.undo.endGroup

## 相关 Topic

- Undo/Redo 系统

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_undo_undo.html
