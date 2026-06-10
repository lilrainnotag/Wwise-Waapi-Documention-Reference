# ak.wwise.core.object.isPropertyEnabled

> **命名空间**: ak.wwise.core.object

## 概述

根据属性所依赖的其他属性的值，返回该属性是否已启用。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要检查的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| property | string | 是 | - | 属性名称。参见《Wwise Objects Reference》获取Wwise对象属性列表 |
| platform | any of | 是 | - | 平台的ID (GUID) 或唯一名称 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | boolean | 指示该属性是否已启用 |

## JSON-RPC 请求示例

### 示例：检查属性是否启用

```json
{
    "method": "ak.wwise.core.object.isPropertyEnabled",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "property": "EnableLFO",
        "platform": "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "return": true
}
```

## 注意事项

- 某些属性的启用状态取决于其他属性的值（例如，LFO相关属性可能依赖于EnableLFO属性的值）
- 此函数用于判断在当前对象的属性配置下，某个属性是否处于可用/启用状态
- 通过 getPropertyInfo 可以查看属性的依赖关系

## 相关函数

- ak.wwise.core.object.getPropertyInfo
- ak.wwise.core.object.get

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_isPropertyEnabled.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_ispropertyenabled_example_checking_if_a_property_is_enabled.html
