# ak.wwise.core.switchContainer.getAssignments

## 命名空间
ak.wwise.core.switchContainer

## 状态
正常

## 概述

Returns the list of assignments between a Switch Container's children and states.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| id * | any of: string | 是 | — | The ID (GUID), name, or path of the Switch Container. 支持格式: type:name (如 Event:Play_Sound_01), Global:shortId (如 Global:245489792), GUID ({aabbcc00-...}), 或 project path (如 \Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX). |

\* 表示必填参数

## 参数 Schema

（官网未提供独立 Schema）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | List of assignments (pairs of child and state). |
| return [...] | object | Assignment (pair of child and state). |
| return[...].child * | any of: string | The ID (GUID), name, or path of the child assigned to a State. |
| return[...].stateOrSwitch * | any of: string | The ID (GUID), name, or path of the State or Switch to which the child is assigned. |

## 返回值 Schema

（官网未提供独立 Schema）

## JSON-RPC 请求示例

```json
{
    "id": "{7A12D08F-B0D9-4403-9EFA-2E6338C197C1}"
}
```

## JSON-RPC 响应示例

```json
{
    "return": [
        {
            "child": "{7A12D08F-B0D9-4403-9EFA-2E6338C197C1}",
            "stateOrSwitch": "{A076AA65-B71A-45BB-8841-5A20C52CE727}"
        },
        {
            "child": "{8B12D08F-B0D9-4403-9EFA-2E6338C197D1}",
            "stateOrSwitch": "{B076BB65-B71A-45BB-8841-5A20C52CE738}"
        }
    ]
}
```

## 注意事项

- 返回 Switch Container 的子对象与状态/开关之间的分配关系列表
- 每个 assignment 包含 child 和 stateOrSwitch 两个字段

## 相关函数

- [ak.wwise.core.switchContainer.addAssignment](ak.wwise.core.switchContainer.addAssignment.md)
- [ak.wwise.core.switchContainer.removeAssignment](ak.wwise.core.switchContainer.removeAssignment.md)

## 相关 Topic

- Switch Container
- Assigned Objects View
- Using the Wwise Authoring API (WAAPI)

## 官方文档链接

- [ak.wwise.core.switchContainer.getAssignments](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_switchcontainer_getassignments.html)
- [示例：Getting the assignments of a Switch Container](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_switchcontainer_getassignments_example_getting_the_assignments_of_a_switch_container.html)
