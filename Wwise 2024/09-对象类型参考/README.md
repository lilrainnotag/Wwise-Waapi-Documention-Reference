# 09-对象类型参考（Object Type Reference）

> **来源**: [Audiokinetic 官方文档 - Wwise Objects Reference](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wwise_object_reference.html)（注：2024.1.14 版本中该页面已无法直接访问，可通过 `ak.wwise.core.object.getTypes` 运行时获取类型列表）

## 概述

Wwise 对象类型系统是所有 WAAPI 操作的基础。每个 Wwise 对象都属于某种类型（Type），每种类型有唯一的 **ClassID**，并定义了一组**属性**（Property）、**引用**（Reference）和**列表**（List）。

### 获取对象类型列表

通过 WAAPI 运行时获取所有支持的对象类型：

```json
{
    "method": "ak.wwise.core.object.getTypes",
    "params": {}
}
```

返回值包含每种类型的 `classId`、`name`、`type`。

## 对象类型层级关系

```
Wwise Object（所有对象的基类）
│
├── 声音对象（Sound Objects）
│   ├── Sound（声音）— ClassID: 65552
│   ├── AudioFileSource（音频文件源）— ClassID: 16
│   ├── SourcePlugin（源插件）— ClassID: 1048592
│   ├── MotionSource（运动源）— PluginID: 409
│   └── MidiFileSource（MIDI 文件源）— ClassID: 5242896
│
├── 容器对象（Container Objects）
│   ├── ActorMixer（Actor 混合器）— ClassID: 524304
│   ├── RandomSequenceContainer（随机/序列容器）— ClassID: 589840
│   ├── SwitchContainer（开关容器）— ClassID: 655376
│   ├── BlendContainer（混合容器）— ClassID: 1900560
│   └── BlendTrack（混合轨道）— ClassID: 1966096
│
├── 音乐对象（Music Objects）
│   ├── MusicSegment（音乐段落）— ClassID: 1769488
│   ├── MusicPlaylistContainer（音乐播放列表容器）— ClassID: 2228240
│   ├── MusicPlaylistItem（音乐播放列表项）— ClassID: 2359312
│   ├── MusicSwitchContainer（音乐开关容器）— ClassID: 2293776
│   ├── MusicTrack（音乐轨道）— ClassID: 1835024
│   ├── MusicTrackSequence（音乐轨道序列）— ClassID: 3801104
│   ├── MusicClip（音乐片段）— ClassID: 3932176
│   ├── MusicClipMidi（MIDI 音乐片段）— ClassID: 4063248
│   ├── MusicCue（音乐提示点）— ClassID: 3866640
│   ├── MusicEventCue（音乐事件提示点）— ClassID: 5046288
│   ├── MusicFade（音乐淡入淡出）— ClassID: 2555920
│   ├── MusicStinger（音乐 Stinger）— ClassID: 2490384
│   └── MusicTransition（音乐过渡）— ClassID: 2424848
│
├── 总线与效果器（Bus & Effect Objects）
│   ├── Bus（总线）— ClassID: 1376272
│   ├── AuxBus（辅助总线）— ClassID: 3997712
│   ├── AudioDevice（音频设备）— ClassID: 4653072
│   ├── Effect（效果器）— ClassID: 1114128
│   ├── EffectSlot（效果器插槽）— ClassID: 5505040
│   └── Attenuation（衰减）— ClassID: 2686992
│
├── 事件与动作（Event & Action Objects）
│   ├── Event（事件）— ClassID: 262160
│   ├── Action（动作）— ClassID: 327696
│   ├── ActionException（动作异常）— ClassID: 4980752
│   └── DialogueEvent（对话事件）— ClassID: 3014672
│
├── 游戏同步对象（Game Sync Objects）
│   ├── GameParameter（游戏参数）— ClassID: 1507344
│   ├── StateGroup（状态组）— ClassID: 458768
│   ├── State（状态）— ClassID: 393232
│   ├── SwitchGroup（开关组）— ClassID: 1245200
│   ├── Switch（开关）— ClassID: 1310736
│   ├── Trigger（触发器）— ClassID: 2621456
│   └── RTPC（实时参数控制）— ClassID: 1441808
│
├── 工程组织对象（Project Organization Objects）
│   ├── Project（工程）— ClassID: 196624
│   ├── WorkUnit（工作单元）— ClassID: 1638416
│   ├── Folder（文件夹）— ClassID: 131088
│   ├── Platform（平台）— ClassID: 4522000
│   └── Language（语言）— ClassID: 4915216
│
├── SoundBank 系统
│   ├── SoundBank（声音库）— ClassID: 1179664
│   ├── ExternalSource（外部源）— ClassID: 3735568
│   ├── ExternalSourceFile（外部源文件）— ClassID: 3670032
│   └── Conversion（转换设置）— ClassID: 3604496
│
├── 调制器与修饰器（Modulator & Modifier）
│   ├── ModulatorEnvelope（包络调制器）— ClassID: 4259856
│   ├── ModulatorLfo（LFO 调制器）— ClassID: 4194320
│   ├── ModulatorTime（时间调制器）— ClassID: 5111824
│   └── Modifier（修饰器）— ClassID: 983056
│
└── 其他对象
    ├── AcousticTexture（声学材质）— ClassID: 4718608
    ├── Curve（曲线）— ClassID: 917520
    ├── Panner（声像器）— ClassID: 2752528
    ├── Position（位置）— ClassID: 786448
    ├── Path2D（2D 路径）— ClassID: 720912
    ├── Query（查询）— ClassID: 2097168
    ├── SearchCriteria（搜索条件）— ClassID: 2162704
    ├── Metadata（元数据）— ClassID: 5308432
    ├── MultiSwitchEntry（多开关条目）— ClassID: 5439504
    ├── CustomState（自定义状态）— ClassID: 5177360
    ├── Marker（标记）— ClassID: 5373968
    ├── PluginDataSource（插件数据源）— ClassID: 3538960
    ├── ObjectSettingAssoc（对象设置关联）— ClassID: 1572880
    ├── MidiParameter（MIDI 参数）— ClassID: 4128784
    ├── MixingSession（混音会话）— ClassID: 3473424
    ├── SoundcasterSession（Soundcaster 会话）— ClassID: 1703952
    ├── ControlSurfaceSession（控制面板会话）— ClassID: 4325392
    ├── ControlSurfaceBinding（控制面板绑定）— ClassID: 4390928
    ├── ControlSurfaceBindingGroup（控制面板绑定组）— ClassID: 4456464
    └── UserProjectSettings（用户工程设置）— ClassID: 3342352
```

