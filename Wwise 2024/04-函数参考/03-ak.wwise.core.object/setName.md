# ak.wwise.core.object.setName

> **命名空间**: ak.wwise.core.object

## 概述

重命名一个对象。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要重命名的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| value | string | 是 | - | 对象的新名称 |

## 返回值

（官网未提供 - 此函数通常不返回数据，成功执行即表示操作完成）

## JSON-RPC 请求示例

### 示例：重命名对象

```json
{
    "method": "ak.wwise.core.object.setName",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "value": "NewSoundName"
    }
}
```

## 注意事项

- 新名称在同一父对象下必须唯一，否则会失败
- 使用 ak.wwise.core.object.set 可以同时设置名称和其他属性

## 相关函数

- ak.wwise.core.object.setNotes
- ak.wwise.core.object.set
- ak.wwise.core.undo.beginGroup

## 相关Topic

- ak.wwise.core.object.nameChanged

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setName.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setname_example_renaming_a_wwiseobject.html
