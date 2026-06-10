# ak.wwise.waapi.getTopics

## ▎ 命名空间: ak.wwise.waapi

## 概述

获取客户端可以订阅的所有 Topic 列表。这是 WAAPI 自省功能之一，用于在运行时发现可用的发布/订阅通知。

## 参数

（无参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| topics | array | Topic URI 数组 |
| topics [...] | string | 从 Wwise Authoring API Schema 中获取的 Topic URI |

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- 返回的 Topic 列表取决于当前 Wwise 版本和已安装的插件。
- Topic 用于 WAAPI 的发布/订阅模式，客户端可以订阅这些 Topic 来接收实时通知。
- 与 `getFunctions` 类似，这是自省 API 的一部分，用于动态发现系统能力。

## 相关函数

- [[ak.wwise.waapi.getFunctions]] — 获取所有函数 URI 列表
- [[ak.wwise.waapi.getSchema]] — 获取指定 URI 的 Schema

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.waapi.getTopics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_waapi_gettopics.html)
