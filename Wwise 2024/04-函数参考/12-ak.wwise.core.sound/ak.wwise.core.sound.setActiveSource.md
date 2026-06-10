# ak.wwise.core.sound.setActiveSource

## ▎ 命名空间: ak.wwise.core.sound

## 概述

设置指定 Sound 对象当前使用的音频源版本。使用 `ak.wwise.core.object.get` 并指定 `activeSource` 返回选项可获取 Sound 的当前活动源。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| sound * | string (GUID/名称/路径) | 是 | — | Sound 对象的 ID (GUID)、名称或路径 |
| source * | string (GUID/名称/路径) | 是 | — | 源对象的 ID (GUID)、名称或路径。该源必须是 sound 的子对象 |
| platform | string (GUID/名称) | 否 | 当前平台 | 平台 ID (GUID) 或名称。不指定时使用当前平台 |

(* 必填)

## 返回值

（无返回值）

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- `source` 必须是 `sound` 的子对象。
- `platform` 参数可选，不指定时默认使用当前在 Wwise 界面中选中的平台。
- Sound 对象可以有多个音频源（如多语言版本），此函数用于在它们之间切换。

## 相关函数

- [[ak.wwise.core.object.get]] — 获取对象信息（支持 activeSource 返回选项）
- [[ak.wwise.core.audio.import]] — 导入音频文件

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.sound.setActiveSource](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_sound_setactivesource.html)
