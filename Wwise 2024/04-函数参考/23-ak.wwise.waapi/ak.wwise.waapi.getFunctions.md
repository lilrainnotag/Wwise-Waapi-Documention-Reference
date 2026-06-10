# ak.wwise.waapi.getFunctions

## ▎ 命名空间: ak.wwise.waapi

## 概述

获取所有可用函数的列表。这是 WAAPI 自省（Introspection）功能之一，用于在运行时发现可用的 API 函数。

## 参数

（无参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| functions | array | 函数 URI 数组 |
| functions [...] | string | 从 Wwise Authoring API Schema 中获取的函数 URI |

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- 返回的函数列表取决于当前 Wwise 版本和已安装的插件。
- 这是 WAAPI 自省功能的核心函数，可用于动态发现 API 能力。
- 结合 `getSchema` 和 `getTopics` 可以完整了解 WAAPI 的接口。

## 相关函数

- [[ak.wwise.waapi.getSchema]] — 获取 WAAPI Schema
- [[ak.wwise.waapi.getTopics]] — 获取所有 Topic 列表

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.waapi.getFunctions](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_waapi_getfunctions.html)
