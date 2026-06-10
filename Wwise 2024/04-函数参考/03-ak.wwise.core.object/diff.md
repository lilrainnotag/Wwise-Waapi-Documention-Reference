# ak.wwise.core.object.diff

> **命名空间**: ak.wwise.core.object

## 概述

比较源对象与目标对象的属性和列表差异。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| source | any of | 是 | - | 源对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| target | any of | 是 | - | 目标对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| properties | array | 有差异的属性和引用名称数组 |
| properties [...] | string | 属性或引用名称。参见《Wwise Objects Reference》 |
| lists | array | 有差异的列表名称数组 |
| lists [...] | string | 列表名称 |

## JSON-RPC 请求示例

### 示例：比较属性和列表差异

```json
{
    "method": "ak.wwise.core.object.diff",
    "params": {
        "source": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "target": "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "properties": [
        "Volume",
        "OutputBus",
        "MakeUpGain"
    ],
    "lists": [
        "RTPC",
        "State"
    ]
}
```

## 注意事项

- 返回的 `properties` 包含属性名称和引用名称
- 返回的 `lists` 包含列表名称
- 此函数通常与 `pasteProperties` 配合使用，先diff再按需粘贴

## 相关函数

- ak.wwise.core.object.pasteProperties

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_diff.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_diff_example_returning_the_property_and_list_differences.html
