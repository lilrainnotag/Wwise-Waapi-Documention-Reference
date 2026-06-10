# ak.wwise.ui.layout.getLayoutNames

## 命名空间: ak.wwise.ui.layout

## 概述

获取工厂预设布局名称的列表。返回的布局名称可用于 [ak.wwise.ui.layout.getLayout](ak.wwise.ui.layout.getLayout.md)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| （无参数） | — | — | — | 此函数不接受任何参数 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| layouts | array | 工厂预设布局名称数组 |
| layouts[] | string | 布局名称字符串，可用于 getLayout 等函数 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.getLayoutNames",
  "params": {}
}
```

## JSON-RPC 响应示例

```json
{
  "layouts": [
    "Designer",
    "Profiler",
    "Soundcaster",
    "Mixing"
  ]
}
```

## 注意事项

- 仅返回工厂预设布局名称，不包含用户自定义布局
- 返回的布局名称可直接用于 [ak.wwise.ui.layout.getLayout](ak.wwise.ui.layout.getLayout.md)、[ak.wwise.ui.layout.switchLayout](ak.wwise.ui.layout.switchLayout.md) 等函数

## 相关函数

- [ak.wwise.ui.layout.getLayout](ak.wwise.ui.layout.getLayout.md)
- [ak.wwise.ui.layout.getCurrentLayoutName](ak.wwise.ui.layout.getCurrentLayoutName.md)
- [ak.wwise.ui.layout.switchLayout](ak.wwise.ui.layout.switchLayout.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.getLayoutNames](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_getLayoutNames.html)
