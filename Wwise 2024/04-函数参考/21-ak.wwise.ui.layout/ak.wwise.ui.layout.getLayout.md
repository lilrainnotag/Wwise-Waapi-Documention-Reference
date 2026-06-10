# ak.wwise.ui.layout.getLayout

## 命名空间: ak.wwise.ui.layout

## 概述

将指定布局序列化为 JSON 格式。返回的数据包含布局的完整结构描述，包括 StackPanel 层次结构、视图位置、未停靠视图和各类最后标签位置等。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要序列化的布局名称 |

## 返回值

返回一个 `Layout` 对象，包含以下主要字段：

| 名称 | 类型 | 说明 |
|------|------|------|
| Layout.Name | string | 布局名称 |
| Layout.StackPanel | object | 布局的主 StackPanel 结构（包含嵌套的子元素树） |
| Layout.Undocked | array | 未停靠（浮动）视图列表 |
| Layout.LastPositions | array | 最后标签位置列表 |
| Layout.AudioDeviceLastTabPositions | array | AudioDevice 最后标签位置 |
| Layout.EffectLastTabPositions | array | Effect 最后标签位置 |
| Layout.FallbackLastTabPositions | array | Fallback 最后标签位置 |
| Layout.MetadataLastTabPositions | array | Metadata 最后标签位置 |
| Layout.ObjectTypeLastTabPositions | array | ObjectType 最后标签位置 |
| Layout.PluginInnerObjectLastTabPositions | array | PluginInnerObject 最后标签位置 |
| Layout.SourcePluginLastTabPositions | array | SourcePlugin 最后标签位置 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.getLayout",
  "params": {
    "name": "Designer"
  }
}
```

## JSON-RPC 响应示例

```json
{
  "Layout": {
    "Name": "Designer",
    "StackPanel": {
      "@type": "StackPanel",
      "Name": "Root",
      "ID": "{...}",
      "Orientation": "Horizontal",
      "@Children": []
    },
    "Undocked": []
  }
}
```

## 注意事项

- 返回的 JSON 结构完整描述了布局的 StackPanel 层次和视图排列
- 可用于备份布局配置，或与 [ak.wwise.ui.layout.setLayout](#) 配合恢复布局

## 相关函数

- [ak.wwise.ui.layout.setLayout](ak.wwise.ui.layout.setLayout.md)
- [ak.wwise.ui.layout.getLayoutNames](ak.wwise.ui.layout.getLayoutNames.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.getLayout](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_getLayout.html)
