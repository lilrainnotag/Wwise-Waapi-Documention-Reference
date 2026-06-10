# ak.wwise.core.object.move

> **命名空间**: ak.wwise.core.object

## 概述

将对象移动到指定的父对象下。返回被移动的对象。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要移动的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| parent | any of | 是 | - | 新父对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| onNameConflict | string | 否 | "fail" | 如果"parent"已有同名子对象时的操作。可选值: rename, replace, fail |
| autoCheckOutToSourceControl | boolean | 否 | true | 是否自动对受影响的Work Unit和项目执行source control的Checkout操作 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| id | string | 被移动对象的ID (GUID)。格式: {aabbcc00-1122-3344-5566-77889900aabb} |
| name | string | 被移动对象的名称 |
| notes | string | 对象的注释 |
| type | string | 对象类型 |
| pluginName | string | 插件名称 |
| path | string | 从项目根目录的对象路径 |
| parent | object | 层次结构中的父对象（含id和name） |
| owner | object | 对象的拥有者（含id和name） |
| isPlayable | boolean | 对象是否可在Transport中播放 |
| shortId | integer | 对象的Short ID |
| classId | integer | 对象的class ID |
| category | string | 对象类别 |
| filePath | string | 包含该对象的文件路径 |
| workunit | object | 包含该对象的Work Unit（含id和name） |
| childrenCount | number | **已弃用**。子对象数量，建议使用 children.count() |
| totalSize | integer | 对象及其所有子对象在SoundBank中占用的空间（字节） |
| mediaSize | integer | 对象及其所有子对象的媒体文件总转换大小（字节） |
| objectSize | integer | 对象元数据在SoundBank中占用的空间（字节） |
| structureSize | integer | 对象及其所有子对象的元数据在SoundBank中占用的空间（字节） |

## JSON-RPC 请求示例

### 示例：移动对象到新父对象

```json
{
    "method": "ak.wwise.core.object.move",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "parent": "\\Actor-Mixer Hierarchy\\Another Work Unit"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "id": "{AABBCC00-1122-3344-5566-77889900AABB}",
    "name": "MySound",
    "type": "Sound",
    "path": "\\Actor-Mixer Hierarchy\\Another Work Unit\\MySound"
}
```

## 注意事项

- 移动操作不创建副本，只是改变对象在层级结构中的位置
- `onNameConflict` 选项: "rename" 自动重命名, "replace" 替换已有对象, "fail" 操作失败

## 相关函数

- ak.wwise.core.object.copy
- ak.wwise.core.object.delete
- ak.wwise.core.object.create

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_move.html
- 示例-移动到新父对象: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_move_example_moving_an_object_to_a_new_parent.html
