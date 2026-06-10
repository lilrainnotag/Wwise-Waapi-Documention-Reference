# ak.wwise.core.object.pasteProperties

> **命名空间**: ak.wwise.core.object

## 概述

将属性、引用和列表从源对象粘贴到任意数量的目标对象上。只有源对象和目标对象之间存在差异的属性、引用和列表才会被粘贴。关于每个对象类型上可用的属性、引用和列表，参见《Wwise Objects Reference》。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| source | any of | 是 | - | 源对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| targets | array | 是 | - | 要粘贴到的目标对象数组。每个元素为ID (GUID)、名称或路径 |
| targets [...] | any of | 是 | - | 目标对象的ID (GUID)、名称或路径 |
| pasteMode | string | 否 | "replaceEntire" | 列表的粘贴模式。可选值: replaceEntire（替换全部——删除目标对象列表中的所有元素，从源列表复制所选元素）, addReplace（添加替换——保留目标中不在源中的元素，添加源中有但目标没有的元素，共有元素用源的替换）, addKeep（添加保留——保留目标中不在源中的元素，添加源中有但目标没有的元素，共有元素保留目标的） |
| inclusion | array | 否 | 全部包含 | 要包含在粘贴操作中的属性、引用和列表名称数组。不指定时包含所有 |
| inclusion [...] | string | 否 | - | 属性、引用或列表名称 |
| exclusion | array | 否 | 无排除 | 要从粘贴操作中排除的属性、引用和列表名称数组。不指定时不排除任何 |
| exclusion [...] | string | 否 | - | 属性、引用或列表名称 |

## 返回值

（官网未提供 - 此函数通常不返回数据）

## JSON-RPC 请求示例

### 示例：使用默认模式粘贴

```json
{
    "method": "ak.wwise.core.object.pasteProperties",
    "params": {
        "source": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "targets": [
            "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
        ]
    }
}
```

### 示例：使用包含列表粘贴

```json
{
    "method": "ak.wwise.core.object.pasteProperties",
    "params": {
        "source": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "targets": [
            "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
        ],
        "inclusion": [
            "Volume",
            "OutputBus"
        ]
    }
}
```

## 注意事项

- 只会粘贴 source 和 target 之间有差异的属性/引用/列表，相同的部分不会重复粘贴
- `pasteMode` 的三个选项影响列表粘贴行为：replaceEntire, addReplace, addKeep
- `inclusion` 和 `exclusion` 可以精确控制粘贴范围
- 此函数常用于配合 `diff` 使用：先diff找出差异，再用pasteProperties按需粘贴

## 相关函数

- ak.wwise.core.object.diff

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_pasteProperties.html
- 示例-默认粘贴: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_pasteproperties_example_pasting_with_defaults.html
