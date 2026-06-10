# ak.wwise.core.object.copy

> **命名空间**: ak.wwise.core.object

## 概述

将对象复制到指定的父对象下。注意：如果复制的是一个Work Unit，该操作不可撤销，并且项目将被保存。返回被复制的对象。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要复制的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| parent | any of | 是 | - | 新父对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| onNameConflict | string | 否 | "fail" | 如果"parent"已有同名子对象时的操作。可选值: rename, replace, fail |
| autoCheckOutToSourceControl | boolean | 否 | true | 是否自动对受影响的Work Unit和项目执行source control的Checkout操作 |
| autoAddToSourceControl | boolean | 否 | true | 是否自动对受影响的Work Unit执行source control的Add操作 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| id | string | 新复制对象的ID (GUID)。格式: {aabbcc00-1122-3344-5566-77889900aabb} |
| name | string | 新复制对象的名称 |
| notes | string | 新复制对象的注释 |
| type | string | 对象类型。参见《Wwise Objects Reference》 |
| pluginName | string | 插件名称（Source, Effect, Mixer, Device 和 Metadata 插件） |
| path | string | 从项目根目录的对象路径 |
| parent | object | 层次结构中的父对象（含id和name） |
| owner | object | 对象的拥有者（含id和name） |
| isPlayable | boolean | 对象是否可在Transport中播放 |
| shortId | integer | 对象的Short ID |
| classId | integer | 对象的class ID |
| category | string | 对象类别 |
| filePath | string | 包含该对象的文件路径 |
| workunit | object | 包含该对象的Work Unit（含id和name） |

## JSON-RPC 请求示例

### 示例：复制对象到指定父对象

```json
{
    "method": "ak.wwise.core.object.copy",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "parent": "\\Actor-Mixer Hierarchy\\Default Work Unit"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "id": "{66666666-7777-8888-9999-AAAAAAAAAAAA}",
    "name": "MySound",
    "type": "Sound",
    "path": "\\Actor-Mixer Hierarchy\\Default Work Unit\\MySound"
}
```

## 注意事项

- **复制Work Unit不可撤销**，操作后项目将自动保存
- `onNameConflict` 选项: "rename" 自动重命名, "replace" 替换已有对象, "fail" 操作失败
- 可以通过 `return` 参数（Options）指定返回哪些对象属性

## 相关函数

- ak.wwise.core.object.move
- ak.wwise.core.object.delete
- ak.wwise.core.object.create

## 相关Topic

- ak.wwise.core.object.created

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_copy.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_copy_example_copying_an_object_to_the_given_parent.html
