# ak.soundengine.setObjectObstructionAndOcclusion

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetObjectObstructionAndOcclusion`

## 概述

Set a game object's obstruction and occlusion levels. This function is used to affect how an object should be heard by a specific listener. See AK::SoundEngine::SetObjectObstructionAndOcclusion.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| emitter | integer | 是 | （无） | Emitter game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| listener | integer | 是 | （无） | Listener game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| obstructionLevel | number | 是 | （无） | ObstructionLevel: [0.0f..1.0f] |
| occlusionLevel | number | 是 | （无） | OcclusionLevel: [0.0f..1.0f] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setObjectObstructionAndOcclusion",
  "params": {
    "emitter": 1,
    "listener": 2,
    "obstructionLevel": 0.5,
    "occlusionLevel": 0.8
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `obstructionLevel` 和 `occlusionLevel` 取值范围均为 [0.0, 1.0]
- Obstruction（阻碍）影响同一房间内的声音传播
- Occlusion（遮蔽）影响穿墙等不同房间之间的声音传播
- 所有参数均为必填

## 相关函数

- [ak.soundengine.setListeners](ak.soundengine.setListeners.md)
- [ak.soundengine.setPosition](ak.soundengine.setPosition.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setObjectObstructionAndOcclusion.html
