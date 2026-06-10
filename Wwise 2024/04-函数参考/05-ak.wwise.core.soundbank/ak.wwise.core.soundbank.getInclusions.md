# ak.wwise.core.soundbank.getInclusions

▎ **命名空间**: ak.wwise.core.soundbank

## 概述

Retrieves a SoundBank's inclusion list.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| soundbank | string (name/GUID/path) | 是 | — | The ID (GUID), name, or path of the SoundBank to add an inclusion to. 支持格式：type:name（如 SoundBank:MyBank）、Global:shortId、{GUID}、或工程路径。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| inclusions | array | An array of inclusions. |
| inclusions[...] | object | A SoundBank inclusion. |
| inclusions[...].object | string (必填) | The ID (GUID) of the object in the SoundBank's inclusion list. 形如 {aabbcc00-1122-3344-5566-77889900aabb}。 |
| inclusions[...].filter | array (必填) | Specifies what relations are being included. 可选值：events, structures, media。 |

## JSON-RPC 请求示例

```json
{
    "soundbank": "{A076AA65-B71A-45BB-8841-5A20C52CE727}"
}
```

## JSON-RPC 响应示例

```json
{
    "inclusions": [
        {
            "object": "{1111AAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE}",
            "filter": [
                "events"
            ]
        },
        {
            "object": "{2222AAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE}",
            "filter": [
                "structures",
                "media"
            ]
        }
    ]
}
```

## 注意事项

- `filter` 数组中的可选值为 `events`、`structures`、`media`，表示该对象在 SoundBank 中包含的关系类型。

## 相关函数

- ak.wwise.core.soundbank.setInclusions

## 相关 Topic

- SoundBank inclusion

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_getinclusions.html
