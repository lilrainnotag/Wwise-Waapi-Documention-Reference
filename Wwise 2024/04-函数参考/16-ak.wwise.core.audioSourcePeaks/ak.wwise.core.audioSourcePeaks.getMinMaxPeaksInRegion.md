# ak.wwise.core.audioSourcePeaks.getMinMaxPeaksInRegion

## ▎ 命名空间: ak.wwise.core.audioSourcePeaks

## 概述

获取音频源指定区域内的最小/最大峰值对，以二进制字符串集合的形式返回（每个通道一个）。字符串是 Base64 编码的 16 位有符号整数数组，最小值和最大值交替排列。如果 `getCrossChannelPeaks` 为 true，则只返回一个二进制字符串，表示所有通道的全局峰值。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object * | string (GUID/名称/路径) | 是 | — | 音频源对象的 ID (GUID)、名称或路径 |
| timeFrom * | number | 是 | — | 需要峰值的音频源区域的起始时间（秒）。必须小于 `timeTo`。范围：[0,*] |
| timeTo * | number | 是 | — | 需要峰值的音频源区域的结束时间（秒）。必须大于 `timeFrom`。范围：[0,*] |
| numPeaks * | integer | 是 | — | 需要的峰值数量（最小为 1）。范围：[1,4294967295] |
| getCrossChannelPeaks | boolean | 否 | — | 为 true 时，跨所有通道全局计算峰值，而不是每个通道分别计算 |

(* 必填)

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| peaksBinaryStrings | array | 二进制字符串数组，每个字符串代表一个通道的 min/max 峰值数据 |
| peaksBinaryStrings [...] | string | 二进制字符串。当 `getCrossChannelPeaks` 为 true 时，数组中只有一个字符串 |
| numChannels | number | 峰值数据的通道数（即 `peaksBinaryStrings` 中的字符串数）。`getCrossChannelPeaks` 为 true 时为 1 |
| maxAbsValue | number | 峰值可以取的最大值。可用于归一化峰值（范围 -1 到 1） |
| peaksArrayLength | number | 返回的 min/max 通道数组中的峰值数量。如果小于 `numPeaks`，表示可用样本少于请求数量 |
| peaksDataSize | number | 峰值 min/max 数组中的数据大小。可与 `peaksArrayLength` 一起用于解码二进制字符串 |
| channelConfig | string | 通道配置 |

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.audioSourcePeaks.getMinMaxPeaksInRegion",
  "params": {
    "object": "{AAAAAAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE}",
    "timeFrom": 0,
    "timeTo": 2,
    "numPeaks": 750,
    "getCrossChannelPeaks": false
  },
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {
    "peaksBinaryStrings": [
      "longbase64string",
      "longbase64string"
    ],
    "numChannels": 2,
    "maxAbsValue": 32767,
    "peaksArrayLength": 750,
    "peaksDataSize": 1000
  },
  "id": 1
}
```

## 注意事项

- 返回的 `peaksBinaryStrings` 是 Base64 编码的 16 位有符号整数数组。解码方法：先 Base64 解码为字节数组，再按 16 位有符号整数（小端序）解析。
- 最小值（min）和最大值（max）交替存储（interleaved）。
- 峰值可以除以 `maxAbsValue` 来归一化到 [-1, 1] 范围。
- 如果 `peaksArrayLength < numPeaks`，说明请求的时间窗口内可用样本不足，返回了所有可用的峰值。

## 相关函数

- [[ak.wwise.core.audioSourcePeaks.getMinMaxPeaksInTrimmedRegion]] — 获取裁剪区域内的峰值

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.audioSourcePeaks.getMinMaxPeaksInRegion](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audiosourcepeaks_getminmaxpeaksinregion.html)
- [示例：获取每通道峰值](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_audiosourcepeaks_getminmaxpeaksinregion_example_getting_peaks_per_channel.html)
