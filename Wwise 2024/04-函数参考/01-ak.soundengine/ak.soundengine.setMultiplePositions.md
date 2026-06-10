# ak.soundengine.setMultiplePositions

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetMultiplePositions`

## 概述

Sets multiple positions for a single game object. Setting multiple positions for a single game object is a way to simulate multiple emission sources while using the resources of only one voice. This can be used to simulate wall openings, area sounds, or multiple objects emitting the same sound in the same area. See AK::SoundEngine::SetMultiplePositions.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| gameObject | integer | 是 | （无） | Game Object identifier. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| positions | array of object | 是 | （无） | Array of positions to apply. |
| positions[...].position.position.x | number | 是 | （无） | X coordinate of the position. |
| positions[...].position.position.y | number | 是 | （无） | Y coordinate of the position. |
| positions[...].position.position.z | number | 是 | （无） | Z coordinate of the position. |
| positions[...].position.orientationFront.x | number | 是 | （无） | X component of the front orientation. |
| positions[...].position.orientationFront.y | number | 是 | （无） | Y component of the front orientation. |
| positions[...].position.orientationFront.z | number | 是 | （无） | Z component of the front orientation. |
| positions[...].position.orientationTop.x | number | 是 | （无） | X component of the top orientation. |
| positions[...].position.orientationTop.y | number | 是 | （无） | Y component of the top orientation. |
| positions[...].position.orientationTop.z | number | 是 | （无） | Z component of the top orientation. |
| multiPositionType | integer | 是 | （无） | Uses values from AK::SoundEngine::MultiPositionType. Range: [0,2] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setMultiplePositions",
  "params": {
    "gameObject": 1,
    "positions": [
      {
        "position": {
          "position": {"x": 0, "y": 0, "z": 0},
          "orientationFront": {"x": 1, "y": 0, "z": 0},
          "orientationTop": {"x": 0, "y": 1, "z": 0}
        }
      }
    ],
    "multiPositionType": 0
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 设置多个位置可以在只使用一个声音资源的情况下模拟多个发射源
- 适用于模拟墙面开口、区域音效或多个物体发出相同声音的场景
- `multiPositionType` 取值来自 `AK::SoundEngine::MultiPositionType`，范围 [0,2]
- 每个位置包含 position（坐标）、orientationFront（前向）和 orientationTop（上向）三个向量

## 相关函数

- [ak.soundengine.setPosition](ak.soundengine.setPosition.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setMultiplePositions.html
