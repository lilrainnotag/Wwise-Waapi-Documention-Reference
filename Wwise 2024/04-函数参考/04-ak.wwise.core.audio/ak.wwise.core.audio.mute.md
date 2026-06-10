# ak.wwise.core.audio.mute

## ▎ 命名空间: ak.wwise.core.audio

## 概述

将对象静音（Mute）。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| objects * | array | 是 | — | 要静音的对象数组 |
| objects [...] | string (GUID/名称/路径) | 是 | — | 对象的 ID (GUID)、名称（`type:name` 或 `Global:shortId`）或项目路径 |
| value * | boolean | 是 | — | 对象是否静音 |

(* 必填)

## 返回值

（空对象 `{}`）

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audio.mute",
  "params": {
    "objects": [
      "\\Actor-Mixer Hierarchy\\Default Work Unit\\Hello"
    ],
    "value": true
  },
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {},
  "id": 1
}
```

## 注意事项

- `value` 为 `true` 时静音，`false` 时取消静音。
- 支持批量操作，一次可对多个对象设置静音状态。
- 静音操作会立即生效，影响当前 Wwise 项目中的音频播放。

## 相关函数

- [[ak.wwise.core.audio.solo]] — 独奏对象
- [[ak.wwise.core.audio.resetMute]] — 重置所有静音状态
- [[ak.wwise.core.audio.resetSolo]] — 重置所有独奏状态

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audio.mute](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_mute.html)
- [示例：静音 Wwise 对象](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_mute_example_mute_a_wwiseobject.html)
