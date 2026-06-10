# ak.wwise.core.transport.destroy

▎ **命名空间**: ak.wwise.core.transport

## 概述

Destroys the given transport object.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| transport | integer | 是 | — | The transport object ID to be used with all other ak.wwise.core.transport functions. Unsigned Integer 32-bit，范围: [0, 4294967295]。 |

## 返回值

（官网未提供 — 销毁成功时不返回特定数据）

## JSON-RPC 请求示例

```json
{
    "transport": 1234
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 销毁 transport 对象后，该 ID 不再有效，无法继续用于其他 transport 操作。
- 建议在播放完成后及时销毁 transport 对象以释放资源。

## 相关函数

- ak.wwise.core.transport.create
- ak.wwise.core.transport.getList

## 相关 Topic

- Wwise Transport 控制

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_transport_destroy.html
