# ak.wwise.core.sourceControl.getSourceFiles

▎ **命名空间**: ak.wwise.core.sourceControl

## 概述

Retrieve all original files.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| folder | string | 否 | Originals 文件夹 | Base folder for search relative to Originals folder. |
| recursive | boolean | 否 | true | Search in all subfolders of the base folder. |
| filter | string | 否 | all | Filter the files in the search result. 可选值：all（全部文件，默认）、used（仅工程中使用的文件）、unused（仅工程中未使用的文件）。 |

## Options

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of fields to return for each file or folder found. 可选值：isUsed、usage、isMissing、file、folder。 |
| objectReturn | array | The array of return expressions defines which elements of the Wwise object is returned（用于 usage 中的 Wwise 对象属性）。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array (必填) | Files and folders found. |
| return[...] | object | Specifies what is returned for every item found. |
| return[...].file | string | File path relative to Originals folder. |
| return[...].folder | string | Folder path relative to Originals folder. |
| return[...].isUsed | boolean | Indicates whether a file is used by a Wwise Object in the project. |
| return[...].usage | array | List of objects from the project that are using this file. |
| return[...].isMissing | boolean | Indicates if the file is absent in the source manager. |

## JSON-RPC 请求示例

```json
{
    "folder": "",
    "recursive": true,
    "filter": "used"
}
```

## JSON-RPC 响应示例

```json
{
    "return": [
        {
            "file": "Player\\footstep_01.wav",
            "isUsed": true,
            "usage": [
                {
                    "id": "{AAAAAAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE}",
                    "name": "Footstep_SFX"
                }
            ]
        }
    ]
}
```

## 注意事项

- `folder` 路径相对于 Originals 文件夹。
- 通过 `filter: "unused"` 可以查找工程中未被引用的原始文件，便于清理。

## 相关函数

- ak.wwise.core.sourceControl.getStatus

## 相关 Topic

- Source Manager
- 版本控制（Source Control）

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sourcecontrol_getsourcefiles.html
