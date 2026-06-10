# ak.wwise.ui.layout.getViewInstances

## 命名空间: ak.wwise.ui.layout

## 概述

获取指定布局中所有视图实例的列表。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要检查的布局名称 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| viewInstances | array | 布局中所有视图实例的数组 |
| viewInstances[].viewName | string | 视图实例的名称 |
| viewInstances[].viewID | string (GUID) | 视图实例的 ID |
| viewInstances[].viewIsDocked | boolean | 视图是否已停靠 |
| viewInstances[].viewDisplayName | string | 视图实例的显示名称 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.getViewInstances",
  "params": {
    "name": "Designer"
  }
}
```

## JSON-RPC 响应示例

```json
{
  "viewInstances": [
    {
      "viewName": "Property Editor",
      "viewID": "{6609D1BA-0E47-48F4-B3B6-3DA1C345B66E}",
      "viewIsDocked": true,
      "viewDisplayName": "Property Editor"
    },
    {
      "viewName": "Project Explorer",
      "viewID": "{39949670-A96A-47C5-8EEF-F8AD26BD6B34}",
      "viewIsDocked": true,
      "viewDisplayName": "Project Explorer"
    }
  ]
}
```

## 注意事项

- viewID 可用于 [ak.wwise.ui.layout.dockView](ak.wwise.ui.layout.dockView.md) 和 [ak.wwise.ui.layout.undockView](ak.wwise.ui.layout.undockView.md) 等操作
- viewIsDocked 为 false 时表示该视图处于浮动状态

## 相关函数

- [ak.wwise.ui.layout.getViewTypes](ak.wwise.ui.layout.getViewTypes.md)
- [ak.wwise.ui.layout.dockView](ak.wwise.ui.layout.dockView.md)
- [ak.wwise.ui.layout.undockView](ak.wwise.ui.layout.undockView.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.getViewInstances](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_getViewInstances.html)
