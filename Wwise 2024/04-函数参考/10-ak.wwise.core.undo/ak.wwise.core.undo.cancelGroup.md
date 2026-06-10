# ak.wwise.core.undo.cancelGroup

▎ **命名空间**: ak.wwise.core.undo

## 概述

Cancels the last undo group.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| undo | boolean | 否 | false | Specify if the operations are undone. 设为 true 时，不仅取消 undo 组，还会撤销其中的操作。 |

## 返回值

（官网未提供）

## JSON-RPC 请求示例

### 仅取消 undo 组（不撤销操作）

```json
{}
```

### 取消 undo 组并撤销操作

```json
{
    "undo": true
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 取消 undo 组后，该组内的操作将不会作为一个整体出现在 undo 历史中。
- 如果设置 `undo: true`，会同时撤销组内的所有操作。

## 相关函数

- ak.wwise.core.undo.beginGroup
- ak.wwise.core.undo.endGroup
- ak.wwise.core.undo.undo

## 相关 Topic

- Undo/Redo 系统

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_undo_cancelgroup.html
