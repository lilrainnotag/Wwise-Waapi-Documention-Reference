# ak.wwise.core.object.set

> **命名空间**: ak.wwise.core.object
> **函数URI**: `ak.wwise.core.object.set`

## 概述

允许对以下操作进行批量处理：在子层级中创建对象、在列表中创建对象、设置名称、注释、属性和引用。关于创建对象的更多信息，参见《Importing Audio Files and Creating Structures》。另请参见 ak.wwise.core.audio.import 以将音频文件导入到 Wwise。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| objects | array | 是 | - | 要设置值和创建子对象或列表对象的对象数组 |
| objects[...].object | any of | 是 | - | 现有对象的ID (GUID)、名称或路径，在该对象上设置名称/注释/属性/引用，并在其下创建子对象或在列表中创建对象。支持格式: type:name（如 Event:Play_Sound_01）、GUID、项目路径 |
| objects[...].platform | any of | 否 | 所有平台 | 设置属性的平台ID或名称。不指定则为所有链接平台设置值 |
| objects[...].onNameConflict | string | 否 | "fail" | 如果"object"已有同名子对象时的操作。可选值: rename, replace, fail, merge |
| objects[...].listMode | string | 否 | "append" | 如果"object"的指定列表中已有对象时的操作。可选值: replaceAll, append |
| objects[...].name | string | 否 | - | "object"的新名称 |
| objects[...].notes | string | 否 | - | "object"的新注释 |
| objects[...].children | array | 否 | - | 要创建的子对象数组（可递归嵌套） |
| objects[...].children[...].type | string | 是 | - | 新对象的类型。参见《Wwise Objects Reference》 |
| objects[...].children[...].name | string | 是 | - | 新对象的名称 |
| objects[...].children[...].id | string | 否 | - | **仅限内部使用！** 为新创建的对象分配的ID (GUID) |
| objects[...].children[...].notes | string | 否 | - | 新对象的注释 |
| objects[...].children[...].classId | integer | 否 | - | 插件ID。仅对Effect或Source插件指定。范围: [0, 4294967295] |
| objects[...].children[...].language | string | 否 | - | 语言的ID (GUID) 或名称。仅在创建Sound Voice对象时使用 |
| objects[...].children[...].children | (recursive) | 否 | - | 递归创建子对象 |
| objects[...].children[...].import | object | 否 | - | 导入命令参数 |
| objects[...].children[...].import.autoAddToSourceControl | boolean | 否 | true | 是否自动执行source control的Add操作 |
| objects[...].children[...].import.files | array | 是 | - | 导入文件数组 |
| objects[...].children[...].import.files[...].audioFile | string | 否 | - | 要导入的媒体文件路径 |
| objects[...].children[...].import.files[...].audioFileBase64 | string | 否 | - | Base64编码的WAV音频文件数据，格式: '文件名.wav\|Base64数据' |
| objects[...].children[...].import.files[...].originalsSubFolder | string | 否 | - | Originals文件夹下的子文件夹路径 |
| objects[...].children[...].import.files[...].language | string | 否 | - | 音频文件导入的语言 |
| objects[...].children[...].import.files[...].objectType | string | 否 | - | 导入音频文件时创建的对象类型 |
| objects[...].children[...].@<属性名> | any of | 否 | - | 通过 `@属性名` 语法设置对象属性值。支持: null, string, array, number, boolean |
| objects[...].children[...].@<列表名> | array | 否 | - | 通过 `@列表名` 语法在列表中创建对象。参见《Wwise Objects Reference》获取各对象类型的可能列表名 |
| objects[...].@<属性名> | any of | 否 | - | 通过 `@属性名` 语法设置对象属性或创建列表对象 |
| objects[...].@<属性名>.type | string | 是(如果创建对象) | - | 列表中新对象的类型 |
| objects[...].@<属性名>.points | array | 否 | - | 用于创建Curve时。曲线的点数组，每个点含x, y, shape |
| objects[...].import | object | 否 | - | 导入命令参数（与children中的import结构相同） |
| platform | any of | 否 | - | 全局平台设置（可被单个object覆盖）。不指定则为所有链接平台设置值 |
| onNameConflict | string | 否 | "fail" | 全局名称冲突处理（可被单个object覆盖）。可选值: rename, replace, fail, merge |
| listMode | string | 否 | "append" | 全局列表模式（可被单个object覆盖）。可选值: replaceAll, append |
| autoAddToSourceControl | boolean | 否 | true | 是否自动执行source control的Add操作 |

### Curve 点的 shape 可选值
Constant, Linear, Log3, Log2, Log1, InvertedSCurve, SCurve, Exp1, Exp2, Exp3

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| objects | array | 每个父对象的 {对象, 创建的对象} 关联数组 |
| objects[...].id | string | 父对象的ID (GUID) |
| objects[...].name | string | 父对象的名称 |
| objects[...].children | array | 创建的子对象数组，每个对象包含id, name, notes, type, pluginName, path, parent, owner, isPlayable, shortId, classId, category, filePath, workunit等属性 |
| objects[...].@<列表名> | array | 在指定列表中创建的对象数组 |

## JSON-RPC 请求示例

### 示例：创建子层级对象

```json
{
    "method": "ak.wwise.core.object.set",
    "params": {
        "objects": [
            {
                "object": "\\Actor-Mixer Hierarchy\\Default Work Unit",
                "children": [
                    {
                        "type": "RandomSequenceContainer",
                        "name": "My New Sound"
                    }
                ]
            }
        ]
    }
}
```

### JSON-RPC 响应示例

```json
{
    "objects": [
        {
            "id": "{24979032-B170-43E3-A2E4-469E0193E2C3}",
            "name": "Default Work Unit",
            "children": [
                {
                    "id": "{AABBCC00-1122-3344-5566-77889900AABB}",
                    "name": "My New Sound",
                    "type": "RandomSequenceContainer",
                    "path": "\\Actor-Mixer Hierarchy\\Default Work Unit\\My New Sound"
                }
            ]
        }
    ]
}
```

## 注意事项

- 这是一个功能强大的批量操作函数，可同时进行创建、设置属性、设置引用和导入音频文件
- `objects[...].id` 参数仅限内部使用，正常情况下不应手动指定
- `@属性名` 和 `@列表名` 是动态参数，具体可用名称取决于对象类型，参见《Wwise Objects Reference》
- Curve点的shape支持多种插值类型（Constant, Linear, Log, SCurve, Exp等）
- 使用 `onNameConflict: "merge"` 可以将属性合并到已有对象

## 相关函数

- ak.wwise.core.object.create
- ak.wwise.core.object.setName
- ak.wwise.core.object.setNotes
- ak.wwise.core.object.setProperty
- ak.wwise.core.object.setReference
- ak.wwise.core.audio.import

## 相关Topic

- ak.wwise.core.object.created
- ak.wwise.core.object.nameChanged
- ak.wwise.core.object.notesChanged
- ak.wwise.core.object.propertyChanged
- ak.wwise.core.object.referenceChanged

## 官方文档链接

- https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_set.html
