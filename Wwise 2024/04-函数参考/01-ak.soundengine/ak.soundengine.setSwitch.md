# ak.soundengine.setSwitch

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetSwitch`

## 概述

Sets the State of a Switch Group. See AK::SoundEngine::SetSwitch.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| switchGroup | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or short ID of the Switch Group. |
| switchState | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or Short ID of the Switch State. |
| gameObject | integer | 否 | transport game object | Associated game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setSwitch",
  "params": {
    "switchGroup": "MySwitchGroup",
    "switchState": "MySwitchState",
    "gameObject": 1
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `switchGroup` 和 `switchState` 均支持三种形式：名称字符串、GUID字符串、Short ID整数
- `gameObject` 参数可选，默认使用 transport game object
- Switch 用于控制 Switch Container 中播放哪个子对象

## 相关函数

- [ak.soundengine.setState](ak.soundengine.setState.md)
- [ak.soundengine.getSwitch](ak.soundengine.getSwitch.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setSwitch.html
