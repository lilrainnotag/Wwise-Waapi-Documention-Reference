# ak.wwise.core.object.getAttenuationCurve

> **命名空间**: ak.wwise.core.object

## 概述

获取指定衰减对象的衰减曲线。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 衰减对象的ID (GUID)、名称或路径 |
| platform | any of | 否 | - | 要获取曲线的平台ID (GUID) 或名称。设为null-guid获取非链接引用 |
| curveType | string | 是 | - | 衰减曲线类型。可选值见下方 |

### curveType 可选值

| 值 | 说明 |
|------|------|
| VolumeDryUsage | 干声量 |
| VolumeWetGameUsage | 游戏湿声量 |
| VolumeWetUserUsage | 用户湿声量 |
| LowPassFilterUsage | 低通滤波 |
| HighPassFilterUsage | 高通滤波 |
| SpreadUsage | 扩散 |
| FocusUsage | 聚焦 |
| ObstructionVolumeUsage | 障碍音量 |
| ObstructionLPFUsage | 障碍低通滤波 |
| ObstructionHPFUsage | 障碍高通滤波 |
| OcclusionVolumeUsage | 遮蔽音量 |
| OcclusionLPFUsage | 遮蔽低通滤波 |
| OcclusionHPFUsage | 遮蔽高通滤波 |
| DiffractionVolumeUsage | 衍射音量 |
| DiffractionLPFUsage | 衍射低通滤波 |
| DiffractionHPFUsage | 衍射高通滤波 |
| TransmissionVolumeUsage | 传输音量 |
| TransmissionLPFUsage | 传输低通滤波 |
| TransmissionHPFUsage | 传输高通滤波 |

## 返回值

| 名称 | 类型 | 说明 |
|------|------|------|
| curveType | string | 衰减曲线的名称（同参数curveType值） |
| use | string | 定义曲线状态。可选值: None（无点）, Custom（自定义点集）, UseVolumeDry（使用VolumeDryUsage曲线）, UseProject（使用项目默认） |
| points | array | 衰减曲线的点数组 |
| points[...].x | number | 曲线点的X坐标 |
| points[...].y | number | 曲线点的Y坐标 |
| points[...].shape | string | 曲线段形状。可选值: Constant, Linear, Log3, Log2, Log1, InvertedSCurve, SCurve, Exp1, Exp2, Exp3 |

## JSON-RPC 请求示例

```json
{
    "method": "ak.wwise.core.object.getAttenuationCurve",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "curveType": "VolumeDryUsage"
    }
}
```

### JSON-RPC 响应示例

```json
{
    "curveType": "VolumeDryUsage",
    "use": "Custom",
    "points": [
        {
            "x": 0.0,
            "y": 0.0,
            "shape": "Linear"
        },
        {
            "x": 100.0,
            "y": -24.0,
            "shape": "Log3"
        }
    ]
}
```

## 注意事项

- `use` 为 "UseVolumeDry" 时，曲线使用 VolumeDryUsage 曲线的点
- `use` 为 "None" 时，曲线没有点（禁用状态）
- `use` 为 "UseProject" 时，使用项目默认设置

## 相关函数

- ak.wwise.core.object.setAttenuationCurve

## 相关Topic

（官网未提供）

## 官方文档链接

- https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_getAttenuationCurve.html
