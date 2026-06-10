# ak.soundengine.setGameObjectAuxSendValues

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetGameObjectAuxSendValues`

## 概述

Sets the Auxiliary Busses to route the specified game object. See AK::SoundEngine::SetGameObjectAuxSendValues.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| gameObject | integer | 是 | （无） | Associated game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| auxSendValues | array of object | 是 | （无） | Array of AkAuxSendValue structures. |
| auxSendValues[...].listener | integer | 是 | （无） | Game object ID of the listener associated with this send. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| auxSendValues[...].auxBus | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name or Short ID of the auxiliary bus. string: The name of the object. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. integer: The Short ID of a Wwise Object. Unsigned Integer 32-bit. Range: [0,4294967295] |
| auxSendValues[...].controlValue | number | 是 | （无） | Value in the range [0.0f:1.0f], send level to auxiliary bus. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setGameObjectAuxSendValues",
  "params": {
    "gameObject": 1,
    "auxSendValues": [
      {
        "listener": 2,
        "auxBus": "{aabbcc00-1122-3344-5566-77889900aabb}",
        "controlValue": 0.5
      }
    ]
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `auxSendValues` 为 `AkAuxSendValue` 结构体数组
- `controlValue` 取值范围为 [0.0, 1.0]，表示发送到辅助总线的电平
- `listener` 必须是已注册的游戏对象 ID
- `auxBus` 支持三种形式：名称字符串、GUID字符串、Short ID整数

## 相关函数

- [ak.soundengine.setListeners](ak.soundengine.setListeners.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setGameObjectAuxSendValues.html
