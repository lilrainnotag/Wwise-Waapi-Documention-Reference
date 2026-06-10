# ak.wwise.ui.layout.getElementRectangle

## 命名空间: ak.wwise.ui.layout

## 概述

获取布局元素的当前分配矩形区域。如果元素未找到，则返回空矩形。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| id | string | 是 | — | 元素的 ID |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| left | number | 元素的左边界位置（像素） |
| top | number | 元素的上边界位置（像素） |
| right | number | 元素的右边界位置（像素） |
| bottom | number | 元素的下边界位置（像素） |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.getElementRectangle",
  "params": {
    "id": "{6609D1BA-0E47-48F4-B3B6-3DA1C345B66E}"
  }
}
```

## JSON-RPC 响应示例

```json
{
  "left": 0,
  "top": 0,
  "right": 800,
  "bottom": 600
}
```

## 注意事项

- 如果元素未找到，返回空矩形（所有值为 0）
- 元素 ID 可通过 [ak.wwise.ui.layout.getViewInstances](#) 获取

## 相关函数

- [ak.wwise.ui.layout.getViewInstances](ak.wwise.ui.layout.getViewInstances.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.getElementRectangle](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_getElementRectangle.html)
