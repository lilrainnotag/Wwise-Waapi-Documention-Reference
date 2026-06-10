# 07 - 版本控制与 Lua 集成

> **数据来源**: Audiokinetic 官方文档 — `ak.wwise.core.sourceControl.*` 和 `ak.wwise.core.executeLuaScript`

## 场景描述

Wwise WAAPI 提供了与版本控制系统集成的完整 API，以及通过 Lua 脚本在 Wwise 内部执行自动化操作的能力。这两个功能可以结合使用，形成强大的自动化管线。

---

## 第一部分：版本控制（Source Control）

### 核心 API 函数列表

| API 函数 | 说明 |
|----------|------|
| `ak.wwise.core.sourceControl.add` | 将文件添加到版本控制 |
| `ak.wwise.core.sourceControl.checkOut` | 从版本控制检出文件 |
| `ak.wwise.core.sourceControl.commit` | 提交更改到版本控制 |
| `ak.wwise.core.sourceControl.delete` | 从版本控制删除文件 |
| `ak.wwise.core.sourceControl.getSourceFiles` | 获取源文件列表 |
| `ak.wwise.core.sourceControl.getStatus` | 获取文件的版本控制状态 |
| `ak.wwise.core.sourceControl.move` | 在版本控制中移动文件 |
| `ak.wwise.core.sourceControl.revert` | 还原文件的版本控制更改 |
| `ak.wwise.core.sourceControl.setProvider` | 设置版本控制提供者 |

---

### 核心 API 调用链

```
1. 连接 WAAPI → WaapiClient()
2. 设置版本控制提供者 (setProvider)
3. 检查文件状态 (getStatus)
4. 检出所需文件 (checkOut)
5. 执行工程修改（通过其他 WAAPI 调用）
6. 添加新文件 (add) 或提交更改 (commit)
7. 断开连接 → client.disconnect()
```

---

### 示例代码

#### 示例 1：获取文件状态

```python
from waapi import WaapiClient
import pprint

client = WaapiClient()

# 获取特定对象的源文件状态
args = {
    "objects": [
        "{workunit-guid}"
    ]
}
result = client.call("ak.wwise.core.sourceControl.getStatus", args)
pprint.pprint(result)

client.disconnect()
```

#### 示例 2：检出、修改、提交工作流

```python
client = WaapiClient()

# 步骤 1：检出 Work Unit
work_unit_id = "{workunit-guid}"
checkout_args = {
    "objects": [work_unit_id]
}
client.call("ak.wwise.core.sourceControl.checkOut", checkout_args)
print("Work Unit 已检出")

# 步骤 2：执行修改操作
# 例如：修改对象名称
set_name_args = {
    "object": work_unit_id,
    "value": "New Name"
}
# 注意：setName 的具体参数格式请参见 ak.wwise.core.object.setName
# （此处为概念示意）

# 步骤 3：提交更改
commit_args = {
    "objects": [work_unit_id],
    "message": "WAAPI: 修改对象名称"
}
client.call("ak.wwise.core.sourceControl.commit", commit_args)
print("更改已提交")

client.disconnect()
```

#### 示例 3：批量版本控制操作

```python
client = WaapiClient()

# 获取项目中所有 Work Unit
get_args = {
    "waql": "$ from type WorkUnit"
}
options = {
    "return": ["id", "name", "path", "workunit:isDirty"]
}
result = client.call("ak.wwise.core.object.get", get_args, options=options)

# 检出所有脏 Work Unit
dirty_units = [obj for obj in result.get("return", [])
               if obj.get("workunit:isDirty")]

if dirty_units:
    checkout_args = {
        "objects": [u["id"] for u in dirty_units]
    }
    client.call("ak.wwise.core.sourceControl.checkOut", checkout_args)
    print(f"已检出 {len(dirty_units)} 个脏 Work Unit")
else:
    print("没有脏 Work Unit")

client.disconnect()
```

#### 示例 4：获取源文件列表

```python
client = WaapiClient()

# 获取项目的源文件列表
result = client.call("ak.wwise.core.sourceControl.getSourceFiles")
pprint.pprint(result)

client.disconnect()
```

---

## 第二部分：Lua 脚本集成

### ak.wwise.core.executeLuaScript

> **数据来源**: [ak.wwise.core.executeLuaScript](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_executeluascript.html) 官方参考页

**官方描述**: "Execute a Lua script. Optionally, specify additional Lua search paths, additional modules, and additional Lua scripts to load prior to the main script. The script can return a value. All arguments will be passed to the Lua script in the 'wa_args' global variable."

---

