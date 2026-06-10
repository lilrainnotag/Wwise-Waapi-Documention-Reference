# ak.soundengine.setPosition

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetPosition`

## 概述

Sets the position of a game object. See AK::SoundEngine::SetPosition.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| gameObject | integer | 是 | （无） | Game Object identifier. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| position | object | 是 | （无） | The 3D position to set for the game object. |
| position.position.x | number | 是 | （无） | X coordinate. |
| position.position.y | number | 是 | （无） | Y coordinate. |
| position.position.z | number | 是 | （无） | Z coordinate. |
| position.orientationFront.x | number | 是 | （无） | X component of the front orientation. |
| position.orientationFront.y | number | 是 | （无） | Y component of the front orientation. |
| position.orientationFront.z | number | 是 | （无） | Z component of the front orientation. |
| position.orientationTop.x | number | 是 | （无） | X component of the top orientation. |
| position.orientationTop.y | number | 是 | （无） | Y component of the top orientation. |
| position.orientationTop.z | number | 是 | （无） | Z component of the top orientation. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setPosition",
  "params": {
    "gameObject": 1,
    "position": {
      "position": {"x": 10.0, "y": 0.0, "z": 5.0},
      "orientationFront": {"x": 1.0, "y": 0.0, "z": 0.0},
      "orientationTop": {"x": 0.0, "y": 1.0, "z": 0.0}
    }
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 位置包含坐标（position）、前向（orientationFront）和上向（orientationTop）三个向量
- 游戏对象必须先通过 `registerGameObj` 注册
- 如需设置多位置，请使用 `setMultiplePositions`

## 相关函数

- [ak.soundengine.setMultiplePositions](ak.soundengine.setMultiplePositions.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setPosition.html
