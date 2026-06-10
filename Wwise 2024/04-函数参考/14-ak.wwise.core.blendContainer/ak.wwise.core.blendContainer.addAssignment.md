# ak.wwise.core.blendContainer.addAssignment

## 命名空间: ak.wwise.core.blendContainer

## 概述

向 Blend Track 添加新的分配。等效于在 Blend Tracks Editor 中执行拖放操作。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | string (GUID) | 是 | — | Blend Track 的 ID (GUID)，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |
| child | string (GUID) / string (name) / string (path) | 是 | — | 要分配的对象的 ID、名称或路径。此对象必须是 Blend Track 的 Blend Container 的子对象 |
| index | integer | 否 | 末尾 | 分配在 Blend Track 中的索引位置，会被限制在 [0, n] 范围（n 为当前分配数）。未提供时添加到末尾 |
| edges | array | 否 | 默认值 | Blend Track 内分配的边配置。仅在 Blend Track 有 crossfade Game Parameter 时有意义。需提供两个边：0=左，1=右 |
| edges[].fadeMode | string | 是（若提供edges） | — | 边 crossfade 配置。可选值：`None`、`Manual`、`Automatic` |
| edges[].fadeShape | string | 是（若提供edges） | — | 边 crossfade 曲线形状。可选值：`Constant`、`Linear`、`Log3`、`Log2`、`Log1`、`InvertedSCurve`、`SCurve`、`Exp1`、`Exp2`、`Exp3` |
| edges[].edgePosition | number | 是（若提供edges） | — | 边的位置，必须在 crossfade Game Parameter 的范围内 |
| edges[].fadePosition | number | 否 | — | fade 曲线的起止位置。仅在 fadeMode 为 `Manual` 时使用 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| child | string (GUID) | 分配对象的 ID (GUID) |
| index | integer | 分配在 Blend Track 中的索引位置 |
| edges | array | 分配的边配置，0=左，1=右 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.core.blendContainer.addAssignment",
  "params": {
    "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
    "child": "{DDEEFF00-1122-3344-5566-77889900DDEE}",
    "index": 0
  }
}
```

## JSON-RPC 响应示例

```json
{
  "child": "{DDEEFF00-1122-3344-5566-77889900DDEE}",
  "index": 0,
  "edges": []
}
```

## 注意事项

- 等效于在 Blend Tracks Editor 中手动拖放操作
- child 对象必须是 Blend Track 所属 Blend Container 的子对象
- edges 参数仅在 Blend Track 配置了 crossfade Game Parameter 时有意义

## 相关函数

- [ak.wwise.core.blendContainer.addTrack](ak.wwise.core.blendContainer.addTrack.md)
- [ak.wwise.core.blendContainer.removeAssignment](ak.wwise.core.blendContainer.removeAssignment.md)
- [ak.wwise.core.blendContainer.getAssignments](ak.wwise.core.blendContainer.getAssignments.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.core.blendContainer.addAssignment](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_blendContainer_addAssignment.html)
