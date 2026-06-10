# ak.wwise.debug.generateToneWAV

## 命名空间
ak.wwise.debug

## 状态
正常

## 概述

Generate a WAV file playing a tone with a simple envelope and save it to the specified location. This is provided as a utility to generate test WAV files.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| path * | string | 是 | — | File path to write the generated WAV file. This path normally uses the file extension WAV. |
| bitDepth | string | 否 | int16 | Bit depth of the audio file. Possible values: int16, float32 |
| sampleRate | number | 否 | 48000 | Sample rate of the audio file. Range: [300, 192000] |
| channelConfig | string | 否 | 1.0 | Channel configuration of the audio file. Please use the silence waveform for the ambisonics configurations, as the other tone signals will be incompatible with the format. Possible values: 0.1, 1.0, 2.0, 2.1, 3.0, 4.0, 5.1, 7.1, 5.1.2, 7.1.2, 7.1.4, Ambisonics 1st order ~ 5th order |
| setAnonymous | boolean | 否 | — | Sets the channel configuration type to anonymous, this overrides the channel config but keeps the number of channels specified. |
| sustainTime | number | 否 | 1 | Number of seconds of the signal holds at the specified level. Range: [0, *) |
| sustainLevel | number | 否 | 0 | Decibel attenuation for the sustained signal. Range: [-100, 0] |
| attackTime | number | 否 | 0 | Number of seconds for the signal to reach sustain level. Range: [0, *) |
| releaseTime | number | 否 | 0 | Number of seconds for the signal to release from sustain level. Range: [0, *) |
| waveform | string | 否 | silence | Waveform type. Possible values: silence, sine, triangle, square, whiteNoise |
| waveformChannelMask | integer | 否 | (全部通道) | Specifies which channels receive waveform data. The channel mask is a bit field where each bit represents a channel. The least significant bit represents the channel at index zero. The bits with 0 are silent. |
| frequency | number | 否 | 440 | Waveform frequency. Range: [1, 22000] |

\* 表示必填参数

## 参数 Schema

（官网未提供独立 Schema）

## 返回值

无返回值（返回空对象 `{}`）。

## 返回值 Schema

（无）

## JSON-RPC 请求示例

```json
{
    "path": "C:\\WAV\\beep.wav",
    "channelConfig": "1.0",
    "waveform": "sine",
    "frequency": 800,
    "attackTime": 0.01,
    "sustainTime": 0.98,
    "releaseTime": 0.01,
    "sustainLevel": 0
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 这是一个实用工具函数，用于生成测试用的 WAV 文件
- 对于 Ambisonics 配置，请使用 silence 波形，其他音调信号与该格式不兼容
- channelConfig 设置为 anonymous 会覆盖通道配置但保留指定的通道数
- 生成的 WAV 文件会保存到指定路径

## 相关函数

- [ak.wwise.debug.getWalTree](ak.wwise.debug.getWalTree.md)
- [ak.wwise.debug.testAssert](ak.wwise.debug.testAssert.md)
- [ak.wwise.debug.testCrash](ak.wwise.debug.testCrash.md)
- [ak.wwise.debug.validateCall](ak.wwise.debug.validateCall.md)

## 相关 Topic

- Using the Wwise Authoring API (WAAPI)

## 官方文档链接

- [ak.wwise.debug.generateToneWAV](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_debug_generatetonewav.html)
- [示例：Generating a short sine tone WAV file](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_debug_generatetonewav_example_generating_a_short_sine_tone_wav_file.html)
