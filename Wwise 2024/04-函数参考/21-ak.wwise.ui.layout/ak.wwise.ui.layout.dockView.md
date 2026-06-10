# ak.wwise.ui.layout.dockView

## 命名空间: ak.wwise.ui.layout

## 概述

将一个浮动视图停靠到布局中。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要停靠到的布局名称 |
| viewID | string (GUID) | 是 | — | 要停靠的视图唯一 ID，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |
| targetID | string (GUID) | 是 | — | 目标元素的唯一 ID，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |
| side | string | 是 | — | 将视图放置到目标的哪一侧。可选值：`left`、`right`、`top`、`bottom` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功停靠时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.dockView",
  "params": {
    "name": "Designer",
    "viewID": "{6609D1BA-0E47-48F4-B3B6-3DA1C345B66E}",
    "targetID": "{39949670-A96A-47C5-8EEF-F8AD26BD6B34}",
    "side": "left"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- viewID 和 targetID 可通过 [ak.wwise.ui.layout.getViewInstances](#) 获取
- 需要先通过 [ak.wwise.ui.layout.undockView](#) 将视图设为浮动状态后再停靠

## 相关函数

- [ak.wwise.ui.layout.undockView](ak.wwise.ui.layout.undockView.md)
- [ak.wwise.ui.layout.getViewInstances](ak.wwise.ui.layout.getViewInstances.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.dockView](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_dockView.html)
