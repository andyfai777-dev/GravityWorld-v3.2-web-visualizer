# GravityWorld v3.2 Web Visualizer

<p align="center">
  <b>离线叙事推演可视化引擎 · 单文件 HTML 即开即用</b><br>
  <b>Offline Narrative Evolution Engine · Single-file HTML, Zero Dependencies</b>
</p>

<p align="center">
  <a href="#中文">中文</a> |
  <a href="#english">English</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/browser-Chrome%20%7C%20Edge%20%7C%20Firefox-green.svg" alt="Browser">
  <img src="https://img.shields.io/badge/engine-Gaussian%20Gravity-orange.svg" alt="Engine">
</p>

---

<h2 id="中文">中文</h2>

### 简介

**GravityWorld** 是一个基于**高斯引力模型**的叙事推演系统。它将角色建模为 4 维向量空间中的粒子，通过引力相互作用模拟角色价值观的演化、势力归属的变化以及关键剧情节点的涌现。

本项目是 GravityWorld **v3.2 社区版**的 Web 可视化前端——**完全离线**，**单文件 HTML**，内置完整 JavaScript 推演引擎，浏览器打开即可运行。

### 核心特性

| 特性 | 说明 |
|------|------|
| 🔌 **完全离线** | 单文件 `index.html` + 本地 `echarts.min.js`，无网络依赖 |
| 🚀 **内置推演引擎** | 完整移植 v3.2 计算层：MetaRule、GravityFactor、Character、FactionManager、`evolve_full` |
| 📊 **8 面板可视化** | 6 大标签页覆盖轨迹、网络、势力、事件、物理、原始数据 |
| ⏱️ **时间滑块** | 拖动查看任意步数状态，支持播放/暂停自动演化 |
| 🎛️ **动态筛选** | 角色勾选、势力勾选实时影响所有图表渲染 |
| 💾 **导出** | 支持导出推演结果 JSON 与 CSV |

### 快速开始

```bash
# 1. 下载
git clone https://github.com/yourusername/gravityworld-v3.2-web.git

# 2. 打开
# 直接用浏览器打开 index.html（无需服务器）
```

1. 点击右上角「加载配置 JSON」，选择 `config/example_v32.json` 或 `romeo_juliet_v32.json`
2. 在左侧控制面板设置推演步数（10–200），点击「▶ 运行推演」
3. 切换 6 大标签页浏览分析面板，拖动时间滑块查看动态演化

### 6 大分析面板

| 标签页 | 内容 |
|--------|------|
| 📋 **原始数据** | 角色/势力配置表、MetaRule 参数、当前步数据表、余弦相似度热力图、引力 F 热力图 |
| 📈 **轨迹演化** | 4D 向量投影轨迹（Dim 1 × Dim 2）、当前步雷达图 |
| 🕸️ **关系网络** | 角色关系网络（共振/冲突/中性连线）、势力隶属网络（中心–成员结构） |
| 🏛️ **势力分析** | 势力牵引力分解（stacked bar，按角色与势力 field_vector 相似度加权）、势力兴衰动态（area line + 当前步 markLine） |
| ⚡ **事件时间线** | 叛变事件 + 锚点事件散点图、动态锚点检测表 |
| 🔬 **物理引擎** | 高斯力曲线（`F = G·m₁·m₂·sim·peak·(r/R)·exp(-(r/R)²)`）、艺术节奏曲线（dramatic / surprise / theme） |

### 配置 JSON 格式

```json
{
  "meta_rules": {
    "G": 1.0, "gamma": 2.0, "dt": 0.01,
    "distance_scale": 1.5, "peak_force": 3.0,
    "factor_mass_coeff": 5.0,
    "dim_weights": [1, 1, 1, 1]
  },
  "characters": [
    { "name": "Romeo", "mass": 0.6, "plasticity": 0.5,
      "vector": [-0.8, 0.6, 0.7, -0.3],
      "affiliations": { "Montague": 0.9 } }
  ],
  "gravity_factors": [
    { "name": "Montague", "mass": 0.7,
      "field_params": { "vector": [-0.5, 0.3, 0.4, -0.2] } }
  ],
  "anchors": [
    { "step": 20, "name": "冲突爆发", "effect": { "character": "Romeo", "vector_delta": [0.3, -0.2, 0, 0] } }
  ],
  "art_weights": { "dramatic": 0.5, "surprise": 0.5, "theme": 0.5 }
}
```

### 文件结构

```
├── index.html          # 主文件：前端 UI + 内置 JS 推演引擎（930 行）
├── js/
│   └── echarts.min.js  # ECharts 5.4.3 本地离线库
├── config/
│   ├── example_v32.json
│   └── romeo_juliet_v32.json
├── LICENSE             # MIT
└── README.md
```

### 浏览器兼容性

- ✅ Chrome 90+
- ✅ Edge 90+
- ✅ Firefox 90+
- ⚠️ 不支持 IE

### 技术细节

- **前端框架**：纯原生 HTML/CSS/JS，无 React/Vue 依赖
- **图表库**：ECharts 5.4.3（Graph / Line / Bar / Radar / Heatmap / Scatter）
- **物理引擎**：完整移植 Python 版高斯引力模型（`r_norm * exp(-r_norm²)` 高斯衰减）
- **势力管理**：动态隶属分配（余弦相似度 > 0.4）、叛变检测（loyalty threshold + dramatic/surprise 权重）

### 许可证

