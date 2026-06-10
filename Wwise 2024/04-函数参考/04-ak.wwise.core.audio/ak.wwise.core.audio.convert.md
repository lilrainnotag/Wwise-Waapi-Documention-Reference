# ak.wwise.core.audio.convert

## ▎ 命名空间: ak.wwise.core.audio

## 概述

创建转换后的音频文件。发生错误时，此函数会返回带有相应严重级别的消息列表。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| objects * | array | 是 | — | 对象数组。每个对象可以是 ID (GUID)、名称或对象路径 |
| objects [...] | string (GUID/名称/路径) | 是 | — | 对象标识符，支持：`type:name`、`Global:shortId`、GUID 或项目路径 |
| platforms * | array | 是 | — | 平台数组。每个平台是 ID (GUID) 或唯一名称 |
| platforms [...] | string (GUID/名称) | 是 | — | 平台的 GUID 或唯一名称 |
| languages * | array | 是 | — | 语言数组。每种语言是唯一名称 |
| languages [...] | string | 是 | — | 语言名称 |

(* 必填)

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| errors | array | 带有相关消息和严重级别的日志条目列表 |
| errors[...].severity | string | 日志消息的严重级别。可选值：`Message`（不影响操作完整性）、`Warning`（可能影响）、`Error`（影响）、`Fatal Error`（阻止完成） |
| errors[...].message | string | 系统记录的消息（错误或警告） |

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audio.convert",
  "params": {
    "objects": [
      "\\Actor-Mixer Hierarchy\\Default Work Unit\\Hello"
    ],
    "platforms": [
      "Windows"
    ],
    "languages": [
      "SFX"
    ]
  },
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {
    "errors": []
  },
  "id": 1
}
```

## 注意事项

- 此函数用于将原始音频文件转换为 Wwise 使用的 WEM 格式。
- 返回的 `errors` 数组为空表示转换成功，无错误。
- 严重级别说明：`Message`（不影响操作）、`Warning`（可能影响）、`Error`（影响操作完整性）、`Fatal Error`（阻止操作完成）。
- 对象、平台、语言三个参数都是必填的。

## 相关函数

- [[ak.wwise.core.audio.setConversionPlugin]] — 设置转换插件
- [[ak.wwise.core.audio.import]] — 导入音频文件

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audio.convert](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_convert.html)
- [示例：转换 Wwise 对象](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_convert_example_convert_a_wwiseobject.html)
