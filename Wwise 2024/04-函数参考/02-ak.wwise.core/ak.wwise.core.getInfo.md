# ak.wwise.core.getInfo

## ▎ 命名空间: ak.wwise.core

## 概述

获取 Wwise 的全局信息，包括版本、平台、目录、进程信息等。

## 参数

（无参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| sessionId * | string | Wwise 会话 ID，GUID 格式：`{aabbcc00-1122-3344-5566-77889900aabb}` |
| apiVersion * | number | Wwise Authoring API 版本号。范围：[1,*] |
| displayName * | string | Wwise 显示名称 |
| branch * | string | 构建分支 |
| copyright * | string | 版权信息 |
| version * | object | Wwise 版本对象 |
| version.displayName * | string | Wwise 版本名称 |
| version.year * | integer | 版本年份。范围：[2000,2100] |
| version.major * | integer | 主版本号。范围：[0,100] |
| version.minor * | integer | 次版本号。范围：[0,100] |
| version.build * | integer | 构建号。范围：[1,*] |
| version.nickname * | string | 版本的特殊名称 |
| version.schema * | integer | Wwise 项目和 Work Unit 的 Schema 版本。范围：[1,*] |
| configuration * | string | 指示是 Release 还是 Debug 构建。可选值：`release`, `debug` |
| platform * | string | 指示 Wwise 构建的平台。可选值：`x64`, `win32`, `macosx`, `linux` |
| isCommandLine * | boolean | 指示 Wwise 是否以命令行模式运行 |
| processId * | integer | Wwise 进程标识符 |
| processPath * | string | Wwise 进程路径 |
| directories * | object | Wwise 使用的目录集合 |
| directories.install * | string | Wwise 根目录（安装目录） |
| directories.authoring * | string | Wwise Authoring 根目录 |
| directories.bin * | string | bin 目录，Wwise.exe 所在位置 |
| directories.help * | string | 帮助目录 |
| directories.user * | string | Wwise 用户数据根目录 |

(* 必填)

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.getInfo",
  "params": {},
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {
    "displayName": "Wwise",
    "platform": "x64",
    "directories": {
      "help": "C:\\Projects\\Wwise\\Authoring\\Help\\",
      "user": "%APPDATA%\\Audiokinetic\\Wwise\\",
      "install": "C:\\Projects\\Wwise\\",
      "authoring": "C:\\Projects\\Wwise\\Authoring\\",
      "bin": "C:\\Projects\\Wwise\\Authoring\\source\\App\\"
    },
    "branch": "v2016.2/wwise_main",
    "configuration": "debug",
    "version": {
      "displayName": "v2017.1.0",
      "nickname": "",
      "build": 83,
      "minor": 0,
      "year": 2017,
      "major": 1,
      "schema": 103
    },
    "copyright": "© 2006-2017. Audiokinetic Inc. All rights reserved.",
    "apiVersion": 1,
    "isCommandLine": false,
    "processId": 12345,
    "processPath": "C:\\Projects\\Wwise\\Authoring\\x64\\Release\\bin\\Wwise.exe",
    "sessionId": "{FF59687C-48CF-4385-B1C5-CE84B0A63880}"
  },
  "id": 1
}
```

## 注意事项

- 此函数不需要任何参数，调用时 `params` 可以为空对象 `{}`。
- `sessionId` 是当前 Wwise 会话的唯一标识符，格式为 GUID。
- `platform` 和 `configuration` 是枚举值，分别指示平台和构建类型。

## 相关函数

- [[ak.wwise.core.getProjectInfo]] — 获取当前项目信息
- [[ak.wwise.core.ping]] — 验证 WAAPI 是否可用

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.getInfo](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_getinfo.html)
- [示例：获取 Wwise 信息](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_getinfo_example_getting_information_about_wwise.html)
