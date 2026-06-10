# ak.wwise.ui.layout.undockView

## 命名空间: ak.wwise.ui.layout

## 概述

将视图从布局中取消停靠（变为浮动状态）。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要从中取消停靠视图的布局名称 |
| viewID | string (GUID) | 是 | — | 要取消停靠的视图唯一 ID，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |
| posX | integer | 否 | 0 | 取消停靠后视图在水平轴上的位置 |
| posY | integer | 否 | 0 | 取消停靠后视图在垂直轴上的位置 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功取消停靠时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.undockView",
  "params": {
    "name": "Designer",
    "viewID": "{AABBCC00-1122-3344-5566-77889900AABB}",
    "posX": 100,
    "posY": 100
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- viewID 可通过 [ak.wwise.ui.layout.getViewInstances](ak.wwise.ui.layout.getViewInstances.md) 获取
- 取消停靠后的视图可通过 [ak.wwise.ui.layout.dockView](ak.wwise.ui.layout.dockView.md) 重新停靠

## 相关函数

- [ak.wwise.ui.layout.dockView](ak.wwise.ui.layout.dockView.md)
- [ak.wwise.ui.layout.getViewInstances](ak.wwise.ui.layout.getViewInstances.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.undockView](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_undockView.html)
