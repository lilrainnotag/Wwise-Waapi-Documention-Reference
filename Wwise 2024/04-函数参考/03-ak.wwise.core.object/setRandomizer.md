# ak.wwise.core.object.setRandomizer

> **命名空间**: ak.wwise.core.object

## 概述

为特定平台设置对象属性的随机化器(Randomizer)值。关于每个对象类型上可用的属性，参见《Wwise Objects Reference》。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 否 | - | 拥有该属性的对象的ID (GUID)、名称或路径 |
| property | string | 否 | - | 属性名称。参见《Wwise Objects Reference》 |
| platform | any of | 否 | - | 平台的ID (GUID) 或唯一名称 |
| enabled | boolean | 否 | - | 随机化器的启用状态 |
| min | number | 否 | - | 随机化器可以偏移的最小值。范围: [*, 0] |
| max | number | 否 | - | 随机化器可以偏移的最大值。范围: [0, *] |

## 返回值

（官网未提供 - 成功执行即表示操作完成）

## JSON-RPC 请求示例

### 示例：设置Sound对象的Volume随机化器值

```json
{
    "method": "ak.wwise.core.object.setRandomizer",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "property": "Volume",
        "enabled": true,
        "min": -5.0,
        "max": 5.0
    }
}
```

## 注意事项

- `min` 必须 ≤ 0，`max` 必须 ≥ 0
- 随机化器为启用时，每次播放该对象时会在 [min, max] 范围内随机偏移属性值
- 支持随机化器的属性可以通过 getPropertyInfo 查询（supports.randomizer）

## 相关函数

- ak.wwise.core.object.getPropertyInfo
- ak.wwise.core.object.setProperty

## 相关Topic

- ak.wwise.core.object.propertyChanged

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setRandomizer.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setrandomizer_example_setting_the_volume_randomizer_values_of_a_sound_object.html
