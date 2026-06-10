# ak.wwise.core.object.setLinked

> **命名空间**: ak.wwise.core.object

## 概述

将属性/引用或对象列表链接(link)或取消链接(unlink)到特定平台。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要设置值的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| property | string | 是 | - | 属性名称。参见《Wwise Objects Reference》获取Wwise对象属性列表 |
| platform | any of | 是 | - | 平台的ID (GUID) 或唯一名称 |
| linked | boolean | 是 | - | 是否链接。true表示链接到指定平台，false表示取消链接 |

## 返回值

（官网未提供 - 此函数通常不返回数据）

## JSON-RPC 请求示例

```json
{
    "method": "ak.wwise.core.object.setLinked",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "property": "Volume",
        "platform": "{66666666-7777-8888-9999-AAAAAAAAAAAA}",
        "linked": true
    }
}
```

## 注意事项

- 链接属性意味着该属性在所有平台间共享相同的值
- 取消链接(unlink)允许每个平台有不同的属性值
- 使用 isLinked 可以查询当前的链接状态

## 相关函数

- ak.wwise.core.object.isLinked

## 相关Topic

（官网未提供）

## 官方文档链接

- https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setLinked.html
