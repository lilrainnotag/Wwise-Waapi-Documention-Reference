# ak.wwise.core.object.create

> **命名空间**: ak.wwise.core.object

## 概述

创建指定类型（'type'）的对象，作为'parent'的子对象。关于创建对象的更多信息，参见《Importing Audio Files and Creating Structures》。另请参见 ak.wwise.core.audio.import 以导入音频文件到 Wwise。要创建 Effect 或 Source 插件，请使用 ak.wwise.core.object.set，并参考《Wwise Objects Reference》获取 classId。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| parent | any of | 是 | - | 新对象父对象的ID (GUID)、名称或路径。支持格式: type:name（如 Event:Play_Sound_01）、GUID、项目路径（如 \Actor-Mixer Hierarchy\Default Work Unit\） |
| type | string | 是 | - | 新对象的类型。参见《Wwise Objects Reference》获取可能的对象类型 |
| name | string | 是 | - | 新对象的名称 |
| list | string | 否 | - | 要插入对象的列表名称。如果设置此参数，对象将被插入到父对象拥有的列表中，而不是作为子对象 |
| onNameConflict | string | 否 | "fail" | 如果"parent"已有同名子对象时的操作。可选值: rename, replace, fail, merge |
| platform | any of | 否 | 所有平台 | 设置属性时使用的平台ID (GUID) 或名称。不指定则为所有链接平台设置值 |
| autoAddToSourceControl | boolean | 否 | true | 是否自动对受影响的Work Unit执行source control的Add操作 |
| id | string | 否 | - | **仅限内部使用！** 为新创建对象分配的ID (GUID)。格式: {aabbcc00-1122-3344-5566-77889900aabb} |
| notes | string | 否 | - | 新对象的注释 |
| children | array | 否 | - | 要递归创建的子对象数组。每个子对象需指定 type 和 name，可选 id, notes, children 和 @属性名 |
| @<属性名> | any of | 否 | - | 通过 `@属性名` 语法设置对象属性值。支持: null, string, number, boolean |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| id | string | 新创建对象的ID (GUID)。格式: {aabbcc00-1122-3344-5566-77889900aabb} |
| name | string | 新创建对象的名称 |
| children | array | 创建的子对象数组，每个子对象包含 id 和 name，可递归包含 children |

## JSON-RPC 请求示例

### 示例：创建一个 Sound 对象

```json
{
    "method": "ak.wwise.core.object.create",
    "params": {
        "parent": "{7A12D08F-B0D9-4403-9EFA-2E6338C197C1}",
        "type": "Sound",
        "name": "Boom"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "id": "{66666666-7777-8888-9999-AAAAAAAAAAAA}",
    "name": "Boom"
}
```

## 注意事项

- `id` 参数仅限内部使用，正常情况下不应手动指定
- 要创建 Effect 或 Source 插件，应使用 `ak.wwise.core.object.set` 而非此函数
- `onNameConflict: "merge"` 可以将属性合并到已有对象
- `children` 支持递归嵌套，可一次性创建整个层级结构

## 相关函数

- ak.wwise.core.object.set
- ak.wwise.core.audio.import
- ak.wwise.core.undo.beginGroup

## 相关Topic

- ak.wwise.core.object.created

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_create.html
- 示例-创建Sound: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_create_example_creating_a_sound_object.html
