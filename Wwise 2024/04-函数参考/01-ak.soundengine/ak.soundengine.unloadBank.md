# ak.soundengine.unloadBank

▎ **命名空间**: `ak.soundengine`
▎ **对应C++ API**: `AK::SoundEngine::UnloadBank`

## 概述

Unload a SoundBank. See AK::SoundEngine::UnloadBank.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| soundBank | any of: string (name), string (GUID), integer (Short ID) | 是 | （无） | Either the ID (GUID), name, or Short ID of the SoundBank. string: The name of the object. string: An object GUID of the form: {aabbcc00-1122-3344-5566-77889900aabb}. integer: The Short ID of a Wwise Object. Unsigned Integer 32-bit. Range: [0,4294967295] |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | {} | 成功时返回空对象 |

## JSON-RPC 请求示例

```json
{
  "method": "ak.soundengine.unloadBank",
  "params": {
    "soundBank": "{aabbcc00-1122-3344-5566-77889900aabb}"
  }
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `soundBank` 参数为必填，支持三种形式：名称字符串、GUID字符串、Short ID整数
- 卸载 SoundBank 会释放其占用的内存资源
- 与 `loadBank` 配对使用

## 相关函数

- [ak.soundengine.loadBank](ak.soundengine.loadBank.md)

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_soundengine_unloadBank.html
