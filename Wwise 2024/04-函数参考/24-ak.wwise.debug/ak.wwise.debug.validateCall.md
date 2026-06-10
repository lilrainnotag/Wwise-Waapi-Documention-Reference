# ak.wwise.debug.validateCall

## 命名空间
ak.wwise.debug

## 状态
正常

## 概述

Validate the arguments, options and result of a WAAPI function call. Does not actually call the function. This is only available with Debug builds.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| id * | string | 是 | — | The ID of the function. |
| args | object | 否 | — | The arguments passed to the function. |
| options | object | 否 | — | The options passed to the function. |
| result | object | 否 | — | The result returned from the function. |

\* 表示必填参数

## 参数 Schema

（官网未提供独立 Schema）

## 返回值

（官网未明确列出返回值）

## 返回值 Schema

（官网未提供）

## JSON-RPC 请求示例

（官网未提供）

## JSON-RPC 响应示例

（官网未提供）

## 注意事项

- 仅用于 Debug 构建版本
- 此函数不会实际调用目标函数，仅验证参数、选项和返回值
- 用于测试和调试 WAAPI 函数调用的参数正确性

## 相关函数

- [ak.wwise.debug.generateToneWAV](ak.wwise.debug.generateToneWAV.md)
- [ak.wwise.debug.getWalTree](ak.wwise.debug.getWalTree.md)
- [ak.wwise.debug.testAssert](ak.wwise.debug.testAssert.md)
- [ak.wwise.debug.testCrash](ak.wwise.debug.testCrash.md)

## 相关 Topic

- Using the Wwise Authoring API (WAAPI)

## 官方文档链接

- [ak.wwise.debug.validateCall](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_debug_validatecall.html)
