# ak.soundengine.setListenerSpatialization

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetListenerSpatialization`

## 概述

Sets a listener's spatialization parameters. This lets you define listener-specific volume offsets for each audio channel. See AK::SoundEngine::SetListenerSpatialization.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| listener | integer | 是 | （无） | Listener game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |
| spatialized | boolean | 是 | （无） | Spatialization toggle (true: enable spatialization, false: disable spatialization). |
| channelConfig | integer | 是 | （无） | Channel configuration associated with volumeOffsets. Use AK::AkChannelConfig::Serialize to serialize the value. Unsigned Integer 32-bit. Range: [0,4294967295] |
| volumeOffsets | array of number | 是 | （无） | Array of per-speaker volume offsets, in dB. See AkSpeakerVolumes.h for how to manipulate this array. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setListenerSpatialization",
  "params": {
    "listener": 1,
    "spatialized": true,
    "channelConfig": 65535,
    "volumeOffsets": [0.0, -3.0, -3.0, 0.0]
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `spatialized` 控制是否启用空间化处理
- `channelConfig` 使用 `AK::AkChannelConfig::Serialize()` 序列化声道配置值
- `volumeOffsets` 为每个声道的音量偏移（单位：dB），参考 `AkSpeakerVolumes.h`
- 所有参数均为必填

## 相关函数

- [ak.soundengine.setListeners](ak.soundengine.setListeners.md)
- [ak.soundengine.setPosition](ak.soundengine.setPosition.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setListenerSpatialization.html
