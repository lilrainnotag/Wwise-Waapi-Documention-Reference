# ak.wwise.ui.layout.switchLayout

## 命名空间: ak.wwise.ui.layout

## 概述

切换当前布局到指定布局。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | — | 要加载的布局名称 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功切换时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.switchLayout",
  "params": {
    "name": "Designer"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 布局名称可以是工厂预设布局（如 "Designer"、"Profiler"），也可以是用户自定义布局
- 可用 [ak.wwise.ui.layout.getLayoutNames](ak.wwise.ui.layout.getLayoutNames.md) 获取所有可用布局名称

## 相关函数

- [ak.wwise.ui.layout.getCurrentLayoutName](ak.wwise.ui.layout.getCurrentLayoutName.md)
- [ak.wwise.ui.layout.getLayoutNames](ak.wwise.ui.layout.getLayoutNames.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.switchLayout](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_switchLayout.html)
