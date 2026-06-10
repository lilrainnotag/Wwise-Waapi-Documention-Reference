# ak.wwise.ui.commands.execute

## 命名空间: ak.wwise.ui.commands

## 概述

执行一条 Wwise 命令。某些命令可以接受对象列表作为参数。有关可用命令的完整列表，请参阅 [Wwise Authoring Command Identifiers](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=globalcommandsids.html)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| command | string | 是 | — | 要执行的命令 ID。参见 Wwise Authoring Command Identifiers |
| objects | array | 否 | — | 对象数组。每个元素可以是 ID (GUID)、名称或路径。部分命令接受对象作为参数 |
| objects[] | string (GUID) 或 string (name) 或 string (path) | 否 | — | 对象标识，支持三种格式：`{GUID}`、`type:name`（如 `Event:Play_Sound_01`）、项目路径（如 `\Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX`） |
| platforms | array | 否 | — | 平台数组。每个元素为 ID (GUID) 或名称 |
| platforms[] | string (GUID) 或 string (name) | 否 | — | 平台的 ID 或唯一名称 |
| value | any | 否 | — | 传递给命令的值。可以是 null、string、number 或 boolean |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功执行时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.commands.execute",
  "params": {
    "command": "ResetAllMutes"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 这是实现 Wwise UI 自定义命令的核心函数，配合 [ak.wwise.ui.commands.register](#) 使用可实现完整的自定义命令流程
- 可用的命令 ID 列表请参阅官方文档 [Wwise Authoring Command Identifiers](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=globalcommandsids.html)
- objects 参数支持 GUID 字符串、`type:name` 格式（如 `Event:Play_Sound_01`）和项目路径三种形式

## 相关函数

- [ak.wwise.ui.commands.getCommands](ak.wwise.ui.commands.getCommands.md)
- [ak.wwise.ui.commands.register](ak.wwise.ui.commands.register.md)
- [ak.wwise.ui.commands.unregister](ak.wwise.ui.commands.unregister.md)

## 相关Topic

- [Wwise Authoring Command Identifiers](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=globalcommandsids.html)
- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.commands.execute](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_commands_execute.html)
