# ak.wwise.ui.project.create

## 命名空间: ak.wwise.ui.project

## 概述

创建、保存并打开一个新的空白项目（按指定的路径和平台）。项目不含出厂设置 WorkUnit。如需在操作完成后获得通知，请参阅 [ak.wwise.core.project.loaded](../18-ak.wwise.core.project/)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| path | string | 是 | — | 项目 WPROJ 文件路径。路径中 WPROJ 文件名必须与父文件夹名相同。例如：`C:\Projects\MYPROJECT\MYPROJECT.wproj` |
| platforms | object / array | 否 | 仅 Windows | 新项目支持的平台。每个平台对象包含：name（string），basePlatform（string，必填，可选值：Android, iOS, Linux, Mac, Switch, Ounce, PS4, PS5, Windows, XboxOne, XboxSeriesX） |
| languages | array | 否 | English(US) | 项目要创建的语言数组。如未指定，仅创建 English(US)。指定多个语言时，第一个为默认语言 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功创建时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.project.create",
  "params": {
    "path": "C:\\Projects\\MYPROJECT\\MYPROJECT.wproj",
    "platforms": [
      {
        "name": "Windows",
        "basePlatform": "Windows"
      },
      {
        "name": "Android",
        "basePlatform": "Android"
      }
    ],
    "languages": ["English(US)"]
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 此函数是 [ak.wwise.console.project.create](../../25-已废弃函数/) 的替代版本
- WPROJ 文件路径中，WPROJ 文件名必须与父文件夹名相同
- 项目创建完成后可通过 [ak.wwise.core.project.loaded](../18-ak.wwise.core.project/) topic 获得通知

## 相关函数

- [ak.wwise.ui.project.open](ak.wwise.ui.project.open.md)
- [ak.wwise.ui.project.close](ak.wwise.ui.project.close.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.project.create](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_project_create.html)
