# ak.wwise.debug.enableAsserts

## ▎ 命名空间: ak.wwise.debug

## 概述

启用或禁用调试断言（Debug Assertions）。每次调用 `enableAsserts` 并传入 `false` 会增加引用计数，传入 `true` 会减少引用计数。仅适用于 Debug 构建版本。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| enable * | boolean | 是 | — | 指示是否应启用断言。`false` 增加引用计数，`true` 减少引用计数 |

(* 必填)

## 返回值

（无返回值）

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- 使用引用计数机制：多次调用 `enable: false` 需要相应次数的 `enable: true` 才能完全重新启用断言。
- 仅在 Wwise 的 Debug 构建版本中可用，Release 版本中无效。
- 断言失败时会触发 `ak.wwise.debug.assertFailed` Topic。

## 相关函数

- [[ak.wwise.debug.enableAutomationMode]] — 启用自动化模式

## 相关Topic

- ak.wwise.debug.assertFailed

## 官方文档链接

- [ak.wwise.debug.enableAsserts](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_debug_enableasserts.html)
