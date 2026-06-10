# ak.wwise.core.gameParameter.setRange

## 命名空间: ak.wwise.core.gameParameter

## 概述

设置 Game Parameter 的 Min 和 Max 属性。此操作会修改使用该 Game Parameter 作为 X 轴的 RTPC 曲线和 Blend Track。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | string (GUID) / string (name) / string (path) | 是 | — | Game Parameter 的 ID (GUID)、名称或路径 |
| min | number | 是 | — | Game Parameter 的最小值 |
| max | number | 是 | — | Game Parameter 的最大值 |
| onCurveUpdate | string | 是 | — | 修改 Min/Max 值对 RTPC 曲线和 Blend Track 的影响方式。可选值：`stretch`（拉伸/压缩以匹配新范围，Set Game Parameter 动作值也会缩放）、`preserveX`（保持所有项的 X 位置，超出范围则删除，动作值被钳制） |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功设置时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.core.gameParameter.setRange",
  "params": {
    "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
    "min": 0.0,
    "max": 100.0,
    "onCurveUpdate": "stretch"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 修改 Game Parameter 范围会影响所有使用该 Game Parameter 的 RTPC 曲线和 Blend Track
- `stretch` 模式：所有项保留，但 X 位置会随曲线拉伸/压缩而改变
- `preserveX` 模式：保持所有项的 X 位置，超出新范围的项被删除

## 相关函数

- [ak.wwise.core.object.get](../02-ak.wwise.core/)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.core.gameParameter.setRange](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_gameParameter_setRange.html)
