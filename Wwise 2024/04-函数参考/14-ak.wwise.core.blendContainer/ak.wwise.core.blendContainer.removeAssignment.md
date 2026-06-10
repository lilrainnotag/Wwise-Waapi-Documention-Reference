# ak.wwise.core.blendContainer.removeAssignment

## 命名空间: ak.wwise.core.blendContainer

## 概述

从 Blend Track 中移除一个分配。等效于在 Blend Tracks Editor 中删除一个条目。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | string (GUID) | 是 | — | Blend Track 的 ID (GUID)，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |
| child | string (GUID) / string (name) / string (path) | 是 | — | 要取消分配的对象 ID (GUID)、名称或路径 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功移除时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.core.blendContainer.removeAssignment",
  "params": {
    "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
    "child": "{DDEEFF00-1122-3344-5566-77889900DDEE}"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 等效于在 Blend Tracks Editor 中手动删除分配条目

## 相关函数

- [ak.wwise.core.blendContainer.addAssignment](ak.wwise.core.blendContainer.addAssignment.md)
- [ak.wwise.core.blendContainer.addTrack](ak.wwise.core.blendContainer.addTrack.md)
- [ak.wwise.core.blendContainer.getAssignments](ak.wwise.core.blendContainer.getAssignments.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.core.blendContainer.removeAssignment](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_blendContainer_removeAssignment.html)
