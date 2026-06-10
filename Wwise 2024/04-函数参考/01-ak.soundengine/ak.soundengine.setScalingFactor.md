# ak.soundengine.setScalingFactor

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetScalingFactor`

## 概述

Sets the scaling factor of a game object. You can modify the attenuation computations on this game object to simulate sounds with a larger or smaller affected areas. See AK::SoundEngine::SetScalingFactor.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| gameObject | integer | 是 | （无） | The game object identifier. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| attenuationScalingFactor | number | 是 | （无） | The scaling factor, where 1 means 100%, 0.5 means 50%, 2 means 200%, and so on. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setScalingFactor",
  "params": {
    "gameObject": 1,
    "attenuationScalingFactor": 0.5
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 缩放因子影响衰减计算：1 = 100%（正常），0.5 = 50%（缩小影响范围），2 = 200%（扩大影响范围）
- 可用于模拟声音在大范围或小范围区域的传播效果

## 相关函数

- [ak.soundengine.setPosition](ak.soundengine.setPosition.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setScalingFactor.html
