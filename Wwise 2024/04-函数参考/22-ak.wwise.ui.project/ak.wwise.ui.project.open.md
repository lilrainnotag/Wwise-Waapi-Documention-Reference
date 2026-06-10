# ak.wwise.ui.project.open

## 命名空间: ak.wwise.ui.project

## 概述

按路径打开一个项目。这是 [ak.wwise.console.project.open](../../25-已废弃函数/) 的替代函数（旧版已废弃）。如需在操作完成后获得通知，请参阅 [ak.wwise.core.project.loaded](../18-ak.wwise.core.project/)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| path | string | 是 | — | 项目 WPROJ 文件路径 |
| onUpgrade | string | 否 | — | **（已废弃）** 打开需要升级的项目时的操作。可选值：`migrate`、`fail` |
| onMigrationRequired | string | 否 | — | 打开需要迁移的项目时的操作。可选值：`migrate`、`fail` |
| bypassSave | boolean | 否 | true | 是否跳过提示用户保存当前项目 |
| autoCheckOutToSourceControl | boolean | 否 | true | 是否自动对受影响的工作单元和项目执行 Checkout 源代码管理操作 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功打开时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.project.open",
  "params": {
    "path": "C:\\Projects\\MYPROJECT\\MYPROJECT.wproj",
    "onMigrationRequired": "migrate",
    "bypassSave": true,
    "autoCheckOutToSourceControl": true
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 此函数是 [ak.wwise.console.project.open](../../25-已废弃函数/) 的替代版本
- onUpgrade 参数已废弃，请使用 onMigrationRequired 替代
- 项目打开完成后可通过 [ak.wwise.core.project.loaded](../18-ak.wwise.core.project/) topic 获得通知

## 相关函数

- [ak.wwise.ui.project.close](ak.wwise.ui.project.close.md)
- [ak.wwise.ui.project.create](ak.wwise.ui.project.create.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.project.open](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_project_open.html)
