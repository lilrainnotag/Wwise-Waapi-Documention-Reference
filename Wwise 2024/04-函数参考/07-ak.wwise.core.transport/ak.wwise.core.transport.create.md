# ak.wwise.core.transport.create

▎ **命名空间**: ak.wwise.core.transport

## 概述

Creates a transport object for the given Wwise object. The return transport object can be used to play, stop, pause and resume the Wwise object via the other transport functions.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | string (name/GUID/path) | 是 | — | The ID (GUID), name, or path of the object to control via the transport object. 支持格式：type:name（如 Event:Play_Sound_01）、Global:shortId、{GUID}、或工程路径。 |
| gameObject | integer | 否 | — | The game object to use for playback. Unsigned Integer 64-bit，范围: [0, 18446744073709551615]。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| transport | integer | Transport object ID to be used with all other ak.wwise.core.transport functions. Unsigned Integer 32-bit，范围: [0, 4294967295]。 |

## JSON-RPC 请求示例

```json
{
    "object": "{A076AA65-B71A-45BB-8841-5A20C52CE727}"
}
```

## JSON-RPC 响应示例

```json
{
    "transport": 1234
}
```

## 注意事项

- 返回的 `transport` 对象 ID 是后续所有 transport 操作（play、stop、pause、resume、destroy 等）所依赖的关键标识。
- 如果指定了 `gameObject` 参数，播放将使用该游戏对象 ID。
- 创建 transport 对象后，需要使用 `ak.wwise.core.transport.executeAction` 来执行播放操作。
- Transport 对象使用完毕后，应通过 `ak.wwise.core.transport.destroy` 销毁以释放资源。

## 相关函数

- ak.wwise.core.transport.destroy
- ak.wwise.core.transport.executeAction
- ak.wwise.core.transport.getList
- ak.wwise.core.transport.getState
- ak.wwise.core.transport.prepare

## 相关 Topic

- Wwise Transport 控制

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_transport_create.html
