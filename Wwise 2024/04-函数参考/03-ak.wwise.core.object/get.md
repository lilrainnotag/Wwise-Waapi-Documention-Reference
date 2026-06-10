# ak.wwise.core.object.get

> **命名空间**: ak.wwise.core.object
> **函数URI**: `ak.wwise.core.object.get`

## 概述

执行查询并返回结果中每个对象的数据（根据options指定）。查询可以通过'waql'参数或已弃用的'from'参数（配合可选的'transform'参数）来指定。详见《Using the Wwise Authoring Query Language (WAQL)》和《Querying the Wwise Project》。返回数据的具体内容通过 Return Options 控制。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| waql | string | 否 | - | 使用WAQL语言指定的查询。详见《Using the Wwise Authoring Query Language (WAQL)》 |
| from | one of | 否(已弃用) | - | 查询的起始点。**注意：此参数已弃用，建议使用WAQL参数代替**。支持指定id、search、name、path、ofType、query字段的对象 |
| from.id | array | 否 | - | 对象ID数组，支持GUID或Short ID (uint32) |
| from.id [...] | one of | 否 | - | GUID字符串（格式：{aabbcc00-1122-3344-5566-77889900aabb}）或包含shortId和type的对象 |
| from.id[...].shortId | integer | 是(如果使用Short ID) | - | 对象的Short ID。范围: [0, 4294967295] |
| from.id[...].type | integer | 是(如果使用Short ID) | - | **已弃用**。Short ID对应的对象类型。例如: 10(Event), 12(SwitchGroup), 14(StateGroup), 17(EffectPlugin), 18(SoundBank), 19(Bus), 20(AuxBus), 22(GameParameter), 41(Trigger), 68(AudioDevicePlugin)。范围: [1, *] |
| from.search | array | 否 | - | 用于搜索项目的文本token数组 |
| from.search [...] | string | 否 | - | 搜索token |
| from.name | array | 否 | - | 对象唯一限定名数组。格式: type:name 或 Global:shortId，例如 Event:Play_Sound_01, Global:245489792 |
| from.path | array | 否 | - | 对象路径数组。例如: \Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX |
| from.ofType | array | 否 | - | 对象类型数组。详见《Wwise Objects Reference》 |
| from.query | array | 否 | - | 查询对象ID数组。每个元素为GUID字符串 |
| transform | array | 否 | - | 对"from"返回结果依次应用的变换链 |
| transform[...].select | array | 否 | - | 选择器数组（仅1个）。可选值: parent, children, descendants, ancestors, referencesTo |
| transform[...].range | array | 否 | - | 两个数字组成的数组，指定结果的边界索引。例如 [0, 100] 获取前100条 |
| transform[...].where | array | 否 | - | 两个token组成的过滤数组。第一个是过滤谓词名称，第二个是参数。详见《Querying the Wwise Project》 |

### Options（选项参数）

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | - | 指定每个对象返回的内容。可包含内置访问器（id, name, notes, type, path, parent, owner, isPlayable, shortId, classId, category, filePath, workunit, childrenCount, totalSize, mediaSize, objectSize, structureSize等）或对象属性（如Volume, Pitch等），使用点分隔的访问器语法 |
| platform | any of | 否 | 当前平台 | 平台ID (GUID) 或名称 |
| language | any of | 否 | - | 语言ID (GUID) 或名称 |

### return 支持的内置访问器

id, name, notes, type, pluginName, shortId, classId, category, filePath, workunit, parent, owner, path, isPlayable, childrenCount, totalSize, mediaSize, objectSize, structureSize, sound:convertedWemFilePath, sound:originalWavFilePath, soundbank:bnkFilePath, music:transitionRoot, music:playlistRoot, audioSource:playbackDuration, audioSource:maxDurationSource, audioSource:trimValues, audioSource:maxRadiusAttenuation, audioSource:language, workunit:isDefault, workunit:type, workunit:isDirty, switchContainerChild:context, convertedWemFilePath, originalFilePath, originalRelativeFilePath, convertedFilePath, originalWavFilePath, soundbankBnkFilePath, musicTransitionRoot, musicPlaylistRoot, playbackDuration, duration, maxDurationSource, audioSourceTrimValues, maxRadiusAttenuation, audioSourceLanguage, workunitIsDefault, workunitType, workunitIsDirty, switchContainerChildContext, isExplicitMute, isExplicitSolo, isImplicitMute, isImplicitSolo, isIncluded, points, stateProperties, stateGroups, blendTracks

