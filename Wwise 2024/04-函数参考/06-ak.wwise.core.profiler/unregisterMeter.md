# ak.wwise.core.profiler.unregisterMeter

## ▎ 命名空间: ak.wwise.core.profiler

## 概述

Unregisters a bus or device that was registered with ak.wwise.core.profiler.registerMeter.

取消注册之前通过 `registerMeter` 注册的 Bus 或 Device。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of: | 是 | — | The ID (GUID), name, or path of the object to receive meter data. 要取消 Meter 注册的对象。必须是 Bus、Aux Bus 或 Device。 |
| object | string | — | — | 格式为 type:name 的名称（如 `Bus:Master Audio Bus`）。 |
| object | string | — | — | 对象 GUID，格式: {aabbcc00-1122-3344-5566-77889900aabb}。 |
| object | string | — | — | 项目路径。 |

## 返回值

（官网未提供 - 该函数无返回值，调用成功返回空对象 {}）

## JSON-RPC 请求示例

### 示例：取消注册 Bus 的 Metering

Unregistering a bus for metering

```json
{
    "function": "ak.wwise.core.profiler.unregisterMeter",
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

- 必须与 `registerMeter` 成对使用
- Master Audio Bus 默认被注册，如需取消也需调用此函数

## 相关函数

- [ak.wwise.core.profiler.registerMeter](./registerMeter.md)
- [ak.wwise.core.profiler.getMeters](./getMeters.md)

## 相关 Topic

- [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics.html)

## 官方文档链接

[https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_unregistermeter.html](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_unregistermeter.html)