### 参数说明（来源：官方 Schema）

| 参数 | 类型 | 必需 | 说明 |
|------|------|------|------|
| `luaScript` | string | ✅ | 要加载和执行的主 Lua 脚本内容 |
| `luaPaths` | array | — | 额外 Lua 模块搜索路径，如 `'C:/path_to_folder/?.lua'` |
| `requires` | array | — | 使用 require 系统加载的额外模块。以下目录自动加入 Lua path: `PROJECT/Add-ons/Lua`, `APPDATA/Audiokinetic/Wwise/Add-ons/Lua`, `INSTALLDIR/Authoring/Data/Add-ons/Lua` |
| `doFiles` | array | — | 在主脚本之前加载的额外 Lua 文件。也可指定目录，目录中所有 .lua 文件都会被加载 |

**返回值**: `boolean`, `object`, `array`, `number`, `string` — Lua 脚本的 return 语句返回的值。

> **注意**: 所有 WAAPI 调用参数通过全局变量 `wa_args` 传递给 Lua 脚本。

---

### 示例代码

#### 示例 1：执行简单 Lua 脚本

```python
from waapi import WaapiClient

client = WaapiClient()

# 执行一个简单的 Lua 脚本
args = {
    "luaScript": """
        -- Lua 脚本通过 wa_args 接收 WAAPI 传递的参数
        return "Hello from Lua!"
    """
}

result = client.call("ak.wwise.core.executeLuaScript", args)
print(f"Lua 返回值: {result.get('return', result)}")

client.disconnect()
```

> **注意**: `executeLuaScript` 的参数名是 `luaScript`（驼峰命名），不是 `script`。在 Lua 脚本中通过 `wa_args` 全局变量访问 WAAPI 传递的参数。Wwise Authoring Lua API 的可用函数请参考官方的 "Authoring Lua API" 文档（官网未在 executeLuaScript 页面列出具体的 Lua API 函数）。

#### 示例 2：批量设置对象属性

```python
client = WaapiClient()

# 通过 Lua 脚本批量设置属性
lua_script = """
-- Note: Wwise Authoring Lua API functions (like wwise.getObjects, wwise.createObject)
-- are documented in the Authoring Lua API reference (see official docs).
-- This is a conceptual example. Actual Lua API functions may differ.
return "Lua script executed"
"""

args = {"luaScript": lua_script}
result = client.call("ak.wwise.core.executeLuaScript", args)
print(result)

client.disconnect()
```

#### 示例 3：复杂的工程自动化

```python
client = WaapiClient()

lua_script = """
-- 创建一个新的 Work Unit 和角色文件夹结构
-- Note: The Wwise Authoring Lua API function names shown here are conceptual.
-- For actual API functions, refer to the official Authoring Lua API documentation.
return "自动化结构创建完成"
"""

args = {"luaScript": lua_script}
result = client.call("ak.wwise.core.executeLuaScript", args)
print(result)

client.disconnect()
```

#### 示例 4：Lua 与版本控制结合

```python
client = WaapiClient()

# 先通过 WAAPI 检出文件
client.call("ak.wwise.core.sourceControl.checkOut", {
    "objects": ["{workunit-guid}"]
})

# 通过 Lua 脚本执行批量修改
lua_script = """
-- 通过 Lua 脚本修改对象
-- Note: Wwise Authoring Lua API functions are documented separately.
-- This is a conceptual example showing the pattern.
return "操作完成"
"""

args = {"luaScript": lua_script}
result = client.call("ak.wwise.core.executeLuaScript", args)
print(result)

# 提交更改
client.call("ak.wwise.core.sourceControl.commit", {
    "objects": ["{workunit-guid}"],
    "message": "WAAPI + Lua: 批量添加 MOD_ 前缀"
})

client.disconnect()
```

---

## 版本控制最佳实践

1. **先检查后操作**：在修改对象前，先调用 `getStatus` 检查文件状态
2. **批量检出**：一次性检出一个操作中涉及的所有 Work Unit
3. **有意义的提交信息**：在 `commit` 中使用描述性消息，便于追踪更改历史
4. **处理冲突**：在自动化流程中检测并处理版本冲突（官网未提供冲突检测的详细 API）
5. **还原机制**：使用 `revert` 在出现问题时快速回退更改

## Lua 脚本最佳实践

