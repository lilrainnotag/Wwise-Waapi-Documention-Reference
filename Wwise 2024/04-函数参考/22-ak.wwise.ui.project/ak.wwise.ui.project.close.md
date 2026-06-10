# ak.wwise.ui.project.close

## 命名空间: ak.wwise.ui.project

## 概述

关闭当前项目。这是 [ak.wwise.console.project.close](../../25-已废弃函数/) 的替代函数（旧版已废弃）。如需在操作完成后获得通知，请参阅 [ak.wwise.core.project.postClosed](../18-ak.wwise.core.project/)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| bypassSave | boolean | 否 | true | 是否跳过提示用户保存当前项目 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| hadProjectOpen | boolean | 如果之前有项目打开则为 true，否则为 false。注意：如果本来就没有打开的项目，则不会发出 ak.wwise.core.project.preClosed 或 ak.wwise.core.project.postClosed 事件 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.project.close",
  "params": {
    "bypassSave": true
  }
}
```

## JSON-RPC 响应示例

```json
{
  "hadProjectOpen": true
}
```

## 注意事项

- 此函数是 [ak.wwise.console.project.close](../../25-已废弃函数/) 的替代版本
- 关闭项目前后会发出 [ak.wwise.core.project.preClosed](../18-ak.wwise.core.project/) 和 [ak.wwise.core.project.postClosed](../18-ak.wwise.core.project/) 事件
- 如果本来就没有打开的项目，不会发出这些事件

## 相关函数

- [ak.wwise.ui.project.open](ak.wwise.ui.project.open.md)
- [ak.wwise.ui.project.create](ak.wwise.ui.project.create.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.project.close](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_project_close.html)
