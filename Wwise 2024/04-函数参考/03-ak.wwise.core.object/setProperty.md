# ak.wwise.core.object.setProperty

> **命名空间**: ak.wwise.core.object

## 概述

为特定平台设置对象的属性值。关于每个对象类型上可用的属性，参见《Wwise Objects Reference》。要设置对象的引用，参见 ak.wwise.core.object.setReference。要获取对象的属性值，参见 ak.wwise.core.object.get。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要设置值的对象的ID (GUID)、名称或路径。支持格式: type:name（如 Event:Play_Sound_01）、GUID（如 {aabbcc00-1122-3344-5566-77889900aabb}）、项目路径（如 \Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX） |
| property | string | 是 | - | 属性名称。参见《Wwise Objects Reference》获取每个Wwise对象的属性列表 |
| value | any of | 是 | - | 属性的值。支持类型: null（空值）、string（字符串值）、number（数值）、boolean（布尔值） |
| platform | any of | 否 | 当前平台 | 平台的ID (GUID) 或唯一名称。用于设置非链接属性的值。不指定时使用当前平台 |

## 返回值

（官网未提供 - 此函数通常不返回数据，成功执行即表示操作完成）

## JSON-RPC 请求示例

### 示例：设置音量

```json
{
    "method": "ak.wwise.core.object.setProperty",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "property": "Volume",
        "value": 2.5
    }
}
```

### 示例：在指定平台上设置属性

```json
{
    "method": "ak.wwise.core.object.setProperty",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "property": "Volume",
        "value": 2.5,
        "platform": "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
    }
}
```

## 注意事项

- `value` 的类型取决于所设置的属性，可以传递 null、string、number 或 boolean
- 如果不指定 `platform`，则使用当前活动平台
- 对于链接(linked)属性，设置值会影响所有链接的平台

## 相关函数

- ak.wwise.core.object.get
- ak.wwise.core.object.setReference
- ak.wwise.core.object.set
- ak.wwise.core.undo.beginGroup

## 相关Topic

- ak.wwise.core.object.propertyChanged

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setProperty.html
- 示例-设置音量: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setproperty_example_setting_the_volume.html
- 示例-在指定平台设置属性: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setproperty_example_setting_the_value_of_a_specified_property_on_the_specified_platform.html
