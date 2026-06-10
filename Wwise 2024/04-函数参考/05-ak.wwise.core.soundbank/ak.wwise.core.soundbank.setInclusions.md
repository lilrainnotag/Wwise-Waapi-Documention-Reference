# ak.wwise.core.soundbank.setInclusions

▎ **命名空间**: ak.wwise.core.soundbank

## 概述

Modifies a SoundBank's inclusion list. The 'operation' argument determines how the 'inclusions' argument modifies the SoundBank's inclusion list; 'inclusions' may be added to / removed from / replace the SoundBank's inclusion list.

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| soundbank | string (name/GUID/path) | 是 | — | The ID (GUID), name, or path of the SoundBank. 支持格式：type:name、Global:shortId、{GUID}、或工程路径。 |
| operation | string | 是 | — | Determines how the 'inclusions' argument is used to modify the SoundBank's inclusion list. 可选值：add（添加）、remove（移除）、replace（替换）。 |
| inclusions | array | 是 | — | An array of SoundBank inclusions. |
| inclusions[...] | object | — | — | A SoundBank inclusion. |
| inclusions[...].object | string (name/GUID/path) | 是 | — | The ID (GUID), name, or path of the object to add to / remove from the SoundBank's inclusion list. |
| inclusions[...].filter | array | 是 | — | An array of inclusion types defining what to include. 可选值：events、structures、media。 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| （无） | — | 返回空对象 {} |

## JSON-RPC 请求示例

### 示例 1：向 inclusion 列表添加对象

```json
{
    "soundbank": "{A076AA65-B71A-45BB-8841-5A20C52CE727}",
    "operation": "add",
    "inclusions": [
        {
            "object": "{AAAAAAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE}",
            "filter": [
                "events",
                "structures"
            ]
        }
    ]
}
```

### 示例 2：清空 inclusion 列表（官网提供）

使用 `operation: "replace"` 并传入空的 inclusions 数组来清空列表：
```json
{
    "soundbank": "{A076AA65-B71A-45BB-8841-5A20C52CE727}",
    "operation": "replace",
    "inclusions": []
}
```

## JSON-RPC 响应示例

```json
{}
```

## 注意事项

- `operation` 的三种模式：
  - `add`：将 inclusions 中的对象添加到现有列表
  - `remove`：从现有列表中移除 inclusions 中指定的对象
  - `replace`：用 inclusions 完全替换现有列表（传入空数组可清空）
- `filter` 可选值：`events`（包含事件）、`structures`（包含结构）、`media`（包含媒体）。

## 相关函数

- ak.wwise.core.soundbank.getInclusions

## 相关 Topic

- SoundBank inclusion

## 官方文档链接

https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_setinclusions.html
