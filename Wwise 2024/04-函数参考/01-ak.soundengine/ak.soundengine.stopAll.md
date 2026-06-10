# ak.soundengine.stopAll

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::StopAll`

## 概述

Stop playing the current content associated to the specified game object ID. If no game object is specified, all sounds are stopped. See AK::SoundEngine::StopAll.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| gameObject | integer | 是 | （官网未提供） | Specify a game object to stop only playback associated to the provided game object ID. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.stopAll",
  "params": {
    "gameObject": 1
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 指定 `gameObject` 时只停止与该游戏对象关联的播放
- 根据官网描述，如果不指定 game object，则停止所有声音（但参数列表中 `gameObject` 标记为必填，请以实际测试为准）
- 如需停止特定 Event 的特定播放实例，请使用 `stopPlayingID`

## 相关函数

- [ak.soundengine.stopPlayingID](ak.soundengine.stopPlayingID.md)
- [ak.soundengine.postEvent](ak.soundengine.postEvent.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_stopAll.html
