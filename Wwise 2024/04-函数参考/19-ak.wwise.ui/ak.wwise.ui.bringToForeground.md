# ak.wwise.ui.bringToForeground

## 命名空间: ak.wwise.ui

## 概述

将 Wwise 主窗口带到前台。有关限制的更多信息，请参阅 MSDN 上的 SetForegroundWindow 和 AllowSetForegroundWindow。请参阅 ak.wwise.core.getInfo 获取 Wwise 进程 ID 以用于 AllowSetForegroundWindow。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| （无参数） | — | — | — | 此函数不接受任何参数 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 此函数不返回任何数据 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.bringToForeground",
  "params": {}
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 此函数受 Windows 的 SetForegroundWindow 限制约束，在某些情况下（如前台进程优先级不足）可能无法成功将窗口带到前台
- 可通过 ak.wwise.core.getInfo 获取 Wwise 进程 ID 来配合 AllowSetForegroundWindow 使用

## 相关函数

- [ak.wwise.core.getInfo](../02-ak.wwise.core/ak.wwise.core.getInfo.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.bringToForeground](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_bringToForeground.html)
