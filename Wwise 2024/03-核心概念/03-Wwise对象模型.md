# 03-Wwise 对象模型

## Wwise 工程层级结构

Wwise 工程以层级树的形式组织所有对象。主要分为以下几个顶层类别（Category）：

### 1. Actor-Mixer Hierarchy（Actor-Mixer 层级）

音频行为的核心层级，包含所有的声音对象和容器对象：

- **ActorMixer** — Actor 混合器，用于组织和控制一组声音
- **RandomSequenceContainer** — 随机/序列容器，控制子对象的播放顺序
- **SwitchContainer** — 开关容器，根据 Switch 选择播放的子对象
- **BlendContainer** — 混合容器，根据 Game Parameter 混合子对象
- **Sound** — 声音对象，Wwise 中最基本的音频单元
- **AudioFileSource** — 音频文件源，关联到实际的 WAV 文件
- **SourcePlugin** — 源插件（例如 Wwise Synth One、Tone Generator）
- **MotionSource** — 运动/振动源

### 2. Interactive Music Hierarchy（交互音乐层级）

专门用于组织音乐对象：

- **MusicSwitchContainer** — 音乐开关容器
- **MusicPlaylistContainer** — 音乐播放列表容器
- **MusicSegment** — 音乐段落
- **MusicTrack** — 音乐轨道
- **MusicTrackSequence** — 音乐轨道序列
- **MusicClip** — 音乐片段（关联音频文件）
- **MusicClipMidi** — MIDI 音乐片段
- **MusicCue** — 音乐提示点
- **MusicEventCue** — 音乐事件提示点
- **MusicFade** — 音乐淡入淡出
- **MusicStinger** — 音乐 Stinger（短音乐片段）
- **MusicTransition** — 音乐过渡
- **MusicPlaylistItem** — 音乐播放列表项

### 3. Master-Mixer Hierarchy（主混音器层级/总线）

音频路由和混音结构：

- **Bus** — 主总线
- **AuxBus** — 辅助总线（用于发送效果）
- **AudioDevice** — 音频输出设备
- **Effect** — 效果器插件实例
- **EffectSlot** — 效果器插槽
- **Attenuation** — 衰减对象（控制声音的空间衰减）

### 4. Event 系统

- **Event** — 事件，触发动作的入口
- **Action** — 动作（Play、Stop、Pause、Resume、Mute 等）
- **ActionException** — 动作异常规则
- **DialogueEvent** — 对话事件

### 5. SoundBank 系统

- **SoundBank** — 声音库，包含打包的音频数据和元数据
- **ExternalSource** — 外部音频源
- **ExternalSourceFile** — 外部音频源文件
- **Conversion** — 转换设置

### 6. 游戏同步系统

- **GameParameter** — 游戏参数（RTPC 的驱动源）
- **StateGroup** — 状态组
- **State** — 状态
- **SwitchGroup** — 开关组
- **Switch** — 开关
- **Trigger** — 触发器
- **RTPC** — 实时参数控制

### 7. 全局/工程级别对象

- **Project** — 工程
- **WorkUnit** — 工作单元（物理文件）
- **Folder** — 文件夹（组织对象，不生成数据）
- **Platform** — 平台定义
- **Language** — 语言定义
- **Query** — 查询对象
- **SearchCriteria** — 搜索条件
- **UserProjectSettings** — 用户工程设置
- **MixingSession** — 混音会话
- **SoundcasterSession** — Soundcaster 会话
- **ControlSurfaceSession** — 控制面板会话
- **ControlSurfaceBinding** — 控制面板绑定
- **ControlSurfaceBindingGroup** — 控制面板绑定组

### 8. 其他对象类型

- **Curve** — 曲线（RTPC 衰减曲线）
- **Modifier** — 修饰器
- **ModulatorEnvelope** — 包络调制器
- **ModulatorLfo** — LFO 调制器
- **ModulatorTime** — 时间调制器
- **Panner** — 声像器
- **Path2D** — 2D 路径
- **Position** — 位置
- **AcousticTexture** — 声学材质
- **CustomState** — 自定义状态
- **Marker** — 标记点
- **Metadata** — 元数据
- **MidiParameter** — MIDI 参数
- **MultiSwitchEntry** — 多开关条目
- **ObjectSettingAssoc** — 对象设置关联
- **PluginDataSource** — 插件数据源
- **BlendTrack** — 混合轨道

