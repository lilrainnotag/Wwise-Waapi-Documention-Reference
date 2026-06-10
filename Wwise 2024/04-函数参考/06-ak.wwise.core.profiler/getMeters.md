# ak.wwise.core.profiler.getMeters

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the Meter data for all registered busses, aux busses and devices. Only the master audio bus is registered by default. Use ak.wwise.core.profiler.registerMeter for other busses, before retrieval of the meter data.

获取所有已注册的 Bus、Aux Bus 和 Device 的 Meter 数据。默认仅注册 Master Audio Bus。获取其他 Bus 的 Meter 数据前需先调用 `registerMeter`。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query, or a Time Cursor. 查询时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 范围: [0,*] |
| time | string | — | — | 可选值: `user`, `capture` |

## Options

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | — | Specifies what is being returned for every object. 每个对象要返回的成员。 |
| return[...] | string | — | — | 内置访问器: `id`, `name`, `notes`, `type`, `pluginName`, `shortId`, `classId`, `category`, `filePath`, `workunit`, `parent`, `owner`, `path`, `isPlayable`, `childrenCount`, `totalSize`, `mediaSize`, `objectSize`, `structureSize` 等。也可使用 `@PropertyName` 格式访问属性。 |
| platform | string/GUID | 否 | 当前平台 | The ID (GUID) or name of the platform. |
| language | string/GUID | 否 | — | The ID (GUID) or name of the language. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| meters | array | Array of registered meters. 已注册的 Meter 数组。 |
| meters[...] | object | The meter information. Meter 信息。 |
| meters[...].object | object | The metered object (Wwise object). 被计量的 Wwise 对象。 |
| meters[...].object.id | string | The ID (GUID) of the object. 格式: {aabbcc00-...} |
| meters[...].object.name | string | The name of the object. |
| meters[...].object.type | string | The type of the object. |
| meters[...].object.path | string | The path from the project root. |
| meters[...].object.parent | object | The parent object (含 id, name). |
| meters[...].object.owner | object | The owner object (含 id, name). |
| meters[...].object.classId | integer (32-bit) | The class ID of the object. |
| meters[...].object.shortId | integer | The Short ID of the object. |
| meters[...].object.filePath | string | The path to the file containing the object. |
| meters[...].object.workunit | object | The parent Work Unit (含 id, name). |

> **注意**: 返回值中 `object` 字段包含完整的 Wwise 对象属性（id, name, notes, type, pluginName, shortId, classId, category, filePath, workunit, parent, owner, path, isPlayable, childrenCount, totalSize, mediaSize, objectSize, structureSize 等）。实际返回字段取决于 `return` options 的设置。完整字段列表请参考 [Wwise Objects Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wobjects_index.html)。

## JSON-RPC 请求示例

```json
{
    "function": "ak.wwise.core.profiler.getMeters",
    "params": {
        "time": "capture"
    },
    "options": {
        "return": [
            "id",
            "name",
            "@Volume"
        ]
    }
}
```

## JSON-RPC 响应示例

```json
{
    "meters": [
        {
            "object": {
                "id": "{AABBCC00-1122-3344-5566-77889900AABB}",
                "name": "Master Audio Bus",
                "@Volume": -3.5
            }
        }
    ]
}
```

## 注意事项

- 默认仅 Master Audio Bus 被注册，其他 Bus 需通过 `registerMeter` 注册
- 必须先通过 `enableProfilerData` 启用 `meter` 数据类型
- `return` options 支持 Wwise Object 的所有内置访问器和 `@property` 格式的属性访问
- 可指定 `platform` 和 `language` 来获取特定平台/语言的属性值

## 相关函数

- [ak.wwise.core.profiler.registerMeter](./registerMeter.md)
- [ak.wwise.core.profiler.unregisterMeter](./unregisterMeter.md)
- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)

## 相关 Topic

- [Wwise Objects Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wobjects_index.html)
- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getmeters.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getmeters.html)
