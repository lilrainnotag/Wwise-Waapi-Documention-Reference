# ak.soundengine.setGameObjectOutputBusVolume

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetGameObjectOutputBusVolume`

## 概述

Set the output bus volume (direct) to be used for the specified game object. See AK::SoundEngine::SetGameObjectOutputBusVolume.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| emitter | integer | 是 | （无） | Associated emitter game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| listener | integer | 是 | （无） | Associated listener game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| controlValue | number | 是 | （无） | A multiplier where 0 means silence and 1 means no change. Therefore, values between 0 and 1 attenuate the sound, and values greater than 1 amplify it. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setGameObjectOutputBusVolume",
  "params": {
    "emitter": 1,
    "listener": 2,
    "controlValue": 0.5
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `controlValue` 为音量乘数：0 表示静音，1 表示无变化，0~1 之间衰减，大于 1 则放大
- `emitter` 和 `listener` 都必须是已注册的游戏对象 ID

## 相关函数

- [ak.soundengine.setListeners](ak.soundengine.setListeners.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setGameObjectOutputBusVolume.html
