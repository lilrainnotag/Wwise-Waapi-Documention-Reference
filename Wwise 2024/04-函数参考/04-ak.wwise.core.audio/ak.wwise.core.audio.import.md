# ak.wwise.core.audio.import

## ▎ 命名空间: ak.wwise.core.audio

## 概述

创建 Wwise 对象并导入音频文件。此函数在导入过程中发生错误时不会返回错误，请参考日志以获取每个导入命令的结果。此函数使用与 Audio File Importer 中 Tab Delimited 导入相同的导入处理器。函数返回所有已创建、替换或重用的对象数组。使用 options 参数指定如何返回对象。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| importOperation | string | 否 | `useExisting` | 确定导入对象的创建方式。可选值：`createNew`（创建新对象）、`useExisting`（使用已存在对象或创建新对象）、`replaceExisting`（创建新对象并销毁同名对象） |
| default | object | 否 | — | 每个导入项的默认值，用于避免重复指定公共属性 |
| default.importLanguage | string | 否 | — | 音频文件导入的语言（来自项目定义的语言列表） |
| default.importLocation | string (GUID/名称/路径) | 否 | — | 用作根相对对象路径的对象 ID、名称或路径 |
| default.audioFile | string | 否 | — | 要导入的媒体文件路径，必须可从 Wwise 访问 |
| default.audioFileBase64 | string | 否 | — | Base64 编码的 WAV 音频文件数据，格式：`'MySound.wav\|UklGRu...'` |
| default.originalsSubFolder | string | 否 | — | 指定放置导入音频文件的 originals 子文件夹 |
| default.objectPath | string | 否 | — | 要创建对象的路径和名称 |
| default.objectType | string | 否 | — | 导入音频文件时创建的对象类型 |
| default.notes | string | 否 | — | 创建对象的 "Notes" 字段 |
| default.audioSourceNotes | string | 否 | — | 创建的音频源对象的 "Notes" 字段 |
| default.switchAssignation | string | 否 | — | 定义与 Switch Container 关联的 Switch Group 或 State Group |
| default.event | string | 否 | — | 定义要为导入对象创建的 Event 的路径和名称 |
| default.dialogueEvent | string | 否 | — | 定义要为导入对象创建的 Dialogue Event 的路径和名称 |
| default.@Property | any | 否 | — | Wwise 对象属性（以 @ 为前缀），如 `@Volume:3` |
| imports * | array | 是 | — | 导入命令数组 |
| imports[...] | object | 是 | — | 导入命令对象，成员与 `default` 合并，此处优先级更高 |
| imports[...].objectPath * | string | 是 | — | 要创建对象的路径和名称（必填） |
| imports[...].audioFile | string | 否 | — | 媒体文件路径 |
| imports[...].importLanguage | string | 否 | — | 语言设置 |
| imports[...].objectType | string | 否 | — | 对象类型 |
| imports[...].@Property | any | 否 | — | 对象属性值 |
| autoAddToSourceControl | boolean | 否 | `true` | 是否自动对导入文件执行 Source Control Add 操作 |
| autoCheckOutToSourceControl | boolean | 否 | `true` | 是否自动对修改文件执行 Source Control Checkout 操作 |

(* 必填)

## 选项

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | 指定每个对象返回的内容。可包含内置访问器（id, name, notes, type, path 等）或对象属性 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| objects | array | 创建、替换或重用的对象数组 |
| files | array | 导入的文件路径数组 |
| log | array | 导入日志条目数组 |

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audio.import",
  "params": {
    "importOperation": "useExisting",
    "default": {
      "importLanguage": "SFX"
    },
    "imports": [
      {
        "audioFile": "C:\\audio0.wav",
        "objectPath": "\\Actor-Mixer Hierarchy\\Default Work Unit\\<Sound SFX>MySound"
      }
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
    "log": [],
    "files": [
      "C:\\Projects\\Example\\Originals\\SFX\\audio0.wav"
    ],
    "objects": [
      {
        "id": "{FAF8DDCD-D1B2-4EC6-997F-CB9BE9703544}",
        "name": "audio0"
      },
      {
        "id": "{5F444FD2-1203-4205-B8FA-F9DAB3F5F74C}",
        "name": "MySound"
      }
    ]
  },
  "id": 1
}
```

## 注意事项

- 即使导入过程中发生错误，此函数也不会返回错误，需要检查返回结果中的 `log` 数组。
- `default` 对象中的属性会应用到每个 `imports` 条目中，`imports` 条目的属性优先级更高。
- `audioFileBase64` 允许通过 Base64 编码直接传输音频数据，而不需要 Wwise 访问文件系统。
- `objectPath` 中的对象类型用尖括号指定，如 `<Sound SFX>MySound`。
- `importLanguage` 必须是项目 WPROJ 文件中 LanguageList 定义的语言。

## 相关函数

- [[ak.wwise.core.audio.importTabDelimited]] — Tab Delimited 格式导入
- [[ak.wwise.core.audio.convert]] — 转换音频文件
- [[ak.wwise.core.log.get]] — 获取日志

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audio.import](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_import.html)
- [示例：使用绝对路径导入音频文件](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_import_example_importing_an_audio_file_to_create_a_sound_sfx_using_an_absolute_object_path.html)
