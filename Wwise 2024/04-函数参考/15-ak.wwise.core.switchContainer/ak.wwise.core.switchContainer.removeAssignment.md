# ak.wwise.core.switchContainer.removeAssignment

## 命名空间
ak.wwise.core.switchContainer

## 状态
正常

## 概述

Removes an assignment between a Switch Container's child and a State.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| child * | any of: string | 是 | — | The ID (GUID), name, or path of the object assigned to a State. This object must be the child of a Switch Container and must be currently assigned to a State. 支持格式: type:name, Global:shortId, GUID, 或 project path. |
| stateOrSwitch * | any of: string | 是 | — | The ID (GUID), name, or path of the State or Switch to which the child is assigned. Must be the child of the Switch Group or State Group that is currently set for the Switch Container. 支持格式: type:name, Global:shortId, GUID, 或 project path. |

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
    "child": "{7A12D08F-B0D9-4403-9EFA-2E6338C197C1}",
    "stateOrSwitch": "{A076AA65-B71A-45BB-8841-5A20C52CE727}"
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 等效于在 Assigned Objects 视图中选择并删除一个分配给 State 的子对象
- 子对象必须是 Switch Container 的子对象且当前已分配给某个状态
- stateOrSwitch 必须是当前 Switch Container 所设置的 Switch Group 或 State Group 的子对象
- 此函数无返回值（返回空对象）

## 相关函数

- [ak.wwise.core.switchContainer.addAssignment](ak.wwise.core.switchContainer.addAssignment.md)
- [ak.wwise.core.switchContainer.getAssignments](ak.wwise.core.switchContainer.getAssignments.md)
- ak.wwise.core.switchContainer.assignmentRemoved (topic)

## 相关 Topic

- Switch Container
- Assigned Objects View
- Using the Wwise Authoring API (WAAPI)

## 官方文档链接

- [ak.wwise.core.switchContainer.removeAssignment](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_switchcontainer_removeassignment.html)
- [示例：Removing an assignment from a Switch Container](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_switchcontainer_removeassignment_example_removing_an_assignment_from_a_switch_container.html)
