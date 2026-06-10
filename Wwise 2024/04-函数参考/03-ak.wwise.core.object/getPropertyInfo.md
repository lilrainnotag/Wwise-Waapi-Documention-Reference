# ak.wwise.core.object.getPropertyInfo

> **命名空间**: ak.wwise.core.object

## 概述

检索对象属性的信息。注意：此函数不返回属性的值。要获取属性值，请参见 ak.wwise.core.object.get 和 Return Options。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 否 | - | 要查询属性的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| classId | integer | 否 | - | 要检索属性的对象的class ID。范围: [0, 4294967295] |
| property | string | 否 | - | 要检索的属性名称。参见《Wwise Objects Reference》 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| name | string | 属性的名称 |
| type | string | 属性的类型。参见《Wwise Objects Reference》 |
| audioEngineId | integer | 属性的音频引擎ID。范围: [0, 4294967295] |
| default | any of | 属性的默认值。支持类型: null, string, number, boolean |
| supports | object | 属性支持的功能 |
| supports.rtpc | string | 属性支持的RTPC模式。可选值: None, Additive, Exclusive, Multiplicative |
| supports.randomizer | boolean | 属性是否支持Randomizer |
| supports.unlink | boolean | 属性是否支持取消链接(unlink) |
| display | object | 属性的显示信息 |
| display.name | string | 属性的显示名称 |
| display.group | string | 属性的显示分组 |
| display.index | integer | 属性的显示索引 |
| dependencies | array | 属性对其他属性的依赖列表，包含依赖类型、条件、操作等 |

### 依赖类型 (dependencies[...].type)
- override, property, reference, objectType, isMasterBus

## JSON-RPC 请求示例

### 示例：检索对象属性信息

```json
{
    "method": "ak.wwise.core.object.getPropertyInfo",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "property": "Volume"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "name": "Volume",
    "type": "Real64",
    "audioEngineId": 0,
    "default": 0.0,
    "supports": {
        "rtpc": "Additive",
        "randomizer": true,
        "unlink": true
    },
    "display": {
        "name": "Volume",
        "group": "General",
        "index": 0
    }
}
```

## 注意事项

- 此函数返回属性的元信息（类型、默认值、支持的RTPC模式等），而非属性的当前值
- 要获取属性当前值请使用 ak.wwise.core.object.get
- `classId` 和 `object` 参数可以二选一使用：通过对象ID查询，或通过classId查询某类对象支持的属性

## 相关函数

- ak.wwise.core.object.get
- ak.wwise.core.object.getPropertyAndReferenceNames
- ak.wwise.core.object.getTypes

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_getPropertyInfo.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_getpropertyinfo_example_retrieving_information_about_an_object_property.html
