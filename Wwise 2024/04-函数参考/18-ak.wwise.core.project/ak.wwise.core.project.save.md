# ak.wwise.core.project.save

## ▎ 命名空间: ak.wwise.core.project

## 概述

保存当前打开的 Wwise 项目。此操作会保存项目文件（.wproj）以及所有已修改的 Work Unit 文件。

## 参数

（无参数）

## 返回值

（无返回值）

## JSON-RPC 请求示例

```json
{
  "jsonrpc": "2.0",
  "method": "ak.wwise.core.project.save",
  "params": {},
  "id": 1
}
```

## JSON-RPC 响应示例

```json
{
  "jsonrpc": "2.0",
  "result": {},
  "id": 1
}
```

## 注意事项

- 此函数保存整个项目，包括所有已修改但未保存的 Work Unit。
- 如果项目没有未保存的更改，调用此函数不会产生任何效果。
- 保存操作可能会触发 Source Control 操作（如果已配置）。
- 可以通过 `ak.wwise.core.getProjectInfo` 的 `isDirty` 字段检查是否有未保存的更改。

## 相关函数

- [[ak.wwise.core.getProjectInfo]] — 获取项目信息（含 isDirty 状态）

## 相关Topic

（无）

## 官方文档链接

- [ak.wwise.core.project.save](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_project_save.html)
