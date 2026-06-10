# ak.wwise.core.switchContainer.addAssignment

## 命名空间
ak.wwise.core.switchContainer

## 状态
正常

## 概述

Assigns a Switch Container's child to a Switch. This is the equivalent of doing a drag&drop of the child to a state in the Assigned Objects view. The child is always added at the end for each state.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| child * | any of: string | 是 | — | The ID (GUID), name, or path of the object to assign to a State. This object must be the child of a Switch Container. 支持格式: type:name, Global:shortId, GUID, 或 project path. |
| stateOrSwitch * | any of: string | 是 | — | The ID (GUID), name, or path of the State or Switch with which to assign. Must be the child of the Switch Group or State Group that is currently set for the Switch Container. 支持格式: type:name, Global:shortId, GUID, 或 project path. |

\* 表示必填参数

## 参数 Schema

（官网未提供独立 Schema）

## 返回值

（官网未明确列出返回值）

## 返回值 Schema

（无）

## JSON-RPC 请求示例

（官网示例页面返回 404，未提供）

## JSON-RPC 响应示例

（官网示例页面返回 404，未提供）

## 注意事项

- 等效于在 Assigned Objects 视图中拖放子对象到某个状态
- 子对象必须为 Switch Container 的子对象
- stateOrSwitch 必须是当前 Switch Container 所设置的 Switch Group 或 State Group 的子对象
- 子对象总是添加到每个状态的末尾

## 相关函数

- [ak.wwise.core.switchContainer.getAssignments](ak.wwise.core.switchContainer.getAssignments.md)
- [ak.wwise.core.switchContainer.removeAssignment](ak.wwise.core.switchContainer.removeAssignment.md)
- ak.wwise.core.switchContainer.assignmentAdded (topic)

## 相关 Topic

- Assigned Objects View
- Switch Container
- Using the Wwise Authoring API (WAAPI)

## 官方文档链接

- [ak.wwise.core.switchContainer.addAssignment](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_switchcontainer_addassignment.html)