## 对象类型完整列表

来自 Audiokinetic 官方文档 **Wwise Objects Reference** 页面：

### 基础类型 (Types)

| 名称 | ClassID | 说明 |
|------|---------|------|
| AcousticTexture | 4718608 | 声学材质 |
| Action | 327696 | 动作 |
| ActionException | 4980752 | 动作异常 |
| ActorMixer | 524304 | Actor 混合器 |
| Attenuation | 2686992 | 衰减 |
| AudioDevice | 4653072 | 音频设备 |
| AudioFileSource | 16 | 音频文件源 |
| AuxBus | 3997712 | 辅助总线 |
| BlendContainer | 1900560 | 混合容器 |
| BlendTrack | 1966096 | 混合轨道 |
| Bus | 1376272 | 总线 |
| ControlSurfaceBinding | 4390928 | 控制面板绑定 |
| ControlSurfaceBindingGroup | 4456464 | 控制面板绑定组 |
| ControlSurfaceSession | 4325392 | 控制面板会话 |
| Conversion | 3604496 | 转换设置 |
| Curve | 917520 | 曲线 |
| CustomState | 5177360 | 自定义状态 |
| DialogueEvent | 3014672 | 对话事件 |
| Effect | 1114128 | 效果器 |
| EffectSlot | 5505040 | 效果器插槽 |
| Event | 262160 | 事件 |
| ExternalSource | 3735568 | 外部源 |
| ExternalSourceFile | 3670032 | 外部源文件 |
| Folder | 131088 | 文件夹 |
| GameParameter | 1507344 | 游戏参数 |
| Language | 4915216 | 语言 |
| Marker | 5373968 | 标记 |
| Metadata | 5308432 | 元数据 |
| MidiFileSource | 5242896 | MIDI 文件源 |
| MidiParameter | 4128784 | MIDI 参数 |
| MixingSession | 3473424 | 混音会话 |
| Modifier | 983056 | 修饰器 |
| ModulatorEnvelope | 4259856 | 包络调制器 |
| ModulatorLfo | 4194320 | LFO 调制器 |
| ModulatorTime | 5111824 | 时间调制器 |
| MultiSwitchEntry | 5439504 | 多开关条目 |
| MusicClip | 3932176 | 音乐片段 |
| MusicClipMidi | 4063248 | MIDI 音乐片段 |
| MusicCue | 3866640 | 音乐提示点 |
| MusicEventCue | 5046288 | 音乐事件提示点 |
| MusicFade | 2555920 | 音乐淡入淡出 |
| MusicPlaylistContainer | 2228240 | 音乐播放列表容器 |
| MusicPlaylistItem | 2359312 | 音乐播放列表项 |
| MusicSegment | 1769488 | 音乐段落 |
| MusicStinger | 2490384 | 音乐 Stinger |
| MusicSwitchContainer | 2293776 | 音乐开关容器 |
| MusicTrack | 1835024 | 音乐轨道 |
| MusicTrackSequence | 3801104 | 音乐轨道序列 |
| MusicTransition | 2424848 | 音乐过渡 |
| ObjectSettingAssoc | 1572880 | 对象设置关联 |
| Panner | 2752528 | 声像器 |
| Path2D | 720912 | 2D 路径 |
| Platform | 4522000 | 平台 |
| PluginDataSource | 3538960 | 插件数据源 |
| Position | 786448 | 位置(Positioning) |
| Project | 196624 | 工程 |
| Query | 2097168 | 查询 |
| RandomSequenceContainer | 589840 | 随机/序列容器 |
| RTPC | 1441808 | 实时参数控制 |
| SearchCriteria | 2162704 | 搜索条件 |
| Sound | 65552 | 声音 |
| SoundBank | 1179664 | 声音库 |
| SoundcasterSession | 1703952 | Soundcaster 会话 |
| SourcePlugin | 1048592 | 源插件 |
| State | 393232 | 状态 |
| StateGroup | 458768 | 状态组 |
| Switch | 1310736 | 开关 |
| SwitchContainer | 655376 | 开关容器 |
| SwitchGroup | 1245200 | 开关组 |
| Trigger | 2621456 | 触发器 |
| UserProjectSettings | 3342352 | 用户工程设置 |
| WorkUnit | 1638416 | 工作单元 |

