# ak.wwise.core.object.getTypes

> **命名空间**: ak.wwise.core.object

## 概述

检索在 Wwise 对象模型中注册的所有对象类型列表。此函数返回的效果等同于《Wwise Objects Reference》。

## 参数

（官网未提供 — 此函数不接受任何参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | 所有Wwise对象类型的数组 |
| return[...].classId | integer | 对象的class ID。范围: [0, 4294967295] |
| return[...].name | string | 对象的名称 |
| return[...].type | string | 对象的类型。参见《Wwise Objects Reference》 |

## JSON-RPC 请求示例

### 示例：获取所有对象类型列表

```json
{
    "method": "ak.wwise.core.object.getTypes",
    "params": {}
}
```

### JSON-RPC 响应示例

```json
{
    "return": [
        {
            "classId": 0,
            "name": "Sound",
            "type": "Sound"
        },
        {
            "classId": 1,
            "name": "RandomSequenceContainer",
            "type": "RandomSequenceContainer"
        }
    ]
}
```

## 注意事项

- 此函数不接受任何参数
- 返回的 classId 可用于其他函数（如 getPropertyInfo, getPropertyAndReferenceNames）的 classId 参数

## 相关函数

- ak.wwise.core.object.getPropertyInfo
- ak.wwise.core.object.getPropertyAndReferenceNames

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_getTypes.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_gettypes_example_getting_the_list_of_all_object_types.html
