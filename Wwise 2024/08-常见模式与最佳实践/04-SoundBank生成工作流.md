# 04 - SoundBank 生成工作流

> **数据来源**: Audiokinetic 官方文档 — [ak.wwise.core.soundbank.generate](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_generate.html)

## 场景描述

SoundBank 生成是音频资产管线的最后一步，将 Wwise 工程中的 Event、结构和媒体文件打包为游戏运行时可加载的 `.bnk` 文件。WAAPI 提供 `ak.wwise.core.soundbank.generate` 来实现完全自动化的 SoundBank 生成，支持：

- ✅ 指定特定 SoundBank 或生成全部
- ✅ 多平台并行生成
- ✅ 多语言本地化生成
- ✅ 写入磁盘或返回 Base64 数据（内存中）
- ✅ 强制重建、清除缓存等构建控制
- ✅ 动态指定 SoundBank 包含的 Event 和 AuxBus

> **官方说明**: "Generate a list of SoundBanks with the import definition specified in the WAAPI request. If you do not write the SoundBanks to disk, subscribe to ak.wwise.core.soundbank.generated to receive SoundBank structure info and the bank data as base64. Note: This is a synchronous operation."

---

## 核心 API 调用链

```
1. 连接 WAAPI → WaapiClient()
2. (可选) 设置 SoundBank 包含对象 → ak.wwise.core.soundbank.setInclusions
3. 调用 ak.wwise.core.soundbank.generate(args)
4. 检查生成日志中的错误
5. (可选) 订阅 ak.wwise.core.soundbank.generated 获取生成数据
6. 断开连接 → client.disconnect()
```

---

## 参数详解（来源：官方 Schema）

### 顶层参数

| 参数 | 类型 | 必需 | 说明 |
|------|------|------|------|
| `soundbanks` | array | — | 要生成的用户定义 SoundBank 列表。空数组表示生成所有。Auto-defined SoundBank 无法指定，但始终会被生成 |
| `platforms` | array | — | 目标平台 GUID 或名称列表。不指定则生成所有平台 |
| `languages` | array | — | 目标语言 GUID 或名称列表。不指定则生成所有语言 |
| `skipLanguages` | boolean | — | 设为 `true` 跳过所有本地化 SoundBank 生成。默认 `false` |
| `rebuildSoundBanks` | boolean | — | 强制重建所有 SoundBank。默认 `false` |
| `clearAudioFileCache` | boolean | — | 生成前清除音频文件缓存（所有平台），确保所有源文件重新转码。默认 `false` |
| `writeToDisk` | boolean | — | 使用正常生成流程将 SoundBank 写入磁盘。默认 `false` |
| `rebuildInitBank` | boolean | — | 强制重建指定平台的 Init bank |

### soundbanks[]. 子参数

| 参数 | 类型 | 必需 | 说明 |
|------|------|------|------|
| `name` | string | ✅ | 要生成的用户定义 SoundBank 名称。如不存在会创建临时 SoundBank |
| `events` | array | — | 要包含的 Event 列表（GUID、名称如 `Event:Play_Sound_01`、或路径） |
| `auxBusses` | array | — | 要包含的 Auxiliary Bus 列表 |
| `inclusions` | array | — | 包含类型：`events`、`structure`、`media` |
| `rebuild` | boolean | — | 强制重建该特定 SoundBank。默认 `false` |

---

### 返回结果

```json
{
  "logs": [
    {
      "severity": "Message",
      "time": 1700000000,
      "messageId": "MSG_ID_STRING",
      "message": "Bank MyBank generated successfully.",
      "platform": {
        "id": "{GUID}",
        "name": "Windows"
      }
    }
  ]
}
```

日志严重级别：`Message`、`Warning`、`Error`、`Fatal Error`

---

## 完整 Python 示例

### 示例 1：生成所有现有 SoundBank 到磁盘（多平台）

> 基于官方 Schema 和示例标题 "Generating several existing SoundBanks without writing them to disk" 改写