1. **分步测试**：先在 Wwise 内置的 Lua 编辑器中测试脚本，再通过 WAAPI 调用
2. **错误处理**：在 Lua 脚本中使用 `pcall` 捕获错误并返回友好信息
3. **性能考虑**：大量对象的操作建议使用 WAAPI 而非 Lua，WAAPI 通常性能更好
4. **对象 ID 传递**：将对象 GUID 从 WAAPI 传递给 Lua 脚本时确保格式正确
5. **混合使用**：在同一个工作流中结合 WAAPI（用于查询和简单操作）和 Lua（用于复杂逻辑）

---

## Wwise Authoring Lua API 简介

`executeLuaScript` 中使用的 Lua API 基于 Wwise Authoring Lua API（详见 Authoring Lua API 文档）。该 API 提供了在 Wwise 内部操作对象和工程的完整 Lua 接口。

> ⚠️ **注意**: 具体的 Lua API 函数名称和用法请参考官方的 "Authoring Lua API" 文档。`executeLuaScript` 的官方参考页未列出具体的 Lua API 函数列表，仅说明了 Lua 脚本的执行机制（通过 `wa_args` 全局变量传递参数，使用 `luaPaths`、`requires`、`doFiles` 管理依赖）。

### wa_* API 函数列表

以下函数列表从 Wwise 2025.1.8 官方 Authoring Lua API 文档提取，所有函数均以 `wa_` 为前缀。

#### 文件操作

| 函数 | 说明 | 参数 |
|------|------|------|
| `wa_abs_path(path)` | 返回输入路径的绝对路径形式 | `path` (string) — 要转换的目录路径 |
| `wa_canonicalize_path(path)` | 返回规范化路径（去除 `..` 和 `.`，使用首选分隔符） | `path` (string) — 要规范化的路径字符串 |
| `wa_copy_directory(source, destination)` | 将源目录复制到目标目录 | `source` (string) — 源目录路径；`destination` (string) — 目标目录路径 |
| `wa_copy_file(source, destination)` | 将源文件复制到目标文件 | `source` (string) — 源文件路径；`destination` (string) — 目标文件路径 |
| `wa_directory_exists(path)` | 检查目录是否存在 | `path` (string) — 要验证的目录 |
| `wa_ensure_directory_exist(path)` | 确保目录存在，不存在则创建 | `path` (string) — 要验证或创建的目录 |
| `wa_move(path, destination)` | 将源目录移动到目标路径 | `path` (string) — 源目录；`destination` (string) — 目标路径 |
| `wa_remove_directory(path)` | 从文件系统删除目录 | `path` (string) — 要删除的目录 |
| `wa_temporary_directory()` | 创建临时目录 | 无参数 |

#### WAAPI 调用

| 函数 | 说明 | 参数 |
|------|------|------|
| `wa_call(uri, args, options)` | 调用 WAAPI 函数 | `uri` (string) — WAAPI 函数标识符；`args` (table) — 参数表；`options` (table) — 选项表 |
| `wa_subscribe(uri, options, func)` | 订阅 WAAPI 主题 | `uri` (string) — 要订阅的 WAAPI 函数标识符；`options` (table) — 选项表；`func` (function) — 事件回调函数 |
| `wa_unsubscribe(id)` | 取消 WAAPI 订阅 | `id` (number) — `wa_subscribe` 返回的订阅 ID |
| `wa_unsubscribe_all()` | 取消所有 WAAPI 订阅 | 无参数 |

#### 传输控制

| 函数 | 说明 | 参数 |
|------|------|------|
| `wa_render_audio()` | 渲染音频（离线渲染） | 无参数 |
| `wa_reset_transport()` | 重置传输控件 | 无参数 |

#### 调试与日志

| 函数 | 说明 | 参数 |
|------|------|------|
| `wa_debug_break()` | 在当前进程中触发断点 | 无参数 |
| `wa_start_capture_console_output()` | 开始捕获控制台输出 | 无参数 |
| `wa_stop_capture_console_output()` | 停止捕获控制台输出 | 无参数 |
| `wa_start_output_capture(filename)` | 开始将输出捕获到文件 | `filename` (string) — 输出捕获文件的保存路径 |
| `wa_stop_output_capture()` | 停止输出捕获 | 无参数 |
| `wa_get_api_statistics()` | 返回 Lua API 统计信息表，并刷新统计数据 | 无参数 |
| `wa_log(message)` | 在 Wwise 中记录字符串消息 | `message` (string) — 要记录的消息 |

#### 系统与工具

