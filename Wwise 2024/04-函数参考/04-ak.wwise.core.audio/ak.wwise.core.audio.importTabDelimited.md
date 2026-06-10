# ak.wwise.core.audio.importTabDelimited

## ▎ 命名空间: ak.wwise.core.audio

## 概述

从 Tab Delimited 文件进行脚本化对象创建和音频文件导入。此功能与 Wwise 中 Audio File Importer 的 Tab Delimited 导入功能对应。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| importLocation | string (GUID/名称/路径) | 否 | — | 用作根相对对象路径的对象 ID、名称或路径 |
| importLanguage * | string | 是 | — | 音频文件导入的语言（来自项目 WPROJ 文件中定义的语言列表） |
| importOperation * | string | 是 | — | 导入对象创建方式。可选值：`createNew`（创建新对象）、`useExisting`（使用已存在或创建新对象）、`replaceExisting`（替换已存在对象） |
| importFile * | string | 是 | — | Tab Delimited 导入文件的位置 |
| autoAddToSourceControl | boolean | 否 | `true` | 是否自动对导入文件执行 Source Control Add 操作 |
| autoCheckOutToSourceControl | boolean | 否 | `true` | 是否自动对修改文件执行 Source Control Checkout 操作 |

(* 必填)

## 选项

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | 指定每个对象返回的内容，可包含内置访问器（id, name, type, path 等）或对象属性（如 @Volume） |
| platform | string (GUID/名称) | 平台 ID 或名称，不指定时使用当前平台 |
| language | string (GUID/名称) | 语言 ID 或名称 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| objects | array | 导入过程中创建的对象数组 |
| objects[...].id | string | 对象的 ID (GUID) |
| objects[...].name | string | 对象名称 |
| objects[...].type | string | 对象类型 |
| objects[...].path | string | 对象从项目根目录的路径 |

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audio.importTabDelimited",
  "params": {
    "importLocation": "{A076AA65-B71A-45BB-8841-5A20C52CE727}",
    "importLanguage": "SFX",
    "importOperation": "createNew",
    "importFile": "C:\\MyWaves\\MyFolder\\myImportFile.txt"
  },
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {
    "objects": [
      {
        "id": "{02AC7121-AF3D-48C4-BEEA-25BD5EA4FB1E}",
        "name": "My SFX 0"
      },
      {
        "id": "{A014BD8D-E7DA-4401-A1F9-C36829A1B77C}",
        "name": "My SFX 1"
      }
    ]
  },
  "id": 1
}
```

## 注意事项

- `importFile` 必须指向一个格式正确的 Tab Delimited 文本文件，格式与 Wwise Audio File Importer 的 Tab Delimited 导入相同。
- `importLanguage` 必须是项目 WPROJ 文件中已定义的语言。
- 与 `ak.wwise.core.audio.import` 不同，此函数通过读取预定义的文本文件来批量导入，适合大规模自动化导入场景。
- 返回值中的对象属性由 `return` 选项决定，默认返回 `id` 和 `name`。

## 相关函数

- [[ak.wwise.core.audio.import]] — 通过 JSON 参数直接导入音频文件

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audio.importTabDelimited](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_importtabdelimited.html)
- [示例：导入音频文件](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_importtabdelimited_example_importing_an_audio_file.html)
