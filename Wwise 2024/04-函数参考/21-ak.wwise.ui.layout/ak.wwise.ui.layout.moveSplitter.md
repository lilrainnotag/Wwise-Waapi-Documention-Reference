# ak.wwise.ui.layout.moveSplitter

## 命名空间: ak.wwise.ui.layout

## 概述

按给定的像素增量移动分割条（splitter）的位置。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| id | string | 是 | — | 要移动的分割条 ID |
| delta | integer | 是 | — | 分割条位置的像素增量（正值为右/下，负值为左/上） |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无返回值） | — | 成功移动时返回空对象 `{}` |

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.layout.moveSplitter",
  "params": {
    "id": "{AABBCC00-1122-3344-5566-77889900AABB}",
    "delta": 50
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- delta 为正时向右/向下移动分割条，为负时向左/向上移动
- 分割条 ID 可通过布局的 JSON 结构获取（参见 [ak.wwise.ui.layout.getLayout](ak.wwise.ui.layout.getLayout.md)）

## 相关函数

- [ak.wwise.ui.layout.getLayout](ak.wwise.ui.layout.getLayout.md)

## 相关Topic

- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.layout.moveSplitter](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_layout_moveSplitter.html)
