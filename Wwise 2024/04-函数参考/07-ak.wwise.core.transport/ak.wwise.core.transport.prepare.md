# ak.wwise.core.transport.prepare

▎ **命名空间**: ak.wwise.core.transport

## 概述

Prepare the object and its dependencies for playback. Use this function before calling PostEventSync or PostMIDIOnEventSync from IAkGlobalPluginContext.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | string (name/GUID/path) | 是 | — | The ID (GUID), name, or path of the object to control via the transport object. 支持格式：type:name、Global:shortId、{GUID}、或工程路径。 |

## 返回值

（官网未提供 — 准备成功时不返回特定数据）

## JSON-RPC 请求示例

```json
{
    "object": "Event:Play_Music"
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 此函数用于在使用 `IAkGlobalPluginContext` 调用 `PostEventSync` 或 `PostMIDIOnEventSync` 之前，预先加载对象及其依赖项。
- 与 `ak.wwise.core.transport.create` 不同，prepare 不创建 transport 对象，而是直接为指定对象准备播放资源。

## 相关函数

- ak.wwise.core.transport.create
- ak.soundengine.postEvent

## 相关 Topic

- Wwise Transport 控制
- IAkGlobalPluginContext

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_transport_prepare.html
