# ak.wwise.core.getProjectInfo

## ▎ 命名空间: ak.wwise.core

## 概述

获取当前打开项目的信息，包括平台、语言和项目目录。注意：项目名称可能与 WPROJ 文件名不同（如果在项目创建后重命名了文件）。

## 参数

（无参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| name * | string | 项目名称。注意：项目名称可能与 WPROJ 文件名不同 |
| displayTitle * | string | Wwise 标题栏的完整文本 |
| path * | string | WPROJ 文件的绝对路径 |
| id * | string | 项目 ID，GUID 格式：`{aabbcc00-1122-3344-5566-77889900aabb}` |
| isDirty * | boolean | 如果项目或任何 Work Unit 有未保存的更改则为 true |
| currentLanguageId * | string | 用户界面中设置的当前语言，GUID 格式 |
| referenceLanguageId * | string | 语言设置中的参考语言，GUID 格式 |
| currentPlatformId * | string | 用户界面中设置的当前平台，GUID 格式 |
| languages * | array | 项目中定义的语言数组 |
| languages[...].id * | string | 语言唯一 ID，GUID 格式 |
| languages[...].name * | string | 语言名称 |
| languages[...].shortId * | integer | 语言的短 ID（32位）。范围：[0,4294967295] |
| platforms * | array | 项目中定义的平台数组 |
| platforms[...].id * | string | 平台唯一 ID，GUID 格式 |
| platforms[...].name * | string | 项目中定义的平台名称 |
| platforms[...].baseName * | string | 文件系统中使用的部署平台名称 |
| platforms[...].baseDisplayName * | string | 部署平台的官方名称（可能包含特殊字符） |
| platforms[...].soundBankPath * | string | 为此平台生成 SoundBank 文件的路径 |
| platforms[...].copiedMediaPath * | string | 为此平台复制 SoundBank 媒体文件的路径 |
| defaultConversion * | object | 项目中使用的默认 Conversion Settings 对象 |
| defaultConversion.id * | string | Conversion Settings 唯一 ID，GUID 格式 |
| defaultConversion.name * | string | Conversion Settings 对象名称 |
| directories * | object | Wwise 使用的目录集合 |
| directories.root * | string | 项目根目录，wproj 文件所在位置 |
| directories.cache * | string | 项目的 .cache 目录，包含转换后的媒体文件（WEM 文件） |
| directories.originals * | string | 项目的 Originals 目录，包含按语言分隔的 WAV 文件 |
| directories.soundBankOutputRoot * | string | 项目的 SoundBank 输出根目录，包含 C++ 头文件、XML 和 JSON 文件 |
| directories.commands * | string | 项目的 Commands 目录 |
| directories.properties * | string | 项目的 Properties 目录 |

(* 必填)

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.getProjectInfo",
  "params": {},
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {
    "name": "IntegrationDemo",
    "displayTitle": "IntegrationDemo - Wwise 2022.1.0",
    "path": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\WwiseProject\\IntegrationDemo.wproj",
    "id": "{4DA5940A-0C59-43B3-A8FD-8AFFC0DA0711}",
    "isDirty": false,
    "currentLanguageId": "{C7DD1F00-ECD1-4598-B60F-EAE32C06EC46}",
    "referenceLanguageId": "{C7DD1F00-ECD1-4598-B60F-EAE32C06EC46}",
    "currentPlatformId": "{A2D401DE-B8B6-4FEB-8142-137C34D507CB}",
    "languages": [
      {
        "id": "{C7DD1F00-ECD1-4598-B60F-EAE32C06EC46}",
        "name": "English(US)",
        "shortId": 684519430
      }
    ],
    "platforms": [
      {
        "id": "{A2D401DE-B8B6-4FEB-8142-137C34D507CB}",
        "name": "Android",
        "baseName": "Android",
        "baseDisplayName": "Android™",
        "soundBankPath": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\Android\\assets\\GeneratedSoundBanks\\Android\\",
        "copiedMediaPath": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\Android\\assets\\GeneratedSoundBanks\\Android\\Media"
      }
    ],
    "defaultConversion": {
      "id": "{3A429FCB-87D8-458B-B315-DBE8023064B3}",
      "name": "SFX"
    },
    "directories": {
      "root": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\WwiseProject\\",
      "cache": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\WwiseProject\\.cache\\",
      "originals": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\WwiseProject\\Originals\\",
      "soundBankOutputRoot": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\WwiseProject\\GeneratedSoundBanks\\",
      "commands": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\WwiseProject\\Add-ons\\Commands",
      "properties": "C:\\Wwise\\SDK\\samples\\IntegrationDemo\\WwiseProject\\Add-ons\\Properties"
    }
  },
  "id": 1
}
```

## 注意事项

- 项目名称可能与 WPROJ 文件名不同，以返回值中的 `name` 字段为准。
- `isDirty` 为 true 时表示有未保存的更改。
- `currentLanguageId` 和 `currentPlatformId` 是当前 Wwise 界面中选中的语言和平台。
- 平台特定的 SoundBank 路径信息在 `platforms` 数组中，`directories.soundBankOutputRoot` 是根目录。

## 相关函数

- [[ak.wwise.core.getInfo]] — 获取 Wwise 全局信息
- [[ak.wwise.core.project.save]] — 保存项目

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.getProjectInfo](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_getprojectinfo.html)
- [示例：获取当前项目信息](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_getprojectinfo_example_getting_the_information_about_the_current_project.html)
