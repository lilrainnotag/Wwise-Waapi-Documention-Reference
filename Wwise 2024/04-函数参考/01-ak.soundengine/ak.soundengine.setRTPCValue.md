# ak.soundengine.setRTPCValue

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetRTPCValue`

## 概述

Sets the value of a real-time parameter control. See AK::SoundEngine::SetRTPCValue.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| rtpc | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or Short ID of the real-time parameter control. string: The name of the object. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. integer: The Short ID of a Wwise Object. Unsigned Integer 32-bit. Range: [0,4294967295] |
| value | number | 是 | （无） | Value to set. |
| gameObject | integer | 否 | transport game object | Associated game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setRTPCValue",
  "params": {
    "rtpc": "MyRTPC",
    "value": 0.75,
    "gameObject": 1
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `rtpc` 参数为必填，支持三种形式：名称字符串、GUID字符串、Short ID整数
- `gameObject` 参数可选，默认使用 transport game object
- 设置的值会实时影响与该 RTPC 关联的所有声音属性

## 相关函数

- [ak.soundengine.resetRTPCValue](ak.soundengine.resetRTPCValue.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setRTPCValue.html
