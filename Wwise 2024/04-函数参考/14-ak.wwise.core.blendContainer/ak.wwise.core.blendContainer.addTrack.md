# ak.wwise.core.blendContainer.addTrack

## 命名空间: ak.wwise.core.blendContainer

## 概述

向 Blend Container 添加新的 Blend Track。等效于在 Blend Track Editor 中点击 New Blend Track。要获取 Blend Track 列表，使用 `ak.wwise.core.object.get` 并设置 `{return = "blendTracks"}`。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | string (GUID) / string (name) / string (path) | 是 | — | Blend Container 的 ID (GUID)、名称或路径 |
| name | string | 是 | — | Blend Track 的名称 |
| id | string (GUID) | 否 | — | **内部使用**。要分配给新创建对象的 ID (GUID) |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| id | string (GUID) | Blend Track 的 ID (GUID) |
| name | string | Blend Track 的名称 |
| type | string | 对象类型 |
| shortId | integer | 对象的 Short ID |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.core.blendContainer.addTrack",
  "params": {
    "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
    "name": "New Blend Track"
  }
}
```

## JSON-RPC 响应示例

```json
{
  "id": "{DDEEFF00-1122-3344-5566-77889900DDEE}",
  "name": "New Blend Track",
  "type": "BlendTrack",
  "shortId": 12345678
}
```

## 注意事项

- 等效于在 Blend Track Editor 中点击 New Blend Track 按钮
- 可使用 `ak.wwise.core.object.get` 配合 `{return = "blendTracks"}` 获取现有 Blend Track 列表
- id 参数仅供内部使用

## 相关函数

- [ak.wwise.core.blendContainer.addAssignment](ak.wwise.core.blendContainer.addAssignment.md)
- [ak.wwise.core.blendContainer.removeAssignment](ak.wwise.core.blendContainer.removeAssignment.md)
- [ak.wwise.core.blendContainer.getAssignments](ak.wwise.core.blendContainer.getAssignments.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.core.blendContainer.addTrack](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_blendContainer_addTrack.html)
