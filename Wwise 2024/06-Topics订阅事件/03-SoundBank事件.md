# SoundBank 事件

## 订阅机制

`ak.wwise.core.soundbank.*` 系列 Topic 用于监听 SoundBank 的生成过程。在 SoundBank 生成期间，每个 SoundBank 的每个平台生成完成时都会单独发送通知，全部完成后发送总完成通知。

---

## 事件列表

### ak.wwise.core.soundbank.generated

- **触发时机**：当单个 SoundBank 生成完成时发送。在 SoundBank 生成过程中，每个 SoundBank 的每个平台生成完成时都会触发一次，因此可能会触发多次
- **Options**：

| 名称 | 类型 | 说明 |
|------|------|------|
| infoFile | boolean | 是否在响应中嵌入 JSON SoundBank info 文件 |
| bankData | boolean | 是否在响应中嵌入 base64 编码的 SoundBank 数据 |
| pluginInfo | boolean | 是否在响应中嵌入 JSON PluginInfo 文件 |
| return | array | 要返回的数据字段列表 |

- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| soundbank * | object | 生成完成的 SoundBank 对象。使用 return 选项指定返回的属性 |
| soundbank.id | string | SoundBank 对象的 GUID |
| soundbank.name | string | SoundBank 的名称 |
| soundbank.type | string | 对象类型（通常为 "SoundBank"） |
| soundbank.path | string | SoundBank 的工程路径 |
| soundbank.soundbankBnkFilePath | string | 生成的 .bnk 文件绝对路径（仅限 SoundBank 对象） |
| platform | string | （官网提供）生成对应的平台 GUID |
| infoFile | object | （当 `infoFile: true` 时）JSON SoundBank info 文件内容 |
| bankData | string | （当 `bankData: true` 时）base64 编码的 SoundBank 数据 |
| pluginInfo | object | （当 `pluginInfo: true` 时）JSON PluginInfo 文件内容 |

- **WAMP 订阅示例**：

```python
from waapi import WaapiClient

client = WaapiClient()

def on_soundbank_generated(channel, **kwargs):
    sb = kwargs.get("soundbank", {})
    print(f"SoundBank 生成完成: {sb.get('name')} (ID: {sb.get('id')})")

sub_id = client.subscribe(
    "ak.wwise.core.soundbank.generated",
    options={"return": ["id", "name", "soundbankBnkFilePath"]},
    callback=on_soundbank_generated
)
```

- **注意事项**：
  - 每次 SoundBank 生成期间此事件可能触发**多次**（每个 SoundBank × 每个平台各一次）
  - 生成大量 SoundBank 时回调会被频繁调用，注意回调函数的性能
  - `bankData` 选项会使响应体积显著增大（包含整个 SoundBank 的 base64 数据）
  - SoundBank 生成命令参考：`ak.wwise.core.soundbank.generate` 或 `ak.wwise.ui.commands.execute` 配合 SoundBank 生成命令 ID

---

### ak.wwise.core.soundbank.generationDone

- **触发时机**：当所有 SoundBank 全部生成完成后发送
- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| （无特殊返回数据） | — | 此 Topic 为流程完成通知（官网未提供详细 Publish Schema） |

- **WAMP 订阅示例**：

```python
def on_generation_done(channel, **kwargs):
    print("所有 SoundBank 生成完毕！")

sub_id = client.subscribe(
    "ak.wwise.core.soundbank.generationDone",
    callback=on_generation_done
)
```

- **注意事项**：
  - ⚠️ **重要**：此通知**仅在** SoundBank 确实被生成时才发送。如果生成过程中没有任何 SoundBank 需要更新，此事件**不会被触发**
  - **不能**作为判断 `ak.wwise.core.soundbank.generate` 是否完成的可靠方式
  - 建议配合 `generated` 事件一起使用，或通过 RPC 调用的返回值来判断生成操作是否完成

---

## SoundBank 生成流程示意

```
ak.wwise.core.soundbank.generate（RPC 调用）
  │
  ├── soundbank.generated（SoundBank A, Platform X）
  ├── soundbank.generated（SoundBank A, Platform Y）
  ├── soundbank.generated（SoundBank B, Platform X）
  ├── soundbank.generated（SoundBank B, Platform Y）
  │   ...
  └── soundbank.generationDone（所有完成）
```

## 官方文档链接

- [ak.wwise.core.soundbank.generated](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_generated.html)
- [ak.wwise.core.soundbank.generationDone](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_generationdone.html)
