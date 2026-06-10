# ak.wwise.core.object.setStateProperties

> **命名空间**: ak.wwise.core.object

## 概述

设置对象的状态属性(State Properties)。注意：此操作将移除之前设置的所有状态属性，包括默认的状态属性。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要设置状态属性的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| stateProperties | array | 是 | - | 要设置的状态属性名称数组 |
| stateProperties [...] | string | 是 | - | 属性名称。参见《Wwise Objects Reference》 |

## 返回值

（官网未提供 - 成功执行即表示操作完成）

## JSON-RPC 请求示例

### 示例：为Sound设置状态属性

```json
{
    "method": "ak.wwise.core.object.setStateProperties",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "stateProperties": [
            "Volume",
            "Pitch",
            "Lowpass"
        ]
    }
}
```

## 注意事项

- **此操作将移除之前设置的所有状态属性**（包括默认的状态属性），用指定的列表替换
- 必须先使用 setStateGroups 关联 State Group，然后才能设置状态属性
- 如果只想修改而不完全替换，需要使用 ak.wwise.core.object.set

## 相关函数

- ak.wwise.core.object.get
- ak.wwise.core.object.setStateGroups

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setStateProperties.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setstateproperties_example_set_state_properties_to_a_sound.html
