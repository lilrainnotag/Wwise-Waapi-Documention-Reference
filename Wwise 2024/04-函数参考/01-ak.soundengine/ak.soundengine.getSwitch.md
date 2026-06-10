# ak.soundengine.getSwitch

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::GetSwitch`

## 概述

Gets the current state of a Switch Group for a given Game Object.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| switchGroup | any of: string (qualified name), string (GUID), string (path) | 是 | （无） | Either the ID (GUID), unique qualified name, or path of the Switch Group. string: The name of the object qualified by its type or Short ID in the form of type:name or Global:shortId. Ex: Event:Play_Sound_01, Global:245489792. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. string: A project path to a Wwise object, including the category and the work-unit. For example: \Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX. |
| gameObject | integer | 否 | （官网未提供） | The unique ID of the game object. A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 选项（Options）

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | （官网未提供） | Specifies what is being returned for every object. 可指定内置访问器（id, name, notes, type, path 等）或属性访问器表达式。 |
| platform | any of: string (name), string (GUID) | 否 | current platform | The ID (GUID) or name of the platform. |
| language | any of: string (name), string (GUID) | 否 | （官网未提供） | The ID (GUID) or name of the language. |

## 返回值（Result）

返回一个 Wwise 对象的标准属性集合（id, name, notes, type, path, parent, owner 等）。具体返回字段由 Options 中的 `return` 参数决定。

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.getSwitch",
  "params": {
    "switchGroup": "{aabbcc00-1122-3344-5566-77889900aabb}",
    "gameObject": 1
  },
  "options": {
    "return": ["id", "name", "type"]
  }
}
```

## JSON-RPC 响应示例

```json
{
  "id": "{aabbcc00-1122-3344-5566-77889900aabb}",
  "name": "MySwitch",
  "type": "Switch"
}
```

## 注意事项

- `switchGroup` 参数为必填，支持 GUID、类型限定名、项目路径三种形式
- `gameObject` 参数为可选，指定要查询的游戏对象 ID
- 返回值为标准 Wwise 对象属性，可通过 `return` 选项指定需要的字段

## 相关函数

- [ak.soundengine.getState](ak.soundengine.getState.md)
- [ak.soundengine.setSwitch](ak.soundengine.setSwitch.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_getSwitch.html
