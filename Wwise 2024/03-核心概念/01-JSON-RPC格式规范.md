# 01-JSON-RPC 格式规范

## JSON-RPC 2.0 标准简介

WAAPI 使用类 JSON-RPC 2.0 的协议进行远程过程调用。JSON-RPC 2.0 是一种轻量级、无状态的 RPC 协议，使用 JSON 作为数据格式。

WAAPI 通过两种传输协议暴露 JSON-RPC 接口：

| 协议 | 默认端口 | 特性 |
|------|---------|------|
| **WAMP** (WebSocket) | 8080 | 支持 RPC + 发布/订阅，双向通信，性能最优 |
| **HTTP POST** | 8090 | 仅支持 RPC 调用，单向请求/响应 |

> **注**：WAAPI 也支持在 Wwise 插件内通过 `AK::Wwise::Plugin::Host::WaapiCall()` 直接调用。

### 连接限制
- WAMP 最大并发连接数：**20**
- HTTP POST 最大并发连接数：**20**

## WAAPI 请求格式

### 标准 JSON-RPC 请求结构

```json
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "ak.wwise.core.object.get",
    "params": {
        "waql": "\"{24979032-B170-43E3-A2E4-469E0193E2C3}\"",
        "return": ["name"]
    }
}
```

### 字段说明

| 字段 | 类型 | 必需 | 说明 |
|------|------|------|------|
| `id` | number/string/null | 是 | 请求标识符，用于匹配响应。客户端应保证唯一性。`null` 表示通知（无需响应） |
| `jsonrpc` | string | 是 | 固定值 `"2.0"` |
| `method` | string | 是 | 要调用的 WAAPI 函数 URI，如 `ak.wwise.core.object.get` |
| `params` | object | 否 | 函数参数对象，结构因函数而异 |

### 官方示例

来自 Audiokinetic 官网 `ak.wwise.core.object.get` 文档：

**Arguments (请求参数):**
```json
{
    "waql": "\"{24979032-B170-43E3-A2E4-469E0193E2C3}\""
}
```

**Options (选项，合并到 params 中):**
```json
{
    "return": ["name"]
}
```

**完整请求:**
```json
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "ak.wwise.core.object.get",
    "params": {
        "waql": "\"{24979032-B170-43E3-A2E4-469E0193E2C3}\"",
        "return": ["name"]
    }
}
```

## WAAPI 响应格式

### 成功响应

```json
{
    "id": 1,
    "jsonrpc": "2.0",
    "result": {
        "return": [
            {
                "name": "MyObjectName"
            }
        ]
    }
}
```

**字段说明：**

| 字段 | 类型 | 说明 |
|------|------|------|
| `id` | number | 与请求中的 `id` 相匹配 |
| `jsonrpc` | string | 固定值 `"2.0"` |
| `result` | object | 函数执行结果，结构因函数而异 |

### 错误响应

```json
{
    "id": 1,
    "jsonrpc": "2.0",
    "error": {
        "code": -32602,
        "message": "Invalid params",
        "data": "The parameter 'waql' is required"
    }
}
```

**error 对象字段说明：**

| 字段 | 类型 | 说明 |
|------|------|------|
| `code` | integer | 错误码 |
| `message` | string | 错误简短描述 |
| `data` | any | 可选的附加错误信息，可能包含具体的参数名、对象路径等调试信息 |

## params 的常见结构模式

### 1. 单对象操作

用于对单个 Wwise 对象执行操作，如设置属性、获取信息等。

```json
{
    "object": "{24979032-B170-43E3-A2E4-469E0193E2C3}",
    "property": "Volume",
    "value": -6.0,
    "platform": "{66666666-7777-8888-9999-AAAAAAAAAAAA}"
}
```

常见于以下函数：
- `ak.wwise.core.object.setProperty` — 设置对象属性
- `ak.wwise.core.object.isLinked` — 检查属性是否 Link
- `ak.wwise.core.object.setLinked` — 设置属性 Link/Unlink
- `ak.wwise.core.object.setName` — 重命名对象
- `ak.wwise.core.object.setNotes` — 设置对象备注

`object` 字段支持三种格式：
- **GUID**: `"{aabbcc00-1122-3344-5566-77889900aabb}"`
- **类型限定名**: `"Event:Play_Sound_01"` 或 `"Global:245489792"`
- **路径**: `"\\Actor-Mixer Hierarchy\\Default Work Unit\\New Sound SFX"`

### 2. 查询操作 (ak.wwise.core.object.get)

用于查询 Wwise 工程中的对象和数据。

```json
{
    "waql": "$ from type Sound where name:matches /^Footstep/",
    "return": ["id", "name", "Volume", "OutputBus.name", "parent.name"],
    "platform": "{66666666-7777-8888-9999-AAAAAAAAAAAA}",
    "language": "English(US)"
}
```

查询参数说明：

| 参数 | 类型 | 必需 | 说明 |
|------|------|------|------|
| `waql` | string | 是(推荐) | WAQL 查询语句。推荐使用 WAQL 而非 `from` |
| `from` | object | 是(旧) | (**已弃用**) JSON 格式的查询起点，推荐使用 `waql` 代替 |
| `transform` | array | 否 | 对查询结果的转换链（select, where, range, distinct） |
| `return` | array | 否 | 指定返回的字段，默认 `["id", "name"]` |
| `platform` | string | 否 | 平台 GUID 或名称，不指定则使用当前平台 |
| `language` | string | 否 | 语言 GUID 或名称，不指定则使用当前语言 |

### 3. 批量操作 (ak.wwise.core.object.set)

