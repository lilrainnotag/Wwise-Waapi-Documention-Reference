# ak.wwise.ui.commands.unregister

## 命名空间: ak.wwise.ui.commands

## 概述

取消注册一组附加 UI 命令（add-on commands）。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| commands | array | 是 | — | 要取消注册的命令 ID 数组 |
| commands[] | string | 是 | — | 命令 ID 字符串，即注册时使用的 id 值 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功取消注册时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.commands.unregister",
  "params": {
    "commands": [
      "sample.programlessregistration",
      "ak.edit_in_vscode",
      "ak.open_in_wavosaur"
    ]
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 取消注册后，对应的菜单项和快捷键将不再可用
- 传入的命令 ID 必须是通过 [ak.wwise.ui.commands.register](ak.wwise.ui.commands.register.md) 注册过的

## 相关函数

- [ak.wwise.ui.commands.register](ak.wwise.ui.commands.register.md)
- [ak.wwise.ui.commands.execute](ak.wwise.ui.commands.execute.md)

## 相关Topic

- [Defining Command Add-ons](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=defining_command_addons.html)
- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.commands.unregister](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_commands_unregister.html)
