# ak.wwise.ui.commands.getCommands

## 命名空间: ak.wwise.ui.commands

## 概述

获取可用命令的列表。返回的命令 ID 可用于 [ak.wwise.ui.commands.execute](ak.wwise.ui.commands.execute.md)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| （无参数） | — | — | — | 此函数不接受任何参数 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| commands | array | 命令 ID 数组，可用于 ak.wwise.ui.commands.execute |
| commands[] | string | 命令 ID 字符串 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.commands.getCommands",
  "params": {}
}
```

## JSON-RPC 响应示例

```json
{
  "commands": [
    "ResetAllMutes",
    "Mute",
    "FindInProjectExplorer",
    "..."
  ]
}
```

## 注意事项

- 返回的命令 ID 列表包含所有可通过 [ak.wwise.ui.commands.execute](ak.wwise.ui.commands.execute.md) 执行的内置命令
- 完整的命令 ID 参考请参阅 [Wwise Authoring Command Identifiers](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=globalcommandsids.html)

## 相关函数

- [ak.wwise.ui.commands.execute](ak.wwise.ui.commands.execute.md)
- [ak.wwise.ui.commands.register](ak.wwise.ui.commands.register.md)

## 相关Topic

- [Wwise Authoring Command Identifiers](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=globalcommandsids.html)
- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.commands.getCommands](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_commands_getCommands.html)
