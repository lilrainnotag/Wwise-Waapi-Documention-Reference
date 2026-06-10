# ak.wwise.waapi.getSchema

## ▎ 命名空间: ak.wwise.waapi

## 概述

获取指定 WAAPI URI 的 JSON Schema。这是 WAAPI 自省功能之一，用于在运行时获取函数或 Topic 的参数和返回值结构定义。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| uri * | string | 是 | — | WAAPI URI（参见 `ak.wwise.waapi.getFunctions` 和 `ak.wwise.waapi.getTopics`） |
| includeExamples | boolean | 否 | `false` | 是否在 Schema 中包含示例 |

(* 必填)

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| argsSchema | object | 参数 Schema（仅适用于函数） |
| optionsSchema | object | 选项 Schema |
| resultSchema | object | 返回值 Schema（仅适用于函数） |
| publishSchema | object | 发布 Schema（仅适用于 Topic） |
| description | string | 函数或 Topic 的描述 |
| examples | array | Schema 中提供的示例数组（当 `includeExamples` 为 true 时） |
| examples [...] | object | 示例对象 |

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- `uri` 必须是完整的 WAAPI URI，如 `ak.wwise.core.ping` 或 `ak.wwise.core.object.nameChanged`。
- `includeExamples` 为 true 时会返回示例数据，但可能增加响应体积。
- `argsSchema`、`resultSchema` 返回的是 JSON Schema 格式的结构定义。
- 对于 Topic，只返回 `publishSchema` 和 `optionsSchema`，不返回 `argsSchema` 和 `resultSchema`。

## 相关函数

- [[ak.wwise.waapi.getFunctions]] — 获取所有函数 URI 列表
- [[ak.wwise.waapi.getTopics]] — 获取所有 Topic URI 列表

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.waapi.getSchema](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_waapi_getschema.html)
