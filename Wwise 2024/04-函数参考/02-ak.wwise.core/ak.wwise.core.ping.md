# ak.wwise.core.ping

## ▎ 命名空间: ak.wwise.core

## 概述

验证 WAAPI 当前是否可用。

## 参数

（无参数）

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| isAvailable * | boolean | 指示 WAAPI 是否可用。注意：当显示模态对话框时，WAAPI 不可用。 |

(* 必填)

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.ping",
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {
    "isAvailable": true
  },
  "id": 1
}
```

## 注意事项

- 当 Wwise 显示模态对话框（如设置窗口、错误提示框等）时，WAAPI 不可用，此时调用 ping 会返回 `isAvailable: false`。
- 此函数通常用于健康检查或在执行操作前确认 WAAPI 连接状态。

## 相关函数

- [[ak.wwise.core.getInfo]] — 获取 WAAPI 版本和平台信息

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.ping](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_ping.html)
