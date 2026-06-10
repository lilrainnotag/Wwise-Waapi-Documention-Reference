# ak.wwise.ui.layout.setLayout

## 命名空间: ak.wwise.ui.layout

## 概述

以 JSON 格式注册一个新的布局。该布局会成为临时布局，可通过 [ak.wwise.ui.layout.removeLayout](ak.wwise.ui.layout.removeLayout.md) 取消注册。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要注册的布局名称 |
| layout | object | 是 | — | JSON 格式的布局描述。包含 StackPanel、视图位置、未停靠视图等完整布局配置 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功注册时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.setLayout",
  "params": {
    "name": "MyLayout",
    "layout": {
      "Layout": {
        "Name": "MyLayout",
        "StackPanel": {
          "@type": "StackPanel",
          "Name": "MainPanel",
          "ID": "main",
          "Orientation": "Horizontal",
          "@Children": []
        },
        "LastPositions": [],
        "Undocked": []
      }
    }
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- layout 参数结构复杂，包含 StackPanel（主面板布局）、LastPositions（停靠视图位置）、Undocked（浮动窗口）等嵌套结构
- 可通过 [ak.wwise.ui.layout.getLayout](ak.wwise.ui.layout.getLayout.md) 获取现有布局的 JSON 来参考格式
- 这是一个临时布局，Wwise 重启后会丢失

## 相关函数

- [ak.wwise.ui.layout.removeLayout](ak.wwise.ui.layout.removeLayout.md)
- [ak.wwise.ui.layout.getLayout](ak.wwise.ui.layout.getLayout.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.setLayout](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_setLayout.html)