以及通过 `@属性名`（单@获取对象值）或 `@@属性名`（双@获取override源的值）访问的任意Wwise对象属性。详见《Wwise Objects Reference》。

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | 查询到的对象数组，每个对象包含options中指定的属性 |
| return[...].id | string | 对象的ID (GUID)，格式: {aabbcc00-1122-3344-5566-77889900aabb} |
| return[...].name | string | 对象名称 |
| return[...].notes | string | 对象注释 |
| return[...].type | string | 对象类型 |
| return[...].pluginName | string | 插件名称（Source, Effect, Mixer, Device 和 Metadata 插件） |
| return[...].path | string | 从项目根目录的对象路径 |
| return[...].parent | object | 层次结构中的父对象（含id和name） |
| return[...].owner | object | 对象的拥有者（含id和name） |
| return[...].isPlayable | boolean | 对象是否可在Transport中播放 |
| return[...].shortId | integer | 对象的Short ID |
| return[...].classId | integer | 对象的class ID |
| return[...].category | string | 对象类别 |
| return[...].filePath | string | 包含该对象的文件路径 |
| return[...].workunit | object | 包含该对象的Work Unit（含id和name） |
| return[...].childrenCount | number | **已弃用**。子对象数量，建议使用 children.count() |
| return[...].totalSize | integer | 对象及其所有子对象在SoundBank中占用的空间（字节） |
| return[...].mediaSize | integer | 对象及其所有子对象的媒体文件总转换大小（字节） |
| return[...].objectSize | integer | 对象元数据在SoundBank中占用的空间（字节） |
| return[...].structureSize | integer | 对象及其所有子对象的元数据在SoundBank中占用的空间（字节） |
| return[...].duration | object | 持续时间信息（含min, max, type） |
| return[...].maxDurationSource | object | 最长持续时间的音频源对象 |
| return[...].audioSourceTrimValues | object | 音频源修剪时间范围（trimBegin, trimEnd） |
| return[...].maxRadiusAttenuation | object | 最大半径的衰减对象 |
| return[...].audioSourceLanguage | object | 与音频源关联的语言对象 |
| return[...].isExplicitMute | boolean | 对象是否被显式静音 |
| return[...].isExplicitSolo | boolean | 对象是否被显式独奏 |
| return[...].isImplicitMute | boolean | 对象是否被隐式静音 |
| return[...].isImplicitSolo | boolean | 对象是否被隐式独奏 |
| return[...].isIncluded | boolean | 对象是否被包含 |
| return[...].points | array | 曲线对象的点数组（仅适用于Curve对象） |
| return[...].stateProperties | array | 状态属性名称数组 |
| return[...].stateGroups | array | 关联的State Group对象数组 |

## JSON-RPC 请求示例

### 示例1：获取对象名称

```json
{
    "method": "ak.wwise.core.object.get",
    "params": {
        "waql": "\"{24979032-B170-43E3-A2E4-469E0193E2C3}\"",
        "return": [
            "name"
        ]
    }
}
```

### JSON-RPC 响应示例

```json
{
    "return": [
        {
            "name": "MyObjectName"
        }
    ]
}
```

## 注意事项

- `from` 参数已弃用，建议使用 `waql` 参数代替
- `from.id[...].type` 语法已弃用，建议使用 WAQL
- `childrenCount` 已弃用，建议使用 `children.count()`
- `musicTransitionRoot` 和 `musicPlaylistRoot` 已弃用，应使用 TransitionRoot 和 PlaylistRoot 引用
- 部分以 `sound:`、`soundbank:`、`music:` 等前缀的访问器为旧版命名，对应的新版访问器去掉了前缀和冒号
- 返回的媒体大小和SoundBank大小需要先生成SoundBank才能准确
- 在Mac上使用WAAPI时请注意文件路径格式

## 相关函数

- ak.wwise.core.object.set
- ak.wwise.core.object.create
- ak.wwise.core.object.delete
- ak.wwise.core.object.diff
- ak.wwise.core.object.getPropertyNames
- ak.wwise.core.object.getPropertyAndReferenceNames
- ak.wwise.core.object.getPropertyInfo
- ak.wwise.core.object.getTypes

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_get.html
- 示例-获取对象名称: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_get_example_getting_an_object_s_name.html
