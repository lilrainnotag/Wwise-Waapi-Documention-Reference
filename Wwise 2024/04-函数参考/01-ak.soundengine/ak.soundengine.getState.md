# ak.soundengine.getState

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::GetState`

## 概述

Gets the current state of a State Group. When using setState just prior to getState, allow a brief delay (no more than 10ms) for the information to update in the sound engine.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| stateGroup | any of: string (qualified name), string (GUID), string (path) | 是 | （无） | Either the ID (GUID), unique qualified name, or path of the State Group. string: The name of the object qualified by its type or Short ID in the form of type:name or Global:shortId. Ex: Event:Play_Sound_01, Global:245489792. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. string: A project path to a Wwise object, including the category and the work-unit. For example: \Actor-Mixer Hierarchy\Default Work Unit\New Sound SFX. |

## 选项（Options）

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| return | array | 否 | （官网未提供） | Specifies what is being returned for every object. Refer to Wwise Objects Reference for more information on the properties and references available. |
| return [...] | any of: string | 否 | （官网未提供） | Specifies built-in accessors for Wwise objects (id, name, notes, type, pluginName, shortId, classId, category, filePath, workunit, parent, owner, path, isPlayable, childrenCount, totalSize, mediaSize, objectSize, structureSize, 等) or dot-separated property accessors. |
| platform | any of: string (name), string (GUID) | 否 | current platform | The ID (GUID) or name of the platform. |
| language | any of: string (name), string (GUID) | 否 | （官网未提供） | The ID (GUID) or name of the language. |

## 返回值（Result）

返回一个 Wwise 对象的标准属性集合，包含 id, name, notes, type, path, parent, owner 等完整的对象信息。具体返回字段由 Options 中的 `return` 参数决定。

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.getState",
  "params": {
    "stateGroup": "{aabbcc00-1122-3344-5566-77889900aabb}"
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
  "name": "MyState",
  "type": "State"
}
```

## 注意事项

- 使用 `setState` 后立即调用 `getState` 时，需允许短暂延迟（不超过 10ms）以便信息在声音引擎中更新
- `stateGroup` 支持三种形式：GUID字符串、类型限定名（如 `StateGroup:MyGroup`）、项目路径
- 返回值为标准 Wwise 对象属性，可通过 `return` 选项指定需要的字段

## 相关函数

- [ak.soundengine.getSwitch](ak.soundengine.getSwitch.md)
- [ak.soundengine.setState](ak.soundengine.setState.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_getState.html
