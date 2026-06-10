# ak.wwise.ui.commands.register

## 命名空间: ak.wwise.ui.commands

## 概述

注册一组附加命令（add-on commands）。注册的命令会一直保留，直到 Wwise 进程终止。这是实现 WAAPI 自定义命令的关键函数。有关注册命令的更多信息，请参阅 [Defining Command Add-ons](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=defining_command_addons.html)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| commands | array | 是 | — | 要注册的命令数据数组 |
| commands[].id | string | 是 | — | 命令的唯一可读 ID。建议使用 `作者名.产品名.命令名` 格式以避免冲突 |
| commands[].displayName | string | 是 | — | 在用户界面中显示的命令名称 |
| commands[].program | string | 否 | — | 命令执行时要运行的程序或脚本路径。支持 `${CurrentCommandDirectory}` 等目录变量 |
| commands[].luaScript | string | 否 | — | 定义在 Wwise 进程内运行的 Lua 脚本文件路径 |
| commands[].luaPaths | array | 否 | — | 加载额外 Lua 脚本的路径数组 |
| commands[].luaSelectedReturn | array | 否 | — | 为 Wwise 中选中的对象指定的返回表达式数组，通过 `wa_args.selected` 传递给脚本 |
| commands[].startMode | string | 否 | — | 多选情况下变量展开方式：`SingleSelectionSingleProcess`（仅单选）、`MultipleSelectionSingleProcessSpaceSeparated`（空格分隔参数）、`MultipleSelectionMultipleProcesses`（并行多进程） |
| commands[].args | string | 否 | — | 程序参数。多选时变量根据 startMode 展开 |
| commands[].cwd | string | 否 | — | 执行程序的工作目录 |
| commands[].defaultShortcut | string | 否 | — | 默认快捷键。如冲突则被忽略 |
| commands[].redirectOutputs | boolean | 否 | false | 是否将程序 stdout+stderr 重定向到 Wwise 日志 |
| commands[].contextMenu | object | 否 | — | 上下文菜单配置（basePath, visibleFor, enabledFor） |
| commands[].mainMenu | object | 否 | — | 主菜单配置（basePath 必填） |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功注册时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.commands.register",
  "params": {
    "commands": [
      {
        "id": "sample.programlessregistration",
        "displayName": "Programless registration"
      }
    ]
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 注册的命令在 Wwise 进程终止前一直有效
- 命令被触发时会通过 [ak.wwise.ui.commands.executed](../../23-ak.wwise.waapi/) topic 发布通知
- 配合 [ak.wwise.ui.commands.execute](ak.wwise.ui.commands.execute.md) 可实现完整的自定义命令工作流
- 建议使用 `作者名.产品名.命令名` 格式作为命令 ID 以避免与其他插件冲突

## 相关函数

- [ak.wwise.ui.commands.execute](ak.wwise.ui.commands.execute.md)
- [ak.wwise.ui.commands.unregister](ak.wwise.ui.commands.unregister.md)
- [ak.wwise.ui.commands.getCommands](ak.wwise.ui.commands.getCommands.md)

## 相关Topic

- [Defining Command Add-ons](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=defining_command_addons.html)
- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.commands.register](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_commands_register.html)
