# ak.wwise.ui.getSelectedObjects

## 命名空间: ak.wwise.ui

## 概述

获取当前活动视图中用户所选对象的列表。可以通过 return 选项指定要返回的对象属性。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | id, name | 指定每个对象返回的数据。可包含内置访问器（如 id、name）或对象属性（如 Volume、Pitch）。支持 `@` 取值和 `@@` 获取覆盖源属性值 |
| platform | string (GUID) 或 string (name) | 否 | 当前平台 | 平台的 ID (GUID) 或名称 |
| language | string (GUID) 或 string (name) | 否 | 当前语言 | 语言的 ID (GUID) 或名称 |

**常用 return 内置访问器值：**
`id`, `name`, `notes`, `type`, `pluginName`, `shortId`, `classId`, `category`, `filePath`, `workunit`, `parent`, `owner`, `path`, `isPlayable`, `childrenCount`, `totalSize`, `mediaSize`, `objectSize`, `structureSize`, `sound:convertedWemFilePath`, `sound:originalWavFilePath`, `soundbank:bnkFilePath`

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| objects | array | 选中的对象列表，格式由 options 指定。若未选中任何对象则为空数组 |
| objects[].id | string | 对象的 ID (GUID)，格式如 `{aabbcc00-1122-3344-5566-77889900aabb}` |
| objects[].name | string | 对象的名称 |

（更多返回字段取决于 return 选项中指定的访问器）

## JSON-RPC 请求示例

```json
{
  "method": "ak.wwise.ui.getSelectedObjects",
  "params": {}
}
```

## JSON-RPC 响应示例

```json
{
  "objects": [
    {
      "id": "{A076AA65-B71A-45BB-8841-5A20C52CE727}",
      "name": "MySound"
    }
  ]
}
```

## 注意事项

- 若未选中任何对象，返回的 objects 数组为空
- 可以通过 return 选项自定义返回的属性，支持 Wwise 对象引用中所有可用的属性和引用
- 支持 `@` 前缀获取属性值，`@@` 前缀获取覆盖源属性值

## 相关函数

- [ak.wwise.core.object.get]()

## 相关Topic

- [Wwise Objects Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wobjects_index.html)
- [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=goingfurther_waapi.html)

## 官方文档链接

- [ak.wwise.ui.getSelectedObjects](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_ui_getSelectedObjects.html)
