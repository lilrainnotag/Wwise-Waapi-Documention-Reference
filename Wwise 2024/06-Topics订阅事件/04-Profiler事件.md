# Profiler 事件

## 订阅机制

`ak.wwise.core.profiler.*` 系列 Topic 用于监听 Wwise Profiler 相关的运行时事件。其中 `stateChanged` 和 `switchChanged` 不需要启动 Profiler Capture Log 即可工作；其他 Profiler Topic 需要在 Profiler 会话活跃时才能接收通知。

---

## 事件列表

### ak.wwise.core.profiler.captureLog.itemAdded

- **触发时机**：当 Capture Log 中添加新条目时发送。注意：发送的是**所有**条目，不做任何过滤（与 Capture Log 视图中的过滤不同）
- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| item * | object | Capture Log 中新增的条目（官网未提供详细 Publish Schema） |
| item.time | integer | 条目的时间戳 |
| item.severity | string | 条目严重级别（如 "Message", "Warning", "Error"） |
| item.message | string | 条目的消息内容 |

- **WAMP 订阅示例**：

```python
from waapi import WaapiClient

client = WaapiClient()

def on_capture_log_item(channel, **kwargs):
    item = kwargs.get("item", {})
    print(f"[{item.get('severity')}] {item.get('message')}")

sub_id = client.subscribe(
    "ak.wwise.core.profiler.captureLog.itemAdded",
    callback=on_capture_log_item
)
```

- **注意事项**：
  - 不应用 Capture Log 视图中的任何过滤，发送**全部**条目
  - 高频事件（如每帧的 API 调用），订阅时注意回调性能
  - 需要 Profiler 会话处于活跃状态

---

### ak.wwise.core.profiler.gameObjectRegistered

- **触发时机**：当游戏对象（Game Object）在 Profiler 中被注册时发送
- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| gameObject * | object | 被注册的游戏对象信息 |
| gameObject.id | string | 游戏对象的 ID |
| gameObject.name | string | 游戏对象的名称 |

- **WAMP 订阅示例**：

```python
def on_game_object_registered(channel, **kwargs):
    go = kwargs.get("gameObject", {})
    print(f"游戏对象已注册: {go.get('name')} (ID: {go.get('id')})")

sub_id = client.subscribe(
    "ak.wwise.core.profiler.gameObjectRegistered",
    callback=on_game_object_registered
)
```

- **注意事项**：
  - 需要 Profiler 连接到游戏并处于活跃状态
  - 可用于跟踪游戏中活跃的游戏对象列表

---

### ak.wwise.core.profiler.gameObjectReset

- **触发时机**：当游戏对象被重置时发送（如关闭与游戏的 Profiler 连接）
- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| （官网未提供详细 Publish Schema） | — | 此 Topic 为状态变化通知 |

- **WAMP 订阅示例**：

```python
def on_game_object_reset(channel, **kwargs):
    print("游戏对象已重置")

sub_id = client.subscribe(
    "ak.wwise.core.profiler.gameObjectReset",
    callback=on_game_object_reset
)
```

- **注意事项**：
  - 通常在 Profiler 与游戏断开连接时触发
  - 表示所有之前注册的游戏对象已被清除

---

### ak.wwise.core.profiler.gameObjectUnregistered

- **触发时机**：当游戏对象（Game Object）在 Profiler 中被注销时发送
- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| gameObject * | object | 被注销的游戏对象信息 |
| gameObject.id | string | 游戏对象的 ID |
| gameObject.name | string | 游戏对象的名称 |

- **WAMP 订阅示例**：

```python
def on_game_object_unregistered(channel, **kwargs):
    go = kwargs.get("gameObject", {})
    print(f"游戏对象已注销: {go.get('name')} (ID: {go.get('id')})")

sub_id = client.subscribe(
    "ak.wwise.core.profiler.gameObjectUnregistered",
    callback=on_game_object_unregistered
)
```

- **注意事项**：
  - 需要 Profiler 连接处于活跃状态
  - 与 `gameObjectRegistered` 配对使用，可追踪游戏对象的完整生命周期

---

### ak.wwise.core.profiler.stateChanged

- **触发时机**：当 State Group 的 State 发生变化时发送。此订阅**不需要**启动 Profiler Capture Log
- **Options**：

| 名称 | 类型 | 说明 |
|------|------|------|
| return | array | 要返回的数据字段列表 |
| platform | string | 平台 GUID |

- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| stateGroup * | object | 发生变化的 State Group 对象。默认返回 id 和 name |
| stateGroup.id | string | State Group 的 GUID |
| stateGroup.name | string | State Group 的名称 |
| stateGroup.type | string | 对象类型（通常为 "StateGroup"） |
| state * | object | 变化后的 State 对象。默认返回 id 和 name |
| state.id | string | State 的 GUID |
| state.name | string | State 的名称 |
| state.type | string | 对象类型（通常为 "State"） |

- **WAMP 订阅示例**：

```python
def on_state_changed(channel, **kwargs):
    group = kwargs.get("stateGroup", {})
    state = kwargs.get("state", {})
    print(f"State 变化: {group.get('name')} → {state.get('name')}")

sub_id = client.subscribe(
    "ak.wwise.core.profiler.stateChanged",
    options={"return": ["id", "name"]},
    callback=on_state_changed
)
```

- **注意事项**：
  - ✅ **不需要**启动 Profiler Capture Log 即可工作
  - 在游戏运行时动态反映 State 切换情况
  - 同时返回 stateGroup 和 state，可通过 return 选项获取更多属性

---

### ak.wwise.core.profiler.switchChanged

- **触发时机**：当 Switch Group 的 Switch 发生变化时发送。此订阅**不需要**启动 Profiler Capture Log
- **发布内容（返回值）**：

| 名称 | 类型 | 说明 |
|------|------|------|
| switchGroup * | object | 发生变化的 Switch Group 对象。默认返回 id 和 name |
| switchGroup.id | string | Switch Group 的 GUID |
| switchGroup.name | string | Switch Group 的名称 |
| switch * | object | 变化后的 Switch 对象。默认返回 id 和 name |
| switch.id | string | Switch 的 GUID |
| switch.name | string | Switch 的名称 |

- **WAMP 订阅示例**：

```python
def on_switch_changed(channel, **kwargs):
    group = kwargs.get("switchGroup", {})
    switch = kwargs.get("switch", {})
    print(f"Switch 变化: {group.get('name')} → {switch.get('name')}")

sub_id = client.subscribe(
    "ak.wwise.core.profiler.switchChanged",
    options={"return": ["id", "name"]},
    callback=on_switch_changed
)
```

- **注意事项**：
  - ✅ **不需要**启动 Profiler Capture Log 即可工作
  - 与 `stateChanged` 类似，但用于 Switch/ Switch Group 机制
  - 在游戏运行时动态反映 Switch 切换情况

---

## 官方文档链接

- [ak.wwise.core.profiler.captureLog.itemAdded](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_capturelog_itemadded.html)
- [ak.wwise.core.profiler.gameObjectRegistered](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_gameobjectregistered.html)
- [ak.wwise.core.profiler.gameObjectReset](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_gameobjectreset.html)
- [ak.wwise.core.profiler.gameObjectUnregistered](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_gameobjectunregistered.html)
- [ak.wwise.core.profiler.stateChanged](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_statechanged.html)
- [ak.wwise.core.profiler.switchChanged](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_profiler_switchchanged.html)
