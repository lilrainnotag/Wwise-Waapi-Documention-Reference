# ak.wwise.core.profiler.registerMeter

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Registers a bus, an aux bus or device to receive meter data. Only the master audio bus is registered by default. Use ak.wwise.core.profiler.getMeters to retrieve the meter data after registering. Every call to ak.wwise.core.profiler.registerMeter must have a matching call to ak.wwise.core.profiler.unregisterMeter.

注册一个 Bus、Aux Bus 或设备以接收 Meter 数据。默认仅注册 Master Audio Bus。注册后使用 `getMeters` 获取 Meter 数据。每次调用 `registerMeter` 必须有对应的 `unregisterMeter` 调用。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of: | 是 | — | The ID (GUID), name, or path of the object to receive meter data. 要接收 Meter 数据的对象。必须是 Bus、Aux Bus 或 Device。 |
| object | string | — | — | 格式为 type:name 的名称（如 `Bus:Master Audio Bus`）或 Global:shortId（如 `Global:245489792`）。 |
| object | string | — | — | 对象 GUID，格式: {aabbcc00-1122-3344-5566-77889900aabb}。 |
| object | string | — | — | 项目路径，如 `\Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX`。 |

## 返回值

（官网未提供 - 该函数无返回值，调用成功返回空对象 {}）

## JSON-RPC 请求示例

### 示例：注册 Bus 以进行 Metering

Registering a bus for metering

```json
{
    "function": "ak.wwise.core.profiler.registerMeter",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}"
    }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 默认仅 Master Audio Bus 被注册
- 每次 `registerMeter` 调用必须有对应的 `unregisterMeter` 调用
- 需要先通过 `enableProfilerData` 启用 meter 数据类型
- 注册后使用 `getMeters` 获取 Meter 数据

## 相关函数

- [ak.wwise.core.profiler.unregisterMeter](./unregisterMeter.md)
- [ak.wwise.core.profiler.getMeters](./getMeters.md)
- [ak.wwise.core.profiler.enableProfilerData](./enableProfilerData.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_registermeter.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_registermeter.html)
