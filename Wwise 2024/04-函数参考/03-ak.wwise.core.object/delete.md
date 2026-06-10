# ak.wwise.core.object.delete

> **命名空间**: ak.wwise.core.object

## 概述

删除指定的对象。注意：如果删除的是一个Work Unit，该操作不可撤销，并且项目将被保存。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要删除的对象的ID (GUID)、名称或路径。支持格式: type:name（如 Event:Play_Sound_01）、GUID（如 {aabbcc00-1122-3344-5566-77889900aabb}）、项目路径（如 \Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX） |
| autoCheckOutToSourceControl | boolean | 否 | true | 是否自动对受影响的Work Unit和项目执行source control的Checkout操作 |

## 返回值

（官网未提供 - 此函数通常不返回数据）

## JSON-RPC 请求示例

### 示例：通过GUID删除对象

```json
{
    "method": "ak.wwise.core.object.delete",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}"
    }
}
```

### 示例：通过路径删除对象

```json
{
    "method": "ak.wwise.core.object.delete",
    "params": {
        "object": "\\Actor-Mixer Hierarchy\\Default Work Unit\\MySound"
    }
}
```

## 注意事项

- **删除Work Unit不可撤销**，操作后项目将自动保存
- 如果启用了source control，默认会自动check out受影响的文件
- 可以通过 `autoCheckOutToSourceControl: false` 禁用自动check out

## 相关函数

- ak.wwise.core.object.copy
- ak.wwise.core.object.move
- ak.wwise.core.object.create

## 相关Topic

- ak.wwise.core.object.preDeleted
- ak.wwise.core.object.postDeleted

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_delete.html
- 示例-通过GUID删除: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_delete_example_deleting_an_object_by_guid.html
- 示例-通过路径删除: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_delete_example_deleting_an_object_by_path.html
