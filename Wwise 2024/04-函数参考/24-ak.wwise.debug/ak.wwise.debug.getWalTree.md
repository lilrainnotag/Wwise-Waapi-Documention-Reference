# ak.wwise.debug.getWalTree

## 命名空间
ak.wwise.debug

## 状态
正常

## 概述

Retrieves the WAL tree, which describes the nodes that are synchronized in the Sound Engine. Private use only.

## 参数

无参数。

## 参数 Schema

（无）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| return * | object | Result returned by the dump of WAL. |
| return.nodes | object | Nodes in the WALTree. |

\* 表示必填返回字段

## 返回值 Schema

（官网未提供独立 Schema）

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- 仅供内部使用 (Private use only)
- 检索 WAL (Wwise Authoring Language) 树，描述 Sound Engine 中同步的节点
- 无参数调用

## 相关函数

- [ak.wwise.debug.generateToneWAV](ak.wwise.debug.generateToneWAV.md)
- [ak.wwise.debug.testAssert](ak.wwise.debug.testAssert.md)
- [ak.wwise.debug.testCrash](ak.wwise.debug.testCrash.md)
- [ak.wwise.debug.validateCall](ak.wwise.debug.validateCall.md)

## 相关 Topic

- WAL (Wwise Authoring Language)
- Sound Engine
- Using the Wwise Authoring API (WAAPI)

## 官方文档链接

- [ak.wwise.debug.getWalTree](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_debug_getwaltree.html)
