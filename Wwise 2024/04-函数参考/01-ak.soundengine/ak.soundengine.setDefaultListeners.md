# ak.soundengine.setDefaultListeners

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::SetDefaultListeners`

## 概述

Sets the default active listeners for all subsequent game objects that are registered. See AK::SoundEngine::SetDefaultListeners.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| listeners | array of integer | 是 | （无） | Array of listener game object IDs. Game objects must have been previously registered. listeners [...] integer: A game object ID, unsigned integer 64-bit. Range: [0,18446744073709551615] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.setDefaultListeners",
  "params": {
    "listeners": [1, 2]
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- 设置的默认监听器将应用于之后注册的所有游戏对象
- 监听器游戏对象必须事先通过 `registerGameObj` 注册

## 相关函数

- [ak.soundengine.setListeners](ak.soundengine.setListeners.md)
- [ak.soundengine.registerGameObj](ak.soundengine.registerGameObj.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_setDefaultListeners.html
