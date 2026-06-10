# ak.wwise.core.blendContainer.getAssignments

## 命名空间: ak.wwise.core.blendContainer

## 概述

返回 Blend Track 的分配列表。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | string (GUID) | 是 | — | Blend Track 的 ID (GUID)，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | Blend Track 分配数组 |
| return[].child | string (GUID) | 分配的子对象 ID (GUID) |
| return[].index | integer | 子对象在 Blend Track 分配中的索引位置 |
| return[].edges | array | 分配的边配置（0=左，1=右），包含 fadeMode、fadeShape、edgePosition、fadePosition 等字段 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.core.blendContainer.getAssignments",
  "params": {
    "object": "{AABBCC00-1122-3344-5566-77889900AABB}"
  }
}
```

## JSON-RPC 响应示例

```json
{
  "return": [
    {
      "child": "{DDEEFF00-1122-3344-5566-77889900DDEE}",
      "index": 0,
      "edges": []
    }
  ]
}
```

## 注意事项

- object 参数指定的是 Blend Track（不是 Blend Container）的 ID

## 相关函数

- [ak.wwise.core.blendContainer.addAssignment](ak.wwise.core.blendContainer.addAssignment.md)
- [ak.wwise.core.blendContainer.removeAssignment](ak.wwise.core.blendContainer.removeAssignment.md)
- [ak.wwise.core.blendContainer.addTrack](ak.wwise.core.blendContainer.addTrack.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.core.blendContainer.getAssignments](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_blendContainer_getAssignments.html)