用于批量创建/修改对象及层次结构。

```json
{
    "objects": [
        {
            "object": "\\Actor-Mixer Hierarchy\\Default Work Unit",
            "onNameConflict": "merge",
            "children": [
                {
                    "type": "ActorMixer",
                    "name": "FootSteps",
                    "@Volume": -2,
                    "children": [
                        {
                            "type": "RandomSequenceContainer",
                            "name": "FootStep_Concrete",
                            "@RandomOrSequence": 1,
                            "children": [
                                {
                                    "type": "Sound",
                                    "name": "FootStep_Concrete_01",
                                    "import": {
                                        "files": [
                                            {
                                                "audioFile": "C:\\wave\\cues\\FootStep_Concrete_01.wav"
                                            }
                                        ]
                                    }
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ],
    "onNameConflict": "fail",
    "listMode": "append"
}
```

批量操作参数说明：

| 参数 | 类型 | 说明 |
|------|------|------|
| `objects` | array | 要创建/修改的对象层次结构数组 |
| `objects[].object` | string | 目标父对象的 GUID/名称/路径 |
| `objects[].type` | string | 新对象的类型（如 `ActorMixer`, `Sound`, `RandomSequenceContainer`） |
| `objects[].name` | string | 对象名称 |
| `objects[].children` | array | 子对象数组（递归结构） |
| `objects[].import` | object | 音频文件导入配置 |
| `onNameConflict` | string | 名称冲突处理模式：`fail`(默认), `replace`, `rename`, `merge` |
| `listMode` | string | 列表操作模式：`append`(默认), `replaceAll` |

名称冲突模式（`onNameConflict`）说明：
- **fail**: 返回错误（默认行为）
- **replace**: 删除目标位置已有对象（含子对象）并创建新对象
- **rename**: 自动分配唯一名称（追加数字后缀）
- **merge**: 复用目标位置已有对象，合并属性、引用和子对象

列表操作模式（`listMode`）说明：
- **append**: 添加新对象到列表，保留已有对象
- **replaceAll**: 清除已有对象并添加新对象

## WAMP 调用格式

使用 WAMP 协议时，不同语言的 WAAPI 客户端库会封装调用细节。以 Python `waapi-client` 为例：

```python
from waapi import WaapiClient

client = WaapiClient()

# Arguments 和 Options 分别传递
args = {
    "waql": "\"\\Actor-Mixer Hierarchy\" select descendants where name = /^My/"
}

options = {
    "return": ["name", "id"]
}

result = client.call("ak.wwise.core.object.get", args, options=options)
print(result)

client.disconnect()
```

WAMP 底层通过 WebSocket 发送序列化的调用消息，WAAPI 客户端库会自动处理连接管理、序列化和错误处理。

## HTTP POST 调用格式

使用 HTTP POST 协议时，直接发送 JSON-RPC 2.0 格式的 JSON body：

```http
POST http://localhost:8090/waapi HTTP/1.1
Content-Type: application/json

{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "ak.wwise.core.object.get",
    "params": {
        "waql": "\"\\Actor-Mixer Hierarchy\" select descendants where name = /^My/",
        "return": ["name", "id"]
    }
}
```

响应：

```json
{
    "id": 1,
    "jsonrpc": "2.0",
    "result": {
        "return": [
            {"name": "MySound", "id": "{AABBCC00-1122-3344-5566-77889900AABB}"}
        ]
    }
}
```

## 批量调用 vs 单次调用

JSON-RPC 2.0 规范支持两种批量调用模式：

### JSON-RPC 批量请求（数组形式）

将多个请求放入一个 JSON 数组中，一次性发送：

```json
[
    {
        "id": 1,
        "jsonrpc": "2.0",
        "method": "ak.wwise.core.object.get",
        "params": {"waql": "$ from type Sound", "return": ["name"]}
    },
    {
        "id": 2,
        "jsonrpc": "2.0",
        "method": "ak.wwise.core.object.get",
        "params": {"waql": "$ from type Event", "return": ["name"]}
    }
]
```

> **注意**：JSON-RPC 批量请求在 WAAPI 中的支持情况取决于具体实现，建议测试确认。

### WAAPI 内置批量操作

部分函数原生支持批量操作，性能优于多次单独调用：

- **`ak.wwise.core.object.set`**: 一次调用创建/修改多个对象及其层次结构
- **`ak.wwise.core.object.get`**: 通过 WAQL 查询一次获取多个对象
- **`ak.wwise.core.object.delete`**: 支持批量删除对象

## id 管理最佳实践

1. **使用递增整数**: 简单且易于追踪，如 `1, 2, 3...`
2. **使用 UUID**: 适用于多客户端场景，避免冲突
3. **避免重复**: 每个请求应有唯一 `id`，否则响应对应有歧义
4. **`null` 通知**: 如果不需要响应（fire-and-forget），设置 `id` 为 `null`

## Mac 路径注意事项

在 Mac 上使用 WAAPI 时，需要使用 Windows 风格的路径：
- 根目录 `/` 映射为驱动器 `Z:`
- Home 目录映射为驱动器 `Y:`
- 例如：`/Volumes/path/to/MyProject.wproj` → `Z:\Volumes\path\to\MyProject.wproj`

## 参考来源

- Audiokinetic 官方文档：Getting Started with the Wwise Authoring API (WAAPI)
- Audiokinetic 官方文档：ak.wwise.core.object.get 参考页
- Audiokinetic 官方文档：Querying the Wwise Project
- Audiokinetic 官方文档：Importing Audio Files and Creating Structures
