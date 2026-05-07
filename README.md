# UE5 Physically Based Lighting (PBL) Complete Reference

一份基于真实世界照度数据的 **Unreal Engine 5 物理灯光工作流参考手册**，涵盖从晴天正午到雷暴沙暴的全场景、全参数对照。

🔗 **在线查看：https://samuelclex.github.io/UE5-PBL/

---

## 这是什么

在 UE5 中使用物理灯光 (PBL) 工作流时，需要同时协调 Directional Light、Sky Light、Sky Atmosphere、雾效、反射、曝光、后处理等大量参数，而这些参数会随时段和天气条件剧烈变化。

这份参考手册将 **所有相关参数统一整合到每个场景卡片中**——选中一个时段或天气条件，即可一次查看该条件下全部六大系统的推荐数值，无需在多个文档之间跳转。

## 包含场景

### 时段
| 场景 | Directional Light | EV100 | 特征 |
|------|-------------------|-------|------|
| ☀️ 正午 | 100,000–120,000 lux | 14–16 | 最强光照，硬影，16:1 对比度 |
| 🌅 黄金时刻 | 10,000–40,000 lux | 12–14 | 暖橙色，God Rays，电影感最佳 |
| 🌄 清晨 | 400–1,000 lux | 9–12 | 深橙红，晨雾，柔和过渡 |
| 🌇 黄昏 | 400–1,000 lux | 9–12 | 比清晨更红更饱和 |
| 🌆 暮光 | 1–400 lux | 5–9 | Blue Hour，人工灯成为主角 |
| 🌙 夜晚 | 0.1–0.5 lux（月光） | -6–-2 | 最难场景，50 万倍亮度差 |

### 天气
| 场景 | Directional Light | Mie Scale | 核心特征 |
|------|-------------------|-----------|----------|
| ☁️ 阴天 | 1,000–20,000 lux | 5–10 | Sky Light 成主光源，无影 |
| 🌧️ 雨天 | 1,000–8,000 lux | 6–12 | 湿润反射（Roughness 0.05–0.15） |

### 极端天气
| 场景 | Directional Light | Mie Scale | 核心特征 |
|------|-------------------|-----------|----------|
| ⛈️ 雷暴 | 500–5,000（基础）/ 80,000+（闪电） | 8–15 | 闪电脉冲系统，三种实现方案 |
| 🏜️ 沙暴 | 5,000–30,000 lux | 10–20 | 橙色统治一切，Niagara 沙尘粒子 |
| ❄️ 暴风雪 | 2,000–10,000 lux | 8–15 | 高亮度低对比度，Ground Albedo 0.8+ |

## 每个场景包含的参数模块

```
光源          Directional Light (Lux / 色温 / 角度 / Soft Angle / Light Shaft)
              Sky Light (Intensity / 颜色 / Real Time Capture)

天空大气      Rayleigh (Scale / Color / Height)
              Mie (Scale / Color / Height / Anisotropy / Absorption)
              Multi Scattering / Ground Albedo / Absorption Scale

雾效          Height Fog (Density / Falloff / Inscattering Color / Start Distance / Second Layer)
              Volumetric Fog (Extinction Scale / Scattering Distribution / Albedo)

反射          该天气下的反射特征 / Wetness / Roughness 调整建议

曝光          EV100 / 光圈 / 快门 / ISO / 曝光补偿

后处理        Bloom / Lens Flare / Vignette / Saturation / Color Grading / 额外效果
```

## 其他功能页

- **🪞 反射系统** — Lumen Reflections / SSR / Reflection Captures 三层回退方案详解
- **💡 灯光单位** — UE5 各 Actor 物理单位对照 + 常见室内光源参考值 + 色温色带
- **🔢 公式换算** — EV100 / Lux→EV / UE 曝光公式 + 交互式计算器
- **📋 工作流** — 9 步 PBL 搭建流程 + 常见陷阱 + 完整参数关系链

## 数据来源

- [Epic Games 官方文档 — Physical Lighting Units](https://dev.epicgames.com/documentation/en-us/unreal-engine/using-physical-lighting-units-in-unreal-engine)
- [PBL Database — Arthur Tasquin (80 Level)](https://80.lv/articles/get-started-with-physically-based-lighting-in-ue5-with-pbl-database)
- [Magnopus — Lighting in Unreal with PBL](https://www.magnopus.com/blog/lighting-in-unreal-with-photography-principles)
- [Silicon Studio — Physically-based lighting with Enlighten and UE4](https://www.siliconstudio.co.jp/middleware/enlighten/en/blog/2019/20190322/)
- [Wikipedia — Exposure Value](https://en.wikipedia.org/wiki/Exposure_value)
- [NVIDIA GPU Gems 2 — Accurate Atmospheric Scattering](https://developer.nvidia.com/gpugems/gpugems2/part-ii-shading-lighting-and-shadows/chapter-16-accurate-atmospheric-scattering)

## 使用方式

纯静态 HTML，无外部依赖（仅 Google Fonts），直接浏览器打开即可使用：

```bash
# 本地打开
open index.html

# 或部署到 GitHub Pages
git add index.html
git commit -m "UE5 PBL Reference v3"
git push
```

## 说明

所有数值为 **参考范围**，实际使用时需根据项目艺术方向调整。PBL 工作流的核心原则是「先掌握规则，再打破规则」——物理正确的数值提供一致的起点，艺术化的偏移创造独特的视觉风格。

---

MIT License
