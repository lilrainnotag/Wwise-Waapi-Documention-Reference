# ak.wwise.core.profiler.getLoadedMedia

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Retrieves the loaded media at a specific profiler capture time. This data can also be found in the Advanced Profiler, under the Loaded Media tab. To ensure the Loaded Media data is received, refer to ak.wwise.core.profiler.enableProfilerData.

在指定的 Profiler 捕获时间点获取已加载的 Media 信息。此数据也可在 Advanced Profiler 的 Loaded Media 标签页中查看。确保已通过 `enableProfilerData` 启用 Loaded Media 数据捕获。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| time | one of: | 是 | — | Time in milliseconds to query for media, or a Time Cursor. 查询 Media 的时间（毫秒）或 Time Cursor。 |
| time | integer | — | — | 毫秒时间值。范围: [0,*] |
| time | string | — | — | 全局 Profiler Cursor 标识。可选值: `user`, `capture` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Array of Loaded Media. 已加载 Media 数组。 |
| return[...] | object | Information about a media file loaded into memory. 一个已加载到内存中的 Media 文件信息。 |
| return[...].mediaId | integer | The short ID of the media file. Media 文件的 Short ID。 |
| return[...].fileName | string | The name of the media file. Media 文件名。 |
| return[...].format | string | The audio format of the media file. Media 文件的音频格式。 |
| return[...].size | integer | The size (in bytes) of the media file. Media 文件大小（字节）。 |
| return[...].soundBank | string | The name of the SoundBank that contains the media file. 包含此 Media 文件的 SoundBank 名称。 |

## JSON-RPC 请求示例

### 示例：查询指定时间点的已加载 Media

Querying the Loaded Media at a point in time.

```json
{
    "function": "ak.wwise.core.profiler.getLoadedMedia",
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
            "mediaId": 1001,
            "fileName": "Explosion.wem",
            "format": "PCM",
            "size": 245760,
            "soundBank": "Main"
        }
    ]
}
```

## 注意事项

- 必须先调用 `enableProfilerData` 并启用 `loadedMedia` 数据类型才能获取结果
- Media 文件通过 `PrepareEvent()` 和 `PrepareGameSyncs()` 函数加载到内存
- 数据也可在 Wwise Advanced Profiler 的 Loaded Media 标签页中查看

## 相关函数

- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)
- [ak.wwise.core.profiler.getCursorTime](./getCursorTime.md)
- [ak.wwise.core.profiler.getStreamedMedia](./getStreamedMedia.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getloadedmedia.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_getloadedmedia.html)