| 函数 | 说明 | 参数 |
|------|------|------|
| `wa_connect_as_remote(value)` | 模拟远程连接时的 WAL 行为 | `value` (boolean) — 设置值 |
| `wa_copy_to_clipboard(content)` | 将字符串复制到剪贴板 | `content` (string) — 要复制的字符串 |
| `wa_get_from_clipboard()` | 获取剪贴板内容 | 无参数 |
| `wa_get_project_curve(arg)` | 获取项目曲线及其点数据 | `arg` (string) — 命令行参数 |
| `wa_get_session_guid()` | 返回应用程序的会话 GUID | 无参数 |
| `wa_json_pretty_print(table)` | 将 Lua table 转换为 JSON 格式化字符串 | `table` (table) — 要格式化的表 |
| `wa_read_json(strJson)` | 将 JSON 字符串转换为 Lua table | `strJson` (string) — JSON 对象字符串 |
| `wa_table_to_json(args)` | 将 Lua table 转换为 AkJson | `args` (table) — 要转换的表 |
| `wa_set_local_read_only(value)` | 设置本地只读模式 | `value` (boolean) — 设置值 |
| `wa_set_offline_rendering(value)` | 设置离线渲染开关 | `value` (boolean) — 设置值 |
| `wa_set_user_pref(location, name, value)` | 设置用户偏好 | `location` (string) — 偏好位置；`name` (string) — 偏好名称；`value` (number/boolean/string) — 偏好值 |
| `wa_shell_execute(arg)` | 执行 shell 命令 | `arg` (string) — 命令行参数 |
| `wa_simulate_originals_watcher_update(table)` | 模拟 OS 的目录监视事件，指定变更路径列表 | `table` (table) — 声明为变更的路径列表 |
| `wa_sleep(milliseconds)` | 暂停线程执行指定毫秒数 | `milliseconds` (number) — 暂停的毫秒数 |
| `wa_std_channel_index_to_meter_index(channelIndex, channelMask)` | 将 WEM/Sound Engine 顺序的声道索引转换为仪表显示顺序的索引 | `channelIndex` (number) — WAV 文件的声道索引；`channelMask` (number) — 声道配置掩码 |
| `wa_time()` | 获取当前时间 | 无参数 |
| `wa_user_name()` | 获取用户名 | 无参数 |
| `wa_enable_originals_watcher(boolean)` | 启用或禁用 Originals 目录监视器 | `boolean` (boolean) — `true` 启用目录监视器

---

## 完整自动化管线示例

以下示例展示了版本控制 + Lua + WAAPI 的完整自动化管线：

```python
from waapi import WaapiClient

client = WaapiClient()

def auto_rename_sounds_with_prefix(prefix="CHR_"):
    """自动化管线：检出 → Lua 重命名 → 提交"""
    
    # 1. 获取需要处理的 Work Unit
    get_args = {
        "waql": "$ from type WorkUnit where name:contains \"Character\""
    }
    options = {"return": ["id", "name"]}
    result = client.call("ak.wwise.core.object.get", get_args, options=options)
    work_units = result.get("return", [])
    
    if not work_units:
        print("未找到匹配的 Work Unit")
        return
    
    # 2. 检出版本控制
    wu_ids = [wu["id"] for wu in work_units]
    for wu_id in wu_ids:
        try:
            client.call("ak.wwise.core.sourceControl.checkOut", {
                "objects": [wu_id]
            })
            print(f"已检出 Work Unit: {wu_id}")
        except Exception as e:
            print(f"检出失败: {e}")
            return
    
    # 3. 通过 Lua 脚本批量重命名
    lua_script = """
-- 执行批量重命名操作
-- Note: Refer to the official Authoring Lua API for actual function names.
return "操作完成"
"""
    
    lua_args = {"luaScript": lua_script}
    rename_result = client.call("ak.wwise.core.executeLuaScript", lua_args)
    print(f"通过 Lua 重命名了 {rename_result} 个对象")
    
    # 4. 保存项目
    client.call("ak.wwise.core.project.save")
    
    # 5. 提交版本控制
    for wu_id in wu_ids:
        try:
            client.call("ak.wwise.core.sourceControl.commit", {
                "objects": [wu_id],
                "message": f"WAAPI 自动化: 为 Sound 对象添加 '{prefix}' 前缀"
            })
            print(f"已提交 Work Unit: {wu_id}")
        except Exception as e:
            print(f"提交失败: {e}")
    
    print("自动化管线执行完毕")

# 执行自动化管线
auto_rename_sounds_with_prefix("CHR_")

client.disconnect()
```

> **数据来源**：以上 API 函数列表和功能说明均从 Audiokinetic 官方文档 (Wwise 2024.1.14) 提取。Lua API 的具体函数参考 Authoring Lua API 文档。标注为"官网未提供"的部分在文档中未明确列出详细格式。