### 效果器类型 (Effects)

| 名称 | PluginID | ClassID |
|------|----------|---------|
| Mastering Suite | 186 | 12189699 |
| Wwise 3D Audio Bed Mixer | 190 | 12451843 |
| Wwise Compressor | 108 | 7077891 |
| Wwise Convolution Reverb | 127 | 8323075 |
| Wwise Delay | 106 | 6946819 |
| Wwise Expander | 109 | 7143427 |
| Wwise Flanger | 125 | 8192003 |
| Wwise Gain | 139 | 9109507 |
| Wwise Guitar Distortion | 126 | 8257539 |
| Wwise Harmonizer | 138 | 9043971 |
| Wwise Matrix Reverb | 115 | 7536643 |
| Wwise Meter | 129 | 8454147 |
| Wwise Parametric EQ | 105 | 6881283 |
| Wwise Peak Limiter | 110 | 7208963 |
| Wwise Pitch Shifter | 136 | 8912899 |
| Wwise Recorder | 132 | 8650755 |
| Wwise Reflect | 171 | 11206659 |
| Wwise RoomVerb | 118 | 7733251 |
| Wwise Stereo Delay | 135 | 8847363 |
| Wwise Time Stretch | 130 | 8519683 |
| Wwise Tremolo | 131 | 8585219 |

### 源插件类型 (Sources)

| 名称 | PluginID | ClassID |
|------|----------|---------|
| Impacter | 184 | 12058626 |
| Motion Source | 409 | 26804226 |
| SoundSeed Air Wind | 119 | 7798786 |
| SoundSeed Air Woosh | 120 | 7864322 |
| SoundSeed Grain | 183 | 11993090 |
| Wwise Silence | 101 | 6619138 |
| Wwise Synth One | 148 | 9699330 |
| Wwise Tone Generator | 102 | 6684674 |

## Work Unit 概念

### 物理文件 vs 逻辑对象

- **Work Unit (工作单元)** 是 Wwise 工程中对象的物理存储容器，对应磁盘上的 `.wwu` 文件
- 在 WAAPI 中，Work Unit 也是一个逻辑对象，具有 `id`、`name` 等属性
- 每个非 Work Unit 对象都隶属于某个 Work Unit

### Work Unit 类型 (workunitType)

| workunitType | 说明 |
|-------------|------|
| `folder` | 物理文件夹（在磁盘上有对应目录） |
| `rootFile` | 根文件（工程根级别的 .wwu 文件） |
| `nestedFile` | 嵌套文件（子目录中的 .wwu 文件） |

### Work Unit 相关属性

| 属性 | 类型 | 说明 |
|------|------|------|
| `workunitIsDefault` | boolean | 是否为默认 Work Unit |
| `workunitType` | string | Work Unit 类型：`folder`/`rootFile`/`nestedFile` |
| `workunitIsDirty` | boolean | Work Unit 是否未保存（含工程文件 .wproj） |

> **注意**：创建工作单元（Work Unit）需要先清除 undo/redo 历史和剪贴板，且名称冲突模式不能使用 `replace`。

## Virtual Folder vs Physical Folder

### Virtual Folder（虚拟文件夹）
- 仅存在于 Wwise 工程内部，作为逻辑组织容器
- 不占用磁盘目录
- 类型为 `Folder`（ClassID: 131088）

### Physical Folder（物理文件夹）
- 对应磁盘上的实际目录
- 包含 `.wwu` 文件
- 在 WAAPI 中类型为 `WorkUnit`，但 `workunitType` 为 `"folder"`
- 类型为 `WorkUnit`（ClassID: 1638416）

## 对象的属性、引用、列表