```python
from waapi import WaapiClient
import json

client = WaapiClient()

# 生成所有用户定义的 SoundBank
args = {
    "soundbanks": [],                    # 空数组 = 生成所有
    "platforms": ["Windows", "Mac"],     # 指定平台
    "languages": ["English(US)"],        # 指定语言
    "writeToDisk": True,                 # 写入磁盘
    "rebuildSoundBanks": False,          # 不强制重建（增量构建）
    "clearAudioFileCache": False
}

result = client.call("ak.wwise.core.soundbank.generate", args)

# 检查生成日志
has_errors = False
for log_entry in result.get("logs", []):
    severity = log_entry.get("severity", "")
    message = log_entry.get("message", "")
    platform_name = log_entry.get("platform", {}).get("name", "")

    if severity in ("Error", "Fatal Error"):
        has_errors = True
        print(f"[{severity}] [{platform_name}] {message}")
    elif severity == "Warning":
        print(f"[WARNING] [{platform_name}] {message}")
    else:
        print(f"[INFO] [{platform_name}] {message}")

if has_errors:
    print("SoundBank 生成过程中发生错误！")
else:
    print("SoundBank 生成成功！")

client.disconnect()
```

---

### 示例 2：生成新 SoundBank（动态指定包含内容）

> 基于官方示例标题 "Generating a new SoundBank by specifying inclusions" 改写

```python
from waapi import WaapiClient
import json

client = WaapiClient()

# 动态创建 SoundBank 并指定包含的 Event
args = {
    "soundbanks": [
        {
            "name": "UI_SoundBank",
            "events": [
                "Event:Play_UI_Click",
                "Event:Play_UI_Hover",
                "\\Events\\Default Work Unit\\Play_UI_Confirm"
            ],
            "inclusions": ["events", "structure", "media"],
            "rebuild": True
        },
        {
            "name": "Footstep_SoundBank",
            "events": [
                "Event:Play_FootStep_Concrete",
                "Event:Play_FootStep_Wood"
            ],
            "inclusions": ["events", "structure", "media"]
        }
    ],
    "platforms": ["Windows"],
    "languages": ["English(US)", "French(France)"],
    "writeToDisk": True
}

result = client.call("ak.wwise.core.soundbank.generate", args)

print(f"生成完成，共 {len(result.get('logs', []))} 条日志")
client.disconnect()
```

> ⚠️ **注意**: `name` 字段为必需参数。如果指定的 SoundBank 不存在，Wwise 会创建一个临时的 SoundBank。Auto-defined SoundBank 不能通过此参数指定。

---

### 示例 3：生成 SoundBank 返回 Base64 数据（不写盘）

> 基于官方示例标题 "Generating several existing SoundBanks without writing them to disk" 和官方说明改写

```python
from waapi import WaapiClient
import json

client = WaapiClient()

# 先订阅生成完成事件以获取 Base64 数据
subscription_id = None

def on_soundbank_generated(*args, **kwargs):
    """处理生成的 SoundBank 数据"""
    print("收到 SoundBank 生成数据:")
    print(json.dumps(kwargs, indent=2))

try:
    # 订阅 ak.wwise.core.soundbank.generated 主题
    subscription_id = client.subscribe(
        "ak.wwise.core.soundbank.generated",
        on_soundbank_generated
    )

    # 生成 SoundBank（不写盘，通过订阅获取 Base64）
    args = {
        "soundbanks": [
            {
                "name": "MyBank",
                "events": ["Event:Play_Sound_01"]
            }
        ],
        "platforms": ["Windows"],
        "writeToDisk": False,       # 不写盘
        "rebuildSoundBanks": True
    }

    result = client.call("ak.wwise.core.soundbank.generate", args)

    # 检查日志
    for log_entry in result.get("logs", []):
        if log_entry.get("severity") in ("Error", "Fatal Error"):
            print(f"生成失败: {log_entry.get('message')}")

finally:
    if subscription_id:
        client.unsubscribe(subscription_id)

client.disconnect()
```

---

### 示例 4：全平台 + 全语言 CI/CD 构建脚本

