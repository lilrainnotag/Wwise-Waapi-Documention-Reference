# ak.wwise.ui.layout.getViewTypes

## 命名空间: ak.wwise.ui.layout

## 概述

获取 Wwise 中注册的所有视图类型列表。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| （无参数） | — | — | — | 此函数不接受任何参数 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| viewTypes | array | Wwise 中所有视图类型的数组 |
| viewTypes[].viewName | string | 视图的类型名称 |
| viewTypes[].viewDisplayName | string | 视图的显示名称 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.getViewTypes",
  "params": {}
}
```

## JSON-RPC 响应示例

```json
{
  "viewTypes": [
    {
      "viewName": "PropertyEditor",
      "viewDisplayName": "Property Editor"
    },
    {
      "viewName": "ProjectExplorer",
      "viewDisplayName": "Project Explorer"
    }
  ]
}
```

## 注意事项

- viewName 可用于 [ak.wwise.ui.layout.getOrCreateView](ak.wwise.ui.layout.getOrCreateView.md) 的 name 参数

## 相关函数

- [ak.wwise.ui.layout.getOrCreateView](ak.wwise.ui.layout.getOrCreateView.md)
- [ak.wwise.ui.layout.getViewInstances](ak.wwise.ui.layout.getViewInstances.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.getViewTypes](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_getViewTypes.html)
