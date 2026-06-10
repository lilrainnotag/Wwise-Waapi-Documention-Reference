# ak.wwise.core.undo.redo

▎ **命名空间**: ak.wwise.core.undo

## 概述

Redoes the last operation in the Undo stack.

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

- Redo 会重做最近一次被撤销（undo）的操作。
- 只有在执行了 undo 之后，redo 才可用。

## 相关函数

- ak.wwise.core.undo.undo
- ak.wwise.core.undo.beginGroup
- ak.wwise.core.undo.cancelGroup
- ak.wwise.core.undo.endGroup

## 相关 Topic

- Undo/Redo 系统

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_undo_redo.html
