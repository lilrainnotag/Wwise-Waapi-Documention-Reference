# ak.wwise.core.transport.getState

▎ **命名空间**: ak.wwise.core.transport

## 概述

Gets the state of the given transport object.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| transport | integer | 是 | — | The transport object ID. Unsigned Integer 32-bit，范围: [0, 4294967295]。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| state | string (必填) | The state of the transport object. 可选值：playing（播放中）、stopped（已停止）、paused（已暂停）。 |

## JSON-RPC 请求示例

```json
{
    "transport": 1234
}
```

## JSON-RPC 响应示例

```json
{
    "state": "playing"
}
```

## 注意事项

- 返回的状态值只有三种：`playing`、`stopped`、`paused`。

## 相关函数

- ak.wwise.core.transport.create
- ak.wwise.core.transport.executeAction

## 相关 Topic

- Wwise Transport 控制

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_transport_getState.html
