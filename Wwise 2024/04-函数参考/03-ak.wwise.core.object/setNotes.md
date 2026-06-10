# ak.wwise.core.object.setNotes

> **命名空间**: ak.wwise.core.object

## 概述

设置对象的注释(notes)。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 要设置注释的对象的ID (GUID)、名称或路径。支持格式: type:name、GUID、项目路径 |
| value | string | 是 | - | 对象的新注释内容 |

## 返回值

（官网未提供 - 此函数通常不返回数据）

## JSON-RPC 请求示例

### 示例：设置对象注释

```json
{
    "method": "ak.wwise.core.object.setNotes",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "value": "This is a note for the sound object."
    }
}
```

## 注意事项

- 注释内容为纯文本字符串
- 使用 ak.wwise.core.object.set 可以同时设置注释和其他属性

## 相关函数

- ak.wwise.core.object.setName
- ak.wwise.core.object.set
- ak.wwise.core.object.get （通过return "notes"获取注释）

## 相关Topic

- ak.wwise.core.object.notesChanged

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setNotes.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setnotes_example_setting_the_notes_of_an_object.html
