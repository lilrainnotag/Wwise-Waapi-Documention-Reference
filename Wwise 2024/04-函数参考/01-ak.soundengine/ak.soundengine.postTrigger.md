# ak.soundengine.postTrigger

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::PostTrigger`

## 概述

Posts the specified Trigger. See AK::SoundEngine::PostTrigger.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| trigger | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or Short ID of the Trigger. string: The name of the object. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. integer: The Short ID of a Wwise Object. Unsigned Integer 32-bit. Range: [0,4294967295] |
| gameObject | integer | 否 | transport game object | Associated game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.postTrigger",
  "params": {
    "trigger": "MyTrigger",
    "gameObject": 1
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `trigger` 参数为必填，支持三种形式：名称字符串、GUID字符串、Short ID整数
- `gameObject` 参数可选，默认使用 transport game object
- Trigger 用于触发 Stinger 等交互式音乐元素

## 相关函数

- [ak.soundengine.postEvent](ak.soundengine.postEvent.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_postTrigger.html
