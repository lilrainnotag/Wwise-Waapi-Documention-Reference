# ak.wwise.core.undo.endGroup

▎ **命名空间**: ak.wwise.core.undo

## 概述

Ends the last undo group.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| displayName | string | 是 | — | The name that is displayed in the history for this undo group. |

## 返回值

（官网未提供）

## JSON-RPC 请求示例

```json
{
    "displayName": "Batch SoundBank Generation"
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `displayName` 是在 Wwise 的 Undo History 中显示的名称，应使用有意义的描述。
- 每个 `beginGroup` 必须有唯一的 `endGroup` 对应。在嵌套 undo 组中，`endGroup` 关闭最近打开的组。

## 相关函数

- ak.wwise.core.undo.beginGroup
- ak.wwise.core.undo.cancelGroup
- ak.wwise.core.undo.undo

## 相关 Topic

- Undo/Redo 系统

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_undo_endgroup.html
