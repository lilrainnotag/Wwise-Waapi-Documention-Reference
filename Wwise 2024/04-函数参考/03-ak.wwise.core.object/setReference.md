# ak.wwise.core.object.setReference

> **命名空间**: ak.wwise.core.object

## 概述

设置对象的引用值。关于每个对象类型上可用的引用，参见《Wwise Objects Reference》。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 拥有引用的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| reference | string | 是 | - | 要设置的引用名称。参见《Wwise Objects Reference》获取可用的引用信息 |
| value | any of | 是 | - | 要引用的对象的ID (GUID)、名称、路径或定义。支持格式: type:name、GUID、项目路径 |
| platform | any of | 否 | - | 链接引用的平台ID (GUID) 或名称。设为null-guid可取消链接引用 |

## 返回值

（官网未提供 - 此函数通常不返回数据）

## JSON-RPC 请求示例

### 示例：设置对象引用

```json
{
    "method": "ak.wwise.core.object.setReference",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "reference": "OutputBus",
        "value": "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
    }
}
```

## 注意事项

- 引用名称因对象类型而异，需查阅《Wwise Objects Reference》
- `platform` 参数设为 null-guid 可以取消特定平台的链接引用
- 对于不区分平台的对象，不需要指定 `platform`

## 相关函数

- ak.wwise.core.object.setProperty
- ak.wwise.core.object.set
- ak.wwise.core.undo.beginGroup

## 相关Topic

- ak.wwise.core.object.referenceChanged

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setReference.html
- 示例-设置对象引用: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setreference_example_setting_an_object_reference.html
