# ak.wwise.core.audio.resetMute

## ▎ 命名空间: ak.wwise.core.audio

## 概述

重置所有对象的静音（Mute）状态。调用后所有对象恢复到非静音状态。

## 参数

（无参数）

## 返回值

（空对象 `{}`）

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audio.resetMute",
  "params": {},
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

- 此函数会一次性重置所有对象的静音状态，无需逐个指定对象。
- 重置后所有对象恢复到非静音状态。

## 相关函数

- [[ak.wwise.core.audio.mute]] — 静音/取消静音指定对象
- [[ak.wwise.core.audio.solo]] — 独奏指定对象
- [[ak.wwise.core.audio.resetSolo]] — 重置所有独奏状态

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audio.resetMute](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_resetmute.html)
