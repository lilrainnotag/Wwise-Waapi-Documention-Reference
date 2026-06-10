# ak.wwise.core.object.setAttenuationCurve

> **命名空间**: ak.wwise.core.object

## 概述

为指定衰减对象设置衰减曲线。

## 参数

| 名称 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| object | any of | 是 | - | 衰减对象的ID (GUID)、名称或路径 |
| platform | any of | 否 | - | 要设置曲线的平台ID (GUID) 或名称。设为null-guid设置非链接曲线 |
| curveType | string | 是 | - | 衰减曲线类型。可选值同 getAttenuationCurve（VolumeDryUsage, VolumeWetGameUsage, LowPassFilterUsage, SpreadUsage 等19种） |
| use | string | 是 | - | 曲线使用方式。可选值: None（无点）, Custom（自定义点集）, UseVolumeDry（使用VolumeDryUsage曲线）, UseProject（使用项目默认） |
| points | array | 是 | - | 衰减曲线的点数组 |
| points[...].x | number | 是 | - | 曲线点的X坐标 |
| points[...].y | number | 是 | - | 曲线点的Y坐标 |
| points[...].shape | string | 是 | - | 曲线段形状。可选值: Constant, Linear, Log3, Log2, Log1, InvertedSCurve, SCurve, Exp1, Exp2, Exp3 |

## 返回值

（官网未提供 - 成功执行即表示操作完成）

## JSON-RPC 请求示例

### 示例：定义对象的衰减曲线

```json
{
    "method": "ak.wwise.core.object.setAttenuationCurve",
    "params": {
        "object": "{AABBCC00-1122-3344-5566-77889900AABB}",
        "curveType": "VolumeDryUsage",
        "use": "Custom",
        "points": [
            {
                "x": 0.0,
                "y": 0.0,
                "shape": "Linear"
            },
            {
                "x": 50.0,
                "y": -12.0,
                "shape": "Log3"
            },
            {
                "x": 100.0,
                "y": -96.0,
                "shape": "Linear"
            }
        ]
    }
}
```

## 注意事项

- 所有三个字段（object, curveType, use, points）均为必填
- `use` 为 "Custom" 时必须提供 points 数组
- `use` 为 "None" 时，曲线被禁用
- `use` 为 "UseVolumeDry" 或 "UseProject" 时，points 参数可以传空数组
- Curve 点至少需要2个点才能定义完整的曲线段

## 相关函数

- ak.wwise.core.object.getAttenuationCurve

## 相关Topic

（官网未提供）

## 官方文档链接

- 主文档: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setAttenuationCurve.html
- 示例: https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_object_setattenuationcurve_example_defining_an_attenuation_curve_of_an_object.html
