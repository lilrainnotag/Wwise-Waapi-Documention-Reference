# ak.wwise.core.audioSourcePeaks.getMinMaxPeaksInTrimmedRegion

## ▎ 命名空间: ak.wwise.core.audioSourcePeaks

## 概述

获取音频源整个裁剪（trimmed）区域内每个通道的最小/最大峰值对，以二进制字符串数组的形式返回（每个通道一个）。字符串是 Base64 编码的 16 位有符号整数数组，最小值和最大值交替排列。如果 `getCrossChannelPeaks` 为 true，则只返回一个二进制字符串，表示所有通道的全局峰值。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object * | string (GUID/名称/路径) | 是 | — | 音频源对象的 ID (GUID)、名称或路径 |
| numPeaks * | integer | 是 | — | 需要的峰值数量（最小为 1）。范围：[1,4294967295] |
| getCrossChannelPeaks | boolean | 否 | — | 为 true 时，跨所有通道全局计算峰值，而不是每个通道分别计算 |

(* 必填)

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| peaksBinaryStrings | array | 二进制字符串数组 |
| peaksBinaryStrings [...] | string | 二进制字符串。当 `getCrossChannelPeaks` 为 true 时，数组中只有一个字符串 |
| numChannels | number | 峰值数据的通道数。`getCrossChannelPeaks` 为 true 时为 1 |
| maxAbsValue | number | 峰值可以取的最大值。可用于归一化峰值 |
| peaksArrayLength | number | 返回的 min/max 通道数组中的峰值数量 |
| peaksDataSize | number | 峰值 min/max 数组中的数据大小 |
| channelConfig | string | 通道配置 |

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- 与 `getMinMaxPeaksInRegion` 不同，此函数自动使用音频源的整个裁剪区域，无需指定 `timeFrom` 和 `timeTo` 参数。
- 解码 `peaksBinaryStrings`：先 Base64 解码为字节数组，再按 16 位有符号整数（小端序）解析，min/max 交替排列。
- `maxAbsValue` 可用于将峰值归一化到 [-1, 1] 范围。

## 相关函数

- [[ak.wwise.core.audioSourcePeaks.getMinMaxPeaksInRegion]] — 获取指定时间区域的峰值

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audioSourcePeaks.getMinMaxPeaksInTrimmedRegion](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audiosourcepeaks_getminmaxpeaksintrimmedregion.html)
