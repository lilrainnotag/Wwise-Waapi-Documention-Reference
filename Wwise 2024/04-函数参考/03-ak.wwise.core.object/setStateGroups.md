# ak.wwise.core.object.setStateGroups

> **命名空间**: ak.wwise.core.object

## 概述

设置与对象关联的State Group对象。注意：此操作将移除之前关联的所有State Group。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要添加State Group的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| stateGroups | array | 是 | - | 要设置的State Group对象数组 |
| stateGroups [...] | any of | 是 | - | State Group对象的限定名(type:name格式)、GUID或项目路径 |

## 返回值

（官网未提供 - 成功执行即表示操作完成）

## JSON-RPC 请求示例

### 示例：向Sound添加State Group

```json
{
    "method": "ak.wwise.core.object.setStateGroups",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "stateGroups": [
            "{66666666-7777-8888-9999-AAAAAAAAAAAA}",
            "StateGroup:MyStateGroup"
        ]
    }
}
```

## 注意事项

- **此操作将移除之前关联的所有State Group**，然后用指定的列表替换
- 如果只想添加而不移除已有的，需要使用 ak.wwise.core.object.set
- 关联State Group后，可以通过 setStateProperties 设置状态属性

## 相关函数

- ak.wwise.core.object.setStateProperties
- ak.wwise.core.object.get
- ak.wwise.core.object.set

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setStateGroups.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setstategroups_example_adding_a_state_group_to_a_sound.html
