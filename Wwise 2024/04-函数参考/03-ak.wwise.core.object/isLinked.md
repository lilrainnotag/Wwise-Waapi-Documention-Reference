# ak.wwise.core.object.isLinked

> **命名空间**: ak.wwise.core.object

## 概述

指示属性、引用或对象列表是否绑定到特定平台还是所有平台。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要查询属性的链接/取消链接状态的对象ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| property | string | 是 | - | 属性名称。参见《Wwise Objects Reference》获取Wwise对象属性列表 |
| platform | any of | 是 | - | 平台的ID (GUID) 或唯一名称 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| linked | boolean | 指示指定属性在指定平台上是否已链接 |

## JSON-RPC 请求示例

```json
{
    "method": "ak.wwise.core.object.isLinked",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "property": "Volume",
        "platform": "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "linked": true
}
```

## 注意事项

- 当属性为linked时，该属性在所有平台间共享相同的值
- 当属性为unlinked时，每个平台可以有不同的值

## 相关函数

- ak.wwise.core.object.setLinked

## 相关Topic

（官网未提供）

## 官方文档链接

- https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_isLinked.html
