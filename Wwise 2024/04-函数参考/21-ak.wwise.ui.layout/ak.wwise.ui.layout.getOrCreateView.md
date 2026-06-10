# ak.wwise.ui.layout.getOrCreateView

## 命名空间: ak.wwise.ui.layout

## 概述

获取一个视图（如果它存在于当前布局中），或在不存在时创建一个新的视图。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要获取或创建的视图类型的唯一标识符字符串 |
| posX | integer | 否 | -1 | 创建的视图在水平轴上的初始位置 |
| posY | integer | 否 | -1 | 创建的视图在垂直轴上的初始位置 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| id | string (GUID) | 视图的唯一 ID，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.getOrCreateView",
  "params": {
    "name": "Property Editor"
  }
}
```

## JSON-RPC 响应示例

```json
{
  "id": "{6609D1BA-0E47-48F4-B3B6-3DA1C345B66E}"
}
```

## 注意事项

- 如果视图已存在，返回现有视图的 ID；否则创建新视图并返回新 ID
- posX 和 posY 仅在创建新视图时生效
- 视图类型名称可通过 [ak.wwise.ui.layout.getViewTypes](#) 获取

## 相关函数

- [ak.wwise.ui.layout.getViewInstances](ak.wwise.ui.layout.getViewInstances.md)
- [ak.wwise.ui.layout.getViewTypes](ak.wwise.ui.layout.getViewTypes.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.getOrCreateView](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_getOrCreateView.html)
