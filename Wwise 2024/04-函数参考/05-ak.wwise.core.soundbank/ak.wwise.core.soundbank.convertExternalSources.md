# ak.wwise.core.soundbank.convertExternalSources

▎ **命名空间**: ak.wwise.core.soundbank

## 概述

Converts the external sources files for the project as detailed in the wsources file, and places them into either the default folder, or the folder specified by the output argument. External Sources are a special type of source that you can put in a Sound object in Wwise. It indicates that the real sound data will be provided at run time. While External Source conversion is also triggered by SoundBank generation, this operation can be used to process sources not contained in the Wwise Project. Please refer to Wwise SDK help page "Integrating External Sources".

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| sources | array | 是 | — | An array of external sources files and corrisponding arguments. |
| sources[...] | object | — | — | An external sources file and its arguments. |
| sources[...].input | string | 是 | — | The path to the wsources file. |
| sources[...].platform | string (name or GUID) | 是 | — | The platform to convert external sources for. 可以是平台名称字符串（如 "Windows"、"Linux"），或平台 GUID（形如 {aabbcc00-1122-3344-5566-77889900aabb}）。 |
| sources[...].output | string | 否 | WwiseProject/.cache/ExternalSources/Platform | Optional argument for the path of the output folder to be generated. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | — | 返回空对象 {} |

## JSON-RPC 请求示例

### 示例 1：为单个平台转换 External Sources

```json
{
    "sources": [
        {
            "input": "C:\\My-Wsources\\sources1.wsources",
            "platform": "Linux"
        }
    ]
}
```

### 示例 2：为多个平台和输出路径转换 External Sources

```json
{
    "sources": [
        {
            "input": "C:\\My-Wsources\\sources1.wsources",
            "platform": "Windows"
        },
        {
            "input": "C:\\My-Wsources\\sources2.wsources",
            "platform": "{6E0CB257-C6C8-4C5C-8366-2740DFC441EC}",
            "output": "C:\\ExternalSources-Alternate\\Windows"
        },
        {
            "input": "C:\\My-Wsources\\sources1.wsources",
            "platform": "Linux",
            "output": "C:\\ExternalSources-Alternate\\Linux"
        }
    ]
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- External Source 转换也会在 SoundBank 生成时触发，但此操作可用于处理不在 Wwise 工程中的源文件。
- platform 参数支持平台名称字符串或平台 GUID 两种格式。
- 默认输出路径为 `WwiseProject/.cache/ExternalSources/<Platform>`。

## 相关函数

- ak.wwise.core.soundbank.generate

## 相关 Topic

- convert-external-source

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_convertexternalsources.html
