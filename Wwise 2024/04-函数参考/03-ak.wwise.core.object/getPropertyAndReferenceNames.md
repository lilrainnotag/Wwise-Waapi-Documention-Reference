# ak.wwise.core.object.getPropertyAndReferenceNames

> **命名空间**: ak.wwise.core.object

## 概述

检索对象的属性和引用名称列表。此函数替代了已弃用的 ak.wwise.core.object.getPropertyNames。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 否 | - | 要查询的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| classId | integer | 否 | - | 要检索属性和引用名称的对象的class ID。范围: [0, 4294967295] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | 指定对象的所有属性和引用名称的数组 |
| return [...] | string | 属性或引用的名称 |

## JSON-RPC 请求示例

### 示例：检索对象的属性和引用名称列表

```json
{
    "method": "ak.wwise.core.object.getPropertyAndReferenceNames",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "return": [
        "Volume",
        "Pitch",
        "Lowpass",
        "Highpass",
        "OutputBus",
        "OutputBusVolume",
        "MakeUpGain"
    ]
}
```

## 注意事项

- 此函数替代了已弃用的 ak.wwise.core.object.getPropertyNames
- `classId` 和 `object` 可以二选一使用
- 返回的名称列表包含属性名称和引用名称，不区分二者

## 相关函数

- ak.wwise.core.object.getPropertyNames（已弃用，由此函数替代）
- ak.wwise.core.object.getPropertyInfo
- ak.wwise.core.object.getTypes

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_getPropertyAndReferenceNames.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_getpropertyandreferencenames_example_retrieving_the_list_of_property_and_reference_names_of_an_object.html
