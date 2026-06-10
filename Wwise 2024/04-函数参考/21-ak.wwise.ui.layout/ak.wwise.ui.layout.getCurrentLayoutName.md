# ak.wwise.ui.layout.getCurrentLayoutName

## 命名空间: ak.wwise.ui.layout

## 概述

获取当前布局的名称。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| （无参数） | — | — | — | 此函数不接受任何参数 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| name | string | 当前布局的名称，空字符串表示没有布局 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.getCurrentLayoutName",
  "params": {}
}
```

## JSON-RPC 响应示例

```json
{
  "name": "Designer"
}
```

## 注意事项

- 返回空字符串时表示当前没有激活的布局

## 相关函数

- [ak.wwise.ui.layout.switchLayout](ak.wwise.ui.layout.switchLayout.md)
- [ak.wwise.ui.layout.getLayoutNames](ak.wwise.ui.layout.getLayoutNames.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.getCurrentLayoutName](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_getCurrentLayoutName.html)
