# UE5 Physically Based Lighting — Complete Reference
# UE5 物理灯光 (PBL) — 完整参考手册

---

## What Is This / 这是什么

A reference handbook for Unreal Engine 5's Physically Based Lighting workflow, built on real-world illuminance data. Every scenario card shows all six parameter systems at once — no jumping between docs.

一份基于真实世界照度数据的 UE5 物理灯光工作流参考手册。每个场景卡片一次性展示全部六大参数系统——无需在多个文档之间跳转。

When working with PBL in UE5, you need to coordinate Directional Light, Sky Light, Sky Atmosphere, Fog, Reflections, Exposure, and Post Process simultaneously — and all of them shift dramatically with time of day and weather. This guide unifies everything into one place.

在 UE5 中使用 PBL 工作流时，需要同时协调 Directional Light、Sky Light、Sky Atmosphere、雾效、反射、曝光和后处理——它们会随时段和天气剧烈变化。本手册将一切统一整合在一处。

---

## Included Scenarios / 包含场景

### Time of Day / 时段

| Scenario / 场景 | Directional Light | EV100 | Key Feature / 特征 |
|---|---|---|---|
| ☀️ Midday / 正午 | 100,000–120,000 lux | 14–16 | Strongest light, hard shadows, 16:1 contrast / 最强光照，硬影 |
| 🌅 Golden Hour / 黄金时刻 | 10,000–40,000 lux | 12–14 | Warm orange, God Rays, peak cinematic / 暖橙，God Rays，电影感最佳 |
| 🌄 Sunrise / 清晨 | 400–1,000 lux | 9–12 | Deep orange-red, morning mist / 深橙红，晨雾 |
| 🌇 Sunset / 黄昏 | 400–1,000 lux | 9–12 | Redder and more saturated than sunrise / 比清晨更红更饱和 |
| 🌆 Twilight / 暮光 | 1–400 lux | 5–9 | Blue Hour, artificial lights take over / Blue Hour，人工灯为主 |
| 🌙 Night / 夜晚 | 0.1–0.5 lux (moon) | -6 to -2 | Hardest scenario, 500,000x brightness gap / 最难场景，50万倍亮度差 |

### Weather / 天气

| Scenario / 场景 | Directional Light | Mie Scale | Key Feature / 特征 |
|---|---|---|---|
| ☁️ Overcast / 阴天 | 1,000–20,000 lux | 5–10 | SkyLight becomes primary / SkyLight成主光源 |
| 🌧️ Rainy / 雨天 | 1,000–8,000 lux | 6–12 | Wet reflections (Roughness 0.05–0.15) / 湿润反射 |

### Extreme Weather / 极端天气

| Scenario / 场景 | Directional Light | Mie Scale | Key Feature / 特征 |
|---|---|---|---|
| ⛈️ Thunderstorm / 雷暴 | 500–5,000 base / 80,000+ lightning | 8–15 | Lightning pulse system, 3 methods / 闪电脉冲系统，三种方案 |
| 🏜️ Sandstorm / 沙暴 | 5,000–30,000 lux | 10–20 | Orange dominates everything / 橙色统治一切 |
| ❄️ Blizzard / 暴风雪 | 2,000–10,000 lux | 8–15 | High brightness, low contrast, Ground Albedo 0.8+ / 高亮度低对比度 |

---

## Parameters Per Scenario / 每个场景包含的参数

Each scenario card contains all six systems with recommended values:

每个场景卡片包含全部六大系统的推荐数值：

```
Light Sources       Directional Light (Lux / Color Temp / Angle / Soft Angle / Light Shaft)
光源                Sky Light (Intensity / Color / Real Time Capture)

Sky Atmosphere      Rayleigh (Scale / Color / Height)
天空大气            Mie (Scale / Color / Height / Anisotropy / Absorption)
                    Multi Scattering / Ground Albedo / Absorption Scale

Fog                 Height Fog (Density / Falloff / Inscattering Color / Start Distance / Second Layer)
雾效                Volumetric Fog (Extinction Scale / Scattering Distribution / Albedo)

Reflections         Weather-specific reflection behavior / Wetness / Roughness adjustment
反射                该天气下的反射特征 / 湿润度 / Roughness 调整

Exposure            EV100 / Aperture / Shutter / ISO / Exposure Compensation
曝光                EV100 / 光圈 / 快门 / ISO / 曝光补偿

Post Process        Bloom / Lens Flare / Vignette / Saturation / Color Grading / Extras
后处理              Bloom / 镜头光晕 / 暗角 / 饱和度 / 调色 / 额外效果
```

---

## Available Formats / 可用格式

