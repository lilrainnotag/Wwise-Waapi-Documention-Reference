# ak.wwise.core.soundbank.processDefinitionFiles

▎ **命名空间**: ak.wwise.core.soundbank

## 概述

Imports SoundBank definitions from the specified file. Multiple files can be specified. See the WAAPI log for status messages.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| files | array | 是 | — | An array of SoundBank definition files. |
| files[...] | string | — | — | SoundBank Definition Files（文件路径）。 |

## 返回值

（官网未提供 — 操作结果通过 WAAPI log 查看）

## JSON-RPC 请求示例

```json
{
    "files": [
        "soundbank_definitions_1-3.txt",
        "soundbank_definitions_4-401"
    ]
}
```

## JSON-RPC 响应示例

（官网未提供 — 通过 ak.wwise.core.log.get 获取日志查看导入状态）

## 注意事项

- 支持一次导入多个 SoundBank 定义文件。
- 使用 ak.wwise.core.log.get 查看导入过程中的状态消息。

## 相关函数

- ak.wwise.core.audio.import
- ak.wwise.core.log.get

## 相关 Topic

- tab-delimited-import

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_processdefinitionfiles.html
