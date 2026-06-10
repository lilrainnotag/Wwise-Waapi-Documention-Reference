# ak.wwise.core.audio.setConversionPlugin

## ▎ 命名空间: ak.wwise.core.audio

## 概述

更改用于音频文件转换的插件（Plug-in）。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| conversion * | string (GUID/名称/路径) | 是 | — | 用于转换的对象（Conversion Settings），可以是 ID (GUID)、名称或项目路径 |
| platform * | string (GUID/名称) | 是 | — | 设置应用的目标平台，可以是 ID (GUID) 或唯一名称 |
| plugin * | string | 是 | — | 用于未来转换的插件名称 |

(* 必填)

## 返回值

（空对象 `{}`）

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audio.setConversionPlugin",
  "params": {
    "conversion": "{6D1B890C-9826-4384-BF07-C15223E9FB56}",
    "platform": "Windows",
    "plugin": "Vorbis"
  },
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {},
  "id": 1
}
```

## 注意事项

- `conversion` 参数指向一个 Conversion Settings 对象（通常为 ShareSet 类型）。
- 此设置会影响后续使用 `ak.wwise.core.audio.convert` 进行的音频转换操作。
- `plugin` 参数的值应为 Wwise 中已安装的转换插件名称，如 `Vorbis`、`PCM`、`ADPCM` 等。

## 相关函数

- [[ak.wwise.core.audio.convert]] — 转换音频文件

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audio.setConversionPlugin](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_setconversionplugin.html)
- [示例：设置转换插件](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audio_setconversionplugin_example_set_conversion_plugin.html)
