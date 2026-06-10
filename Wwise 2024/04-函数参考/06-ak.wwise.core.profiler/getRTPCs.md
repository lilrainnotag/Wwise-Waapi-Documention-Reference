# ak.wwise.core.profiler.getRTPCs

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves active RTPCs at a specific profiler capture time.

在指定的 Profiler 捕获时间点获取活跃的 RTPC 信息。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for RTPCs, or a Time Cursor. 查询时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of RTPCs. RTPC 数组。 |
| return[...] | object | An RTPC associated with a playing voice. |
| return[...].id | string | The ID (GUID) of the Game Parameter, LFO, Time, Envelope or MIDI Parameter object. 格式: {aabbcc00-1122-3344-5566-77889900aabb} |
| return[...].name | string | The name of the Game Parameter, LFO, Time, Envelope or MIDI Parameter object. |
| return[...].gameObjectId | integer (64-bit) | The Game Object associated with the RTPC scope, or AK_INVALID_GAME_OBJECT for global scope RTPCs. 范围: [0, 18446744073709551615] |
| return[...].value | number | The value of the parameter at the cursor time. Cursor 时间点的参数值。 |

## JSON-RPC 请求示例

### 示例：查询指定时间点的 RTPC ID 和值

Querying the RTPC id and value at a point in time

```json
{
    "function": "ak.wwise.core.profiler.getRTPCs",
    "params": {
        "time": 30000
    }
}
```

## JSON-RPC 响应示例

```json
{
    "return": [
        {
            "id": "{AABBCC00-1122-3344-5566-77889900AABB}",
            "name": "Distance",
            "gameObjectId": 11223344,
            "value": 150.5
        }
    ]
}
```

## 注意事项

- gameObjectId 为 AK_INVALID_GAME_OBJECT 时表示全局作用域的 RTPC
- RTPC 包括 Game Parameter、LFO、Time、Envelope 和 MIDI Parameter 类型的对象

## 相关函数

- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getrtpcs.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getrtpcs.html)