WAAPI 中每个 Wwise 对象包含三类数据：

### 1. 属性（Property）

属性是对象的**标量值**，可以是数值、字符串或布尔值。

**通过 `ak.wwise.core.object.get` 获取属性时的前缀约定：**

| 前缀 | 含义 | 示例 |
|------|------|------|
| `PropertyName`（无前缀）| 返回经 Override 系统解析后的值（推荐）| `"Volume"` 返回实际生效的音量值 |
| `@PropertyName` | 返回直接在对象上设置的值，忽略 Override 系统 | `"@Volume"` 返回对象上直接设置的音量（可能被 Override 隐藏） |
| `@@PropertyName` | 与无前缀相同，返回解析后的值 | `"@@Volume"` 等价于 `"Volume"` |

**常见属性示例：**

| 属性 | 类型 | 说明 |
|------|------|------|
| `Volume` | number | 音量（分贝） |
| `Pitch` | number | 音高（音分） |
| `Lowpass` | number | 低通滤波 |
| `Highpass` | number | 高通滤波 |
| `MakeUpGain` | number | 补偿增益 |
| `OutputBusVolume` | number | 输出总线音量 |
| `RandomOrSequence` | number | 随机（0）还是序列（1）播放 |

### 2. 引用（Reference）

引用是**指向另一个 Wwise 对象的指针**。通过点号链式访问引用目标的属性。

```
OutputBus              → 引用的 Bus 对象
OutputBus.name         → 引用的 Bus 对象的名称
OutputBus.Volume       → 引用的 Bus 对象的音量
OutputBus.Attenuation  → 引用的 Bus 的衰减对象
UserAuxSend0           → 第 0 个用户辅助发送目标
Effects.first.effect.id → 第一个效果器的 ID
```

**常见引用示例：**

| 引用 | 说明 |
|------|------|
| `OutputBus` | 输出总线 |
| `Attenuation` | 衰减对象 |
| `Conversion` | 转换设置 |
| `UserAuxSend0` ~ `UserAuxSend3` | 用户辅助发送 |

> **注意**：引用名称不区分大小写。`OutputBus`、`outputbus`、`@@OutputBus` 等价。

### 3. 列表（List）

列表是**对象的子集合**。列表中的对象通常是同类型的。

**常见列表示例：**

| 列表 | 说明 |
|------|------|
| `children` | 子对象列表 |
| `RTPC` | RTPC 关联列表 |
| `Effects` | 效果器列表 |
| `States` | 状态设置列表 |
| `Stingers` | Stinger 列表 |
| `Sequences` | 序列列表 |
| `Clips` | 音频片段列表 |
| `Metadata` | 元数据列表 |

**列表操作模式（`listMode`）：**

| 模式 | 说明 |
|------|------|
| `append` | 添加到列表末尾（默认） |
| `replaceAll` | 清除已有项后添加新项 |

## 对象之间的关系

### 1. 父子关系
- Wwise 对象组织为层级树
- 使用 `select parent` / `select children` / `select descendants` / `select ancestors` 在查询中遍历

### 2. 引用关系
- 一个对象引用另一个对象（如 Sound 的 `OutputBus` 引用 Bus）
- 使用 `OutputBus.name` 等链式访问获取被引用对象的属性

### 3. Event → Action → Target 关系

```
Event
  └── Action（Play）
       └── Target（Sound / Container 等）
  └── Action（Stop）
       └── Target
  └── Action（Set State）
       └── Target（StateGroup）
```

### 4. 查询遍历关系

| 转换 | 说明 |
|------|------|
| `select parent` | 选择父对象 |
| `select children` | 选择子对象 |
| `select descendants` | 选择所有递归子对象 |
| `select ancestors` | 选择所有递归父对象 |
| `select referencesTo` | 选择所有引用当前对象的对象 |

## 参考来源

- Audiokinetic 官方文档：Wwise Objects Reference
- Audiokinetic 官方文档：ak.wwise.core.object.get
- Audiokinetic 官方文档：Querying the Wwise Project
- Audiokinetic 官方文档：Importing Audio Files and Creating Structures
