# ak.wwise.core.executeLuaScript

## ▎ 命名空间: ak.wwise.core

## 概述

执行 Lua 脚本。可以选择性地指定额外的 Lua 搜索路径、附加模块以及在主脚本之前加载的附加 Lua 脚本。脚本可以返回一个值。所有参数将通过全局变量 `wa_args` 传递给 Lua 脚本。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| luaScript * | string | 是 | — | 定义要加载和执行的主 Lua 文件 |
| luaPaths | array | 否 | — | 定义用于搜索附加 Lua 模块的路径数组。示例：`'C:/path_to_folder/?.lua'` |
| luaPaths [...] | string | 否 | — | 路径选项的值 |
| requires | array | 否 | — | 定义在运行时使用 require 系统加载的附加模块。注意：以下文件夹会自动添加到 Lua 路径中：`PROJECT/Add-ons/Lua`、`APPDATA/Audiokinetic/Wwise/Add-ons/Lua`、`INSTALLDIR/Authoring/Data/Add-ons/Lua` |
| requires [...] | string | 否 | — | 模块选项的值 |
| doFiles | array | 否 | — | 定义在主 Lua 脚本加载和执行之前要加载的附加 Lua 文件。也可以指定一个目录，该目录中的所有 Lua 文件都将被加载 |
| doFiles [...] | string | 否 | — | 文件选项的值 |

(* 必填)

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return * | boolean / object / array / number / string | Lua 脚本返回的结果。在脚本末尾使用 return 语句 |

(* 必填)

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- 脚本通过全局变量 `wa_args` 接收传递的参数。
- 使用 `require` 加载模块时，以下路径会自动添加到 Lua 搜索路径中：项目 Add-ons/Lua 目录、用户数据 Add-ons/Lua 目录、安装目录 Add-ons/Lua 目录。
- `doFiles` 参数可以指定单个文件或整个目录，指定目录时会加载目录中的所有 Lua 文件。
- 返回值类型可以是 boolean、object、array、number 或 string，具体取决于 Lua 脚本的 return 语句。

## 相关函数

（无）

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.executeLuaScript](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_executeluascript.html)
