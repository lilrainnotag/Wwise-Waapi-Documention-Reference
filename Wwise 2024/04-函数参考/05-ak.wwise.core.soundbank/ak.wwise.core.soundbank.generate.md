# ak.wwise.core.soundbank.generate

▎ **命名空间**: ak.wwise.core.soundbank

## 概述

Generate a list of SoundBanks with the import definition specified in the WAAPI request. If you do not write the SoundBanks to disk, subscribe to ak.wwise.core.soundbank.generated to receive SoundBank structure info and the bank data as base64. Note: This is a synchronous operation.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| soundbanks | array | 否 | 全部用户定义的 SoundBank | List of user-defined SoundBanks to generate. If the array is empty then all user-defined SoundBanks are generated. Note that auto-defined SoundBanks cannot be specified, and all auto-defined SoundBanks are generated regardless of this parameter. |
| soundbanks[...] | object | — | — | SoundBank Info. |
| soundbanks[...].name | string | 是 | — | The name of the user-defined SoundBank to generate. A temporary SoundBank will be created if the SoundBank doesn't exist. Auto-defined SoundBanks cannot be specified. |
| soundbanks[...].events | array | 否 | — | List of events to include in this SoundBank. Not required if the bank already exists. |
| soundbanks[...].events[...] | string (name/GUID/path) | — | — | The ID (GUID), name (type:name or Global:shortId), or path of the event to include. 支持格式：Event:Play_Sound_01、Global:245489792、{GUID}、或工程路径。 |
| soundbanks[...].auxBusses | array | 否 | — | List of AuxBus to include in this SoundBank. |
| soundbanks[...].auxBusses[...] | string (name/GUID/path) | — | — | The ID (GUID), name, or path of the Auxiliary Bus to include. |
| soundbanks[...].inclusions | array | 否 | — | List of inclusion type to use for this SoundBank. Not required if the bank already exists. 可选值: "event", "structure", "media" |
| soundbanks[...].rebuild | boolean | 否 | false | Force rebuild of this particular SoundBank. |
| platforms | array | 否 | 全部平台 | List of platforms to generate. If you don't specify any platforms, all the platforms will be generated. |
| platforms[...] | string | — | — | The ID (GUID) or the name of the platform. |
| languages | array | 否 | 全部语言 | List of languages to generate. If you don't specify any languages, all the languages will be generated. |
| languages[...] | string | — | — | The ID (GUID) or name of the language. |
| skipLanguages | boolean | 否 | false | By default, if you don't specify any languages all languages will be generated. If you set this parameter to true, no localized SoundBank will be generated. |
| rebuildSoundBanks | boolean | 否 | false | Will rebuild all SoundBanks if true. If you want to clear the converted media as well, use clearAudioFileCache parameter. |
| clearAudioFileCache | boolean | 否 | false | Deletes the content of the Wwise audio file cache folder prior to converting source files and generating SoundBanks, which ensures that all source files are reconverted. Note that the whole cache is cleared, for all platforms, regardless of the platforms arguments. |
| writeToDisk | boolean | 否 | false | Use the normal SoundBank generation process and write the sound bank and info file to disk. |
| rebuildInitBank | boolean | 否 | — | If you don't use rebuildSoundBanks, use this option to force a rebuild of the Init bank for each specified platform. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| logs | array | The SoundBank generation log. The log is empty when used in WwiseConsole. |
| logs[...] | object | A log entry. |
| logs[...].severity | string (必填) | 日志级别。可选值：Message（不影响操作完整性）、Warning（可能影响）、Error（影响操作完整性）、Fatal Error（阻止操作完成） |
| logs[...].time | integer (必填) | Number of seconds elapsed since midnight (00:00:00), January 1, 1970, Coordinated Universal Time (UTC). |
| logs[...].messageId | string (必填) | The message ID for the log item. |
| logs[...].message | string (必填) | The description message of the log item. |
| logs[...].platform | object | The platform ID and name for which the log item was reported（包含 id, name, notes, type, pluginName, path, parent, owner, isPlayable, shortId, classId, category, filePath, workunit 等完整属性）。 |

## JSON-RPC 请求示例

### 示例 1：生成现有 SoundBank（不写入磁盘，通过 WAAPI 流式传输）

```json
{
    "soundbanks": [
        {
            "name": "SampleBank"
        },
        {
            "name": "AnotherBank"
        }
    ],
    "platforms": [
        "Windows",
        "Linux"
    ],
    "languages": [
        "English(US)"
    ]
}
```

### 示例 2：通过指定 inclusions 生成新 SoundBank

```json
{
    "soundbanks": [
        {
            "name": "SampleBank",
            "events": [
                "Event:Play_Footsteps",
                "Event:Play_Music"
            ],
            "auxBusses": [
                "AuxBus:Cavern"
            ],
            "inclusions": [
                "event",
                "structure",
                "media"
            ]
        }
    ],
    "platforms": [
        "Windows",
        "Linux"
    ]
}
```

## JSON-RPC 响应示例

```json
{
    "logs": [
        {
            "severity": "Message",
            "time": 1574290800,
            "messageId": "GenerateProcessEnd",
            "message": "Generation completed."
        }
    ]
}
```

## 注意事项

- 这是一个**同步操作**，在生成完成之前会阻塞调用方。
- 如果不设置 `writeToDisk: true`，SoundBank 不会写入磁盘，需要通过订阅 `ak.wwise.core.soundbank.generated` 来获取 bank 数据（base64）。
- `soundbanks` 数组为空时，会生成所有用户定义的 SoundBank。
- Auto-defined SoundBank 不能通过 `soundbanks` 参数指定，但无论怎样都会被生成。
- `clearAudioFileCache` 会清除整个缓存文件夹（所有平台），不受 platforms 参数影响。

## 相关函数

- ak.wwise.core.soundbank.getInclusions
- ak.wwise.core.soundbank.setInclusions
- ak.wwise.core.soundbank.processDefinitionFiles

## 相关 Topic

- ak.wwise.core.soundbank.generated (订阅)
- SoundBank 生成

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_generate.html
