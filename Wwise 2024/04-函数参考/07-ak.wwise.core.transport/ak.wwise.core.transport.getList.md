# ak.wwise.core.transport.getList

▎ **命名空间**: ak.wwise.core.transport

## 概述

Returns the list of transport objects.

## 参数

（无需参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| list | array | An array of transport objects. |
| list[...] | object | A transport object. |
| list[...].object | string | The ID (GUID) of the object controlled by the transport object. 形如 {aabbcc00-1122-3344-5566-77889900aabb}。 |
| list[...].gameObject | integer | The game object used by the transport object. Unsigned Integer 64-bit，范围: [0, 18446744073709551615]。 |
| list[...].transport | integer | Transport object ID. Unsigned Integer 32-bit，范围: [0, 4294967295]。 |

## JSON-RPC 请求示例

```json
{}
```

## JSON-RPC 响应示例

```json
{
    "list": [
        {
            "object": "{A076AA65-B71A-45BB-8841-5A20C52CE727}",
            "gameObject": 0,
            "transport": 1234
        },
        {
            "object": "{BBBBBBBB-1111-2222-3333-444444444444}",
            "gameObject": 100,
            "transport": 5678
        }
    ]
}
```

## 注意事项

- 此函数无需任何参数，直接返回当前所有活动 transport 对象的列表。
- 可用于在批量操作前获取当前 transport 状态快照。

## 相关函数

- ak.wwise.core.transport.create

## 相关 Topic

- Wwise Transport 控制

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_transport_getList.html
