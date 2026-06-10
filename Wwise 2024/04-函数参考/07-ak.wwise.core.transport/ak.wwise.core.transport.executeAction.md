# ak.wwise.core.transport.executeAction

▎ **命名空间**: ak.wwise.core.transport

## 概述

Executes an action on the given transport object, or all transport objects if none is specified.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| transport | integer | 否 | 全部 transport 对象 | The transport object ID. Unsigned Integer 32-bit，范围: [0, 4294967295]。如果不指定，则对所有 transport 对象执行操作。 |
| action | string | 是 | — | The action to execute. 可选值：play（播放）、stop（停止）、pause（暂停）、playStop（切换 播放/停止）、playDirectly（直接播放）。 |

## 返回值

（官网未提供 — 操作成功时不返回特定数据）

## JSON-RPC 请求示例

### 播放指定 transport 对象

```json
{
    "transport": 1234,
    "action": "play"
}
```

### 停止所有 transport 对象

```json
{
    "action": "stop"
}
```

### 切换播放/暂停

```json
{
    "transport": 1234,
    "action": "pause"
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 如果不指定 `transport` 参数，操作将应用于**所有**现有的 transport 对象。
- `playStop` 操作会在播放和停止之间切换（toggle）。
- `pause` 操作在暂停和恢复之间切换（toggle）。
- `playDirectly` 用于直接播放，绕过某些播放前处理。

## 相关函数

- ak.wwise.core.transport.create
- ak.wwise.core.transport.getState

## 相关 Topic

- Wwise Transport 控制

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_transport_executeAction.html
