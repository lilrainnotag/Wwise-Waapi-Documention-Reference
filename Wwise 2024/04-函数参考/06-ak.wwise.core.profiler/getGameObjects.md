# ak.wwise.core.profiler.getGameObjects

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the game objects at a specific profiler capture time.

在指定的 Profiler 捕获时间点获取 Game Object 信息。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | The time in milliseconds to query for game objects. 查询 Game Object 的时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | An array of objects containing game object data. Game Object 数据数组。 |
| return[...] | object | The game object and its registration data. Game Object 及其注册数据。 |
| return[...].id | integer (64-bit) | The ID of the game object. 范围: [0, 18446744073709551615] 或 [-9223372036854775808, 9223372036854775807] |
| return[...].name | string | The name of the game object. Game Object 名称。 |
| return[...].registerTime | integer (32-bit) | The time at which the game object was registered. 注册时间。范围: [-2147483648, 2147483647] |
| return[...].unregisterTime | integer (32-bit) | The time at which the game object was unregistered. 注销时间。范围: [-2147483648, 2147483647] |

## JSON-RPC 请求示例

### 示例：查询在 1 分钟前注册的 Game Object

Query game objects registered at or before 1 minute.

```json
{
    "function": "ak.wwise.core.profiler.getGameObjects",
    "params": {
        "time": 60000
    }
}
```

## JSON-RPC 响应示例

```json
{
    "return": [
        {
            "id": 11223344,
            "name": "Player",
            "registerTime": 1000,
            "unregisterTime": -1
        }
    ]
}
```

## 注意事项

- `unregisterTime` 为 -1 表示该 Game Object 尚未被注销
- 需要先调用 `startCapture` 进行捕获

## 相关函数

- [ak.wwise.core.profiler.getVoices](./getVoices.md)
- [ak.wwise.core.profiler.getBusses](./getBusses.md)
- [ak.wwise.core.profiler.getAudioObjects](./getAudioObjects.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getgameobjects.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getgameobjects.html)
