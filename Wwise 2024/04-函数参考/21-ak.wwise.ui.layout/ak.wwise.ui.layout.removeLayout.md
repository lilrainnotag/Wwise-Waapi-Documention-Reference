# ak.wwise.ui.layout.removeLayout

## 命名空间: ak.wwise.ui.layout

## 概述

取消注册一个临时布局（此前通过 [ak.wwise.ui.layout.setLayout](ak.wwise.ui.layout.setLayout.md) 注册的布局）。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要取消注册的布局名称 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功取消注册时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.removeLayout",
  "params": {
    "name": "MyLayout"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 仅可取消通过 [ak.wwise.ui.layout.setLayout](ak.wwise.ui.layout.setLayout.md) 注册的临时布局

## 相关函数

- [ak.wwise.ui.layout.setLayout](ak.wwise.ui.layout.setLayout.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.removeLayout](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_removeLayout.html)
