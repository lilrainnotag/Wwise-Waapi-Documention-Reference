# ak.soundengine.setState

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetState`

## 概述

Sets the State of a State Group. See AK::SoundEngine::SetState.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| stateGroup | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or Short ID of the State Group. |
| state | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or Short ID of the State. |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setState",
  "params": {
    "stateGroup": "MyStateGroup",
    "state": "MyState"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `stateGroup` 和 `state` 均支持三种形式：名称字符串、GUID字符串、Short ID整数
- 使用 `setState` 后如需立即获取状态，调用 `getState` 前应允许短暂延迟（不超过10ms）

## 相关函数

- [ak.soundengine.setSwitch](ak.soundengine.setSwitch.md)
- [ak.soundengine.getState](ak.soundengine.getState.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setState.html