| Format / 格式 | File / 文件 | Description / 说明 |
|---|---|---|
| 🌐 Interactive Web (CN) / 交互网页(中文) | `index.html` | Tabbed interface, scenario switcher, EV calculator / 标签页切换，场景选择器，EV计算器 |
| 📄 Word Document (CN) / Word文档(中文) | `ue5_pbl_reference.docx` | Full document with TOC, tables, info boxes / 完整文档含目录、表格、建议框 |
| 📄 Word Document (EN) / Word文档(英文) | `ue5_pbl_reference_en.docx` | English version for international community / 英文版本供国际社区使用 |

---

## Other Sections / 其他功能页

The interactive web version also includes these dedicated pages:

交互网页版还包含以下独立页面：

**🪞 Reflection System / 反射系统** — Lumen Reflections / SSR / Reflection Captures: the three-tier fallback explained with optimization tips.

Lumen Reflections / SSR / Reflection Captures 三层回退方案详解及优化要点。

**💡 Light Units / 灯光单位** — UE5 actor-to-unit mapping + common indoor light source reference + color temperature strip.

UE5 各 Actor 物理单位对照 + 常见室内光源参考值 + 色温色带。

**🔢 Formulas / 公式换算** — EV100 / Lux-to-EV / UE exposure formula + interactive calculator.

EV100 / Lux→EV / UE 曝光公式 + 交互式计算器。

**📋 Workflow / 工作流** — 9-step PBL setup process + common pitfalls + full parameter dependency chain.

9 步 PBL 搭建流程 + 常见陷阱 + 完整参数关系链。

---

## The Parameter Chain / 参数关系链

Understanding how parameters affect each other is the core of PBL:

理解参数之间的相互影响是 PBL 的核心：

```
Directional Light (Lux) → Absolute brightness → Determines EV100
DirLight(Lux) → 绝对亮度 → 决定 EV100

EV100 → Perceived screen brightness → Aperture / Shutter / ISO
EV100 → 画面亮度 → 光圈 / 快门 / ISO

Sky Light → Shadow fill → Ratio to DirLight = Contrast
SkyLight → 阴影填充 → 与 DirLight 的比值 = 对比度

Sky Atmosphere → Rayleigh = Sky color / Mie = Haze & scatter
天空大气 → Rayleigh = 天空颜色 / Mie = 雾霾散射

Height Fog → Atmospheric density / Volumetric = Light scattering
雾效 → 大气密度 / Volumetric = 光线散射

Reflections → Affected by all light sources / Roughness determines method
反射 → 受所有光源影响 / Roughness 决定反射方式

Full chain: Light → Exposure → Atmosphere → Fog → Reflections → Post Process
完整链路：光源 → 曝光 → 大气 → 雾 → 反射 → 后处理
```

---

## Usage / 使用方式

Pure static HTML with no external dependencies (Google Fonts only). Open directly in any browser:

纯静态 HTML，无外部依赖（仅 Google Fonts），直接浏览器打开：

```bash
# Local / 本地打开
open index.html

# Deploy to GitHub Pages / 部署到 GitHub Pages
git add index.html
git commit -m "UE5 PBL Reference v3"
git push
```

---

## Data Sources / 数据来源

- [Epic Games — Physical Lighting Units](https://dev.epicgames.com/documentation/en-us/unreal-engine/using-physical-lighting-units-in-unreal-engine)
- [PBL Database — Arthur Tasquin (80 Level)](https://80.lv/articles/get-started-with-physically-based-lighting-in-ue5-with-pbl-database)
- [Magnopus — Lighting in Unreal with Photography Principles](https://www.magnopus.com/blog/lighting-in-unreal-with-photography-principles)
- [Silicon Studio — Physically-based Lighting with Enlighten](https://www.siliconstudio.co.jp/middleware/enlighten/en/blog/2019/20190322/)
- [Wikipedia — Exposure Value](https://en.wikipedia.org/wiki/Exposure_value)
- [NVIDIA GPU Gems 2 — Accurate Atmospheric Scattering](https://developer.nvidia.com/gpugems/gpugems2/part-ii-shading-lighting-and-shadows/chapter-16-accurate-atmospheric-scattering)

---

## Disclaimer / 说明

All values are reference ranges. Adjust based on your project's artistic direction. The core principle of PBL is "learn the rules, then break them" — physically correct values provide a consistent starting point, and artistic deviation creates unique visual identity.

所有数值为参考范围，实际使用时需根据项目艺术方向调整。PBL 的核心原则是「先掌握规则，再打破规则」——物理正确的数值提供一致的起点，艺术化的偏移创造独特的视觉风格。

---

MIT License
