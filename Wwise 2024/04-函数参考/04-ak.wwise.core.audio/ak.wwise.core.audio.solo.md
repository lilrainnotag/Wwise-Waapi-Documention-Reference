# ak.wwise.core.audio.solo

## ▎ 命名空间: ak.wwise.core.audio

## 概述

将对象设为独奏（Solo）。Solo 模式下只有被标记为 Solo 的对象会播放，其他对象将被静音。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| objects * | array | 是 | — | 要设置独奏的对象数组 |
| objects [...] | string (GUID/名称/路径) | 是 | — | 对象的 ID (GUID)、名称（`type:name` 或 `Global:shortId`）或项目路径 |
| value * | boolean | 是 | — | 对象是否独奏 |

(* 必填)

## 返回值

（空对象 `{}`）

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audio.solo",
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

- `value` 为 `true` 时独奏，`false` 时取消独奏。
- Solo 模式下，只有被设为 Solo 的对象会播放，其余对象被隐式静音。
- 支持批量操作。

## 相关函数

- [[ak.wwise.core.audio.mute]] — 静音对象
- [[ak.wwise.core.audio.resetSolo]] — 重置所有独奏状态
- [[ak.wwise.core.audio.resetMute]] — 重置所有静音状态

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audio.solo](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_solo.html)