本项目采用 **MIT 许可证** 开源。

> **注意**：GravityWorld v3.2 是"社区版/教学版"（Community Edition），核心高斯引力模型和基础推演引擎在此版本中完全开源。后续 **GravityWorld 5.0** 及 **NarrativeWave** 产品为独立开发的进阶版本，不在本仓库开源范围内。

详见 [LICENSE](./LICENSE) 文件。

---

<h2 id="english">English</h2>

### Introduction

**GravityWorld** is a narrative evolution system based on the **Gaussian Gravity Model**. It models characters as particles in a 4D vector space and simulates value evolution, faction dynamics, and emergent plot events through gravitational interactions.

This repository contains the **v3.2 Community Edition** Web visualizer — **fully offline**, **single-file HTML**, with a complete JavaScript evolution engine built-in. No Python, no backend, no network required — just open `index.html` in your browser and run.

### Key Features

| Feature | Description |
|---------|-------------|
| 🔌 **Fully Offline** | Single `index.html` + local `echarts.min.js`, zero network dependency |
| 🚀 **Built-in Engine** | Full v3.2 compute layer port: MetaRule, GravityFactor, Character, FactionManager, `evolve_full` |
| 📊 **8-Panel Analytics** | 6 tabs covering trajectory, network, faction, events, physics, and raw data |
| ⏱️ **Timeline Slider** | Drag to inspect any step; supports play/pause auto-evolution |
| 🎛️ **Dynamic Filtering** | Character/faction checkboxes affect all charts in real time |
| 💾 **Export** | JSON and CSV export of evolution results |

### Quick Start

```bash
# 1. Clone
git clone https://github.com/yourusername/gravityworld-v3.2-web.git

# 2. Open
# Simply open index.html in your browser (no server needed)
```

1. Click "加载配置 JSON" in the top-right, select `config/example_v32.json` or `romeo_juliet_v32.json`
2. Set evolution steps (10–200) in the left sidebar, click "▶ 运行推演"
3. Switch between 6 tabs and drag the timeline slider to see dynamic evolution

### 6 Analytics Panels

| Tab | Content |
|-----|---------|
| 📋 **Raw Data** | Character/faction config tables, MetaRule params, live step data, cosine similarity heatmap, gravity F heatmap |
| 📈 **Trajectory** | 4D vector projection (Dim 1 × Dim 2), current-step radar chart |
| 🕸️ **Network** | Character relationship graph (resonance/conflict/neutral edges), faction affiliation graph (center–member structure) |
| 🏛️ **Faction** | Faction pull decomposition (stacked bar, weighted by character–field_vector cosine similarity), faction rise/fall dynamics (area line + current-step markLine) |
| ⚡ **Events** | Defection + anchor event scatter timeline, dynamic anchor detection table |
| 🔬 **Physics** | Gaussian force curve (`F = G·m₁·m₂·sim·peak·(r/R)·exp(-(r/R)²)`), art rhythm curves (dramatic / surprise / theme) |

### Configuration JSON Format

```json
{
  "meta_rules": {
    "G": 1.0, "gamma": 2.0, "dt": 0.01,
    "distance_scale": 1.5, "peak_force": 3.0,
    "factor_mass_coeff": 5.0,
    "dim_weights": [1, 1, 1, 1]
  },
  "characters": [
    { "name": "Romeo", "mass": 0.6, "plasticity": 0.5,
      "vector": [-0.8, 0.6, 0.7, -0.3],
      "affiliations": { "Montague": 0.9 } }
  ],
  "gravity_factors": [
    { "name": "Montague", "mass": 0.7,
      "field_params": { "vector": [-0.5, 0.3, 0.4, -0.2] } }
  ],
  "anchors": [
    { "step": 20, "name": "Conflict Erupts", "effect": { "character": "Romeo", "vector_delta": [0.3, -0.2, 0, 0] } }
  ],
  "art_weights": { "dramatic": 0.5, "surprise": 0.5, "theme": 0.5 }
}
```

### File Structure

```
├── index.html          # Main file: UI + built-in JS evolution engine (~930 lines)
├── js/
│   └── echarts.min.js  # ECharts 5.4.3 offline library
├── config/
│   ├── example_v32.json
│   └── romeo_juliet_v32.json
├── LICENSE             # MIT
└── README.md
```

### Browser Compatibility

- ✅ Chrome 90+
- ✅ Edge 90+
- ✅ Firefox 90+
- ⚠️ IE not supported

### Technical Details

- **Frontend**: Pure native HTML/CSS/JS, no React/Vue dependency
- **Charting**: ECharts 5.4.3 (Graph / Line / Bar / Radar / Heatmap / Scatter)
- **Physics Engine**: Full port of Python Gaussian gravity model (`r_norm * exp(-r_norm²)` decay)
- **Faction Management**: Dynamic affiliation assignment (cosine similarity > 0.4), defection detection (loyalty threshold + dramatic/surprise weights)

### License

This project is open-sourced under the **MIT License**.

> **Note**: GravityWorld v3.2 is the "Community/Teaching Edition". The core Gaussian gravity model and basic evolution engine are fully open-sourced here. **GravityWorld 5.0** and **NarrativeWave** are separately developed advanced versions and are not part of this open-source repository.

See [LICENSE](./LICENSE) for details.

---

<p align="center">
  <b>GravityWorld · 高斯引力叙事模型 · Gaussian Gravity Narrative Model</b>
</p>