## 对象的三类数据

WAAPI 中每个 Wwise 对象包含三类数据：

### 1. 属性（Property）
对象的标量值，可以是**数值**、**字符串**或**布尔值**。通过 `ak.wwise.core.object.get` / `setProperty` 操作。

获取属性时的前缀约定：

| 前缀 | 含义 | 示例 |
|------|------|------|
| 无前缀（`PropertyName`）| 返回经 Override 系统解析后的值（推荐）| `"Volume"` |
| `@PropertyName` | 返回直接在对象上设置的值，忽略 Override | `"@Volume"` |
| `@@PropertyName` | 同上，返回解析后的值 | `"@@Volume"` |

### 2. 引用（Reference）
指向另一个 Wwise 对象的**指针**。通过 `ak.wwise.core.object.setReference` 设置，通过 `get` 获取时可链式访问目标对象的属性。

### 3. 列表（List）
对象的**子集合**，列表中的对象通常是同类型的。列表操作通过 `listMode`（`append` / `replaceAll`）控制。

## 相关函数参考

| 函数 | 说明 |
|------|------|
| `ak.wwise.core.object.get` | 获取对象数据（属性/引用/列表） |
| `ak.wwise.core.object.create` | 创建对象 |
| `ak.wwise.core.object.setProperty` | 设置属性 |
| `ak.wwise.core.object.setReference` | 设置引用 |
| `ak.wwise.core.object.getTypes` | 获取所有对象类型列表 |
| `ak.wwise.core.object.getPropertyInfo` | 获取属性信息 |
| `ak.wwise.core.object.delete` | 删除对象 |
| `ak.wwise.core.object.move` | 移动对象 |
| `ak.wwise.core.object.copy` | 复制对象 |

## 章节索引

| 章节 | 内容 |
|------|------|
| [01-声音对象](01-声音对象.md) | Sound、AudioFileSource、SourcePlugin、MotionSource、MidiFileSource |
| [02-容器对象](02-容器对象.md) | ActorMixer、RandomSequenceContainer、SwitchContainer、BlendContainer、BlendTrack |
| [03-音乐对象](03-音乐对象.md) | MusicSegment、MusicPlaylistContainer、MusicSwitchContainer、MusicTrack、MusicClip 等 |
| [04-总线与效果器](04-总线与效果器.md) | Bus、AuxBus、AudioDevice、Effect、EffectSlot、Attenuation |
| [05-事件与动作](05-事件与动作.md) | Event、Action、ActionException、DialogueEvent |
| [06-游戏同步与工程对象](06-游戏同步与工程对象.md) | GameParameter、StateGroup、SwitchGroup、Trigger、RTPC + WorkUnit、Folder、Platform、Language、SoundBank |

## 官方文档链接

- [Wwise SDK 文档](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=index.html)
- WAAPI 运行时获取类型：`ak.wwise.core.object.getTypes`
- WAAPI 运行时获取属性信息：`ak.wwise.core.object.getPropertyInfo`
