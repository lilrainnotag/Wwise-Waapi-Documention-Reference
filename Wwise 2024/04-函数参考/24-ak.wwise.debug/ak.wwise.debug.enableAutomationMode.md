# ak.wwise.debug.enableAutomationMode

## ▎ 命名空间: ak.wwise.debug

## 概述

启用或禁用 Wwise 的自动化模式。此模式可减少由消息框和对话框引起的潜在中断。例如，启用自动化模式后会静默接受：项目迁移、项目加载日志、EULA 接受、项目许可显示以及通用消息框。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| enable * | boolean | 是 | — | 设为 `true` 时，自动化模式减少对话框和弹窗的阻塞；设为 `false` 时恢复为正常模式 |

(* 必填)

## 返回值

（无返回值）

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.debug.enableAutomationMode",
  "params": {
    "enable": true
  },
  }
```

## JSON-RPC 响应示例

```json
{}
  }
```

## 注意事项

- 自动化模式对于无人值守的自动化测试和 CI/CD 流程非常有用。
- 启用后会自动处理以下对话框：项目迁移确认、项目加载日志、EULA 接受、项目许可信息、通用消息框等。
- 这不影响 Source Control 相关的对话框。

## 相关函数

- [[ak.wwise.debug.enableAsserts]] — 启用/禁用调试断言

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.debug.enableAutomationMode](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_debug_enableautomationmode.html)