```python
from waapi import WaapiClient
import sys

client = WaapiClient()

def generate_all_soundbanks(project_path=None):
    """CI/CD 中完整的 SoundBank 生成流程"""
    
    # 1. 打开工程（如需要）
    if project_path:
        client.call("ak.wwise.ui.project.open", {"path": project_path})
    
    # 2. 强制重新构建所有内容
    args = {
        "soundbanks": [],                       # 所有 SoundBank
        "platforms": [],                        # 所有平台
        "languages": [],                        # 所有语言
        "writeToDisk": True,
        "rebuildSoundBanks": True,               # 完全重建
        "clearAudioFileCache": True              # 清除转码缓存
    }
    
    result = client.call("ak.wwise.core.soundbank.generate", args)
    
    # 3. 检查结果
    error_count = 0
    warning_count = 0
    
    for log_entry in result.get("logs", []):
        severity = log_entry.get("severity", "")
        msg = log_entry.get("message", "")
        plat = log_entry.get("platform", {}).get("name", "")
        
        if severity in ("Error", "Fatal Error"):
            error_count += 1
            print(f"ERROR [{plat}]: {msg}", file=sys.stderr)
        elif severity == "Warning":
            warning_count += 1
            print(f"WARNING [{plat}]: {msg}")
        else:
            print(f"INFO [{plat}]: {msg}")
    
    # 4. 保存工程
    client.call("ak.wwise.core.project.save")
    
    # 5. 返回状态
    print(f"\n生成完成: {warning_count} 个警告, {error_count} 个错误")
    return error_count == 0


# 运行
success = generate_all_soundbanks()
client.disconnect()
sys.exit(0 if success else 1)
```

---

## 关联 API

| API | 用途 |
|-----|------|
| `ak.wwise.core.soundbank.setInclusions` | 设置 SoundBank 包含的 Event/结构/媒体 |
| `ak.wwise.core.soundbank.getInclusions` | 查询 SoundBank 的包含设置 |
| `ak.wwise.core.soundbank.processDefinitionFiles` | 处理 SoundBank 定义文件 |
| `ak.wwise.core.soundbank.convertExternalSources` | 转换外部音频源 |

### 相关 Topic

| Topic | 说明 |
|-------|------|
| `ak.wwise.core.soundbank.generated` | SoundBank 生成完成时发布，包含结构信息和 Base64 数据 |
| `ak.wwise.core.soundbank.generationDone` | 所有 SoundBank 生成完成时通知 |

---

## 常见陷阱和注意事项

1. **同步操作**：`ak.wwise.core.soundbank.generate` 是同步的，会阻塞直到生成完成。对于大型工程，构建可能耗时数分钟。
2. **Auto-defined SoundBank**：不能通过 `soundbanks` 参数指定，但始终会自动生成。
3. **缓存清除范围**：`clearAudioFileCache` 会清除所有平台的缓存（无视 `platforms` 参数）。
4. **临时 SoundBank**：如果指定的 SoundBank 名称不存在，Wwise 会创建临时 SoundBank（不会保存到工程）。
5. **HTTP 限制**：Pub/Sub（`ak.wwise.core.soundbank.generated`）仅支持 WAMP 协议，HTTP POST 无法订阅 Topic。
6. **构建顺序**：建议先生成 Init Bank（`rebuildInitBank: true`），再生成其他 SoundBank。

---

## 性能考量

- **增量构建**：日常开发使用默认参数（不设置 `rebuildSoundBanks`），仅构建变更的 Bank
- **完全重建**：发布构建时设置 `rebuildSoundBanks: true` 和 `clearAudioFileCache: true`
- **CI/CD**：建议按平台分批构建，避免单次构建时间过长
- **多语言**：`languages` 为空时会生成所有语言。对于仅需单一语言的快速迭代，明确指定目标语言
- **Base64 订阅**：通过 `ak.wwise.core.soundbank.generated` 获取 Base64 数据适合工具集成，但数据量大时注意内存

## 官方文档链接

- [ak.wwise.core.soundbank.generate](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_generate.html)
- [ak.wwise.core.soundbank.setInclusions](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_setinclusions.html)
- [ak.wwise.core.soundbank.generated](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_soundbank_generated.html)
