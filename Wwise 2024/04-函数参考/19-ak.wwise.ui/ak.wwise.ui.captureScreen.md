# ak.wwise.ui.captureScreen

## 命名空间: ak.wwise.ui

## 概述

捕获 Wwise UI 中相对于某个视图的部分区域截图。可以通过参数指定视图名称、选择通道和捕获区域，返回 Base64 编码的图像数据。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| viewName | string | 否 | 整个 UI | 视图的名称。默认捕获整个 UI |
| viewSelectionChannel | integer | 否 | 自动检测 | 视图的选择通道，值可以是 1、2、3 或 4。默认自动检测当前选择通道 |
| rect | object | 否 | 整个视图 | 捕获区域。默认捕获整个视图 |
| rect.x | integer | 是（若提供rect） | — | 捕获区域左边界位置（像素） |
| rect.y | integer | 是（若提供rect） | — | 捕获区域上边界位置（像素） |
| rect.width | integer | 是（若提供rect） | — | 捕获区域宽度（像素） |
| rect.height | integer | 是（若提供rect） | — | 捕获区域高度（像素） |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| contentType | string | 底层图像数据格式（例如 image/png） |
| contentBase64 | string | 编码后的图像数据（Base64 格式） |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.captureScreen",
  "params": {
    "viewName": "Property Editor",
    "rect": {
      "x": 0,
      "y": 0,
      "width": 800,
      "height": 600
    }
  }
}
```

## JSON-RPC 响应示例

```json
{
  "contentType": "image/png",
  "contentBase64": "iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mNk..."
}
```

## 注意事项

- 截图为整个 Wwise 窗口相对于指定视图的像素级捕获
- 返回的图像数据为 Base64 编码，需要解码后才能保存为图像文件
- rect 对象中的所有字段在提供时必须全部填写

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.captureScreen](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_captureScreen.html)
