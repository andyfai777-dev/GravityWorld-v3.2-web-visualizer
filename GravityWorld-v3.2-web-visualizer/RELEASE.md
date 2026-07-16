# Release Notes — v3.2.0

## [中文]

### 🎉 GravityWorld v3.2 Web Visualizer 正式发布

这是 GravityWorld 的**首个开源版本**——一个完全离线、单文件 HTML 的叙事推演可视化前端，内置完整的 v3.2 高斯引力引擎。

### 核心功能

- **🔌 完全离线运行**：无需 Python、无需后端、无需网络，浏览器直接打开即用
- **🚀 内置推演引擎**：完整移植 MetaRule、GravityFactor、Character、FactionManager 等核心模型
- **📊 6 大分析面板**：原始数据、轨迹演化、关系网络、势力分析、事件时间线、物理引擎
- **⏱️ 动态时间轴**：时间滑块 + 播放/暂停，实时查看任意步数的推演状态
- **🎛️ 实时筛选**：角色与势力的勾选状态即时影响所有图表渲染
- **💾 导出功能**：支持推演结果导出为 JSON 与 CSV

### 技术亮点

- 单文件 `index.html`（约 930 行），纯原生 HTML/CSS/JS，零框架依赖
- ECharts 5.4.3 本地离线图表库（Graph / Line / Bar / Radar / Heatmap / Scatter）
- 完整实现高斯引力衰减模型：`F = G·m₁·m₂·sim·peak·(r/R)·exp(-(r/R)²)`
- 势力动态隶属分配与叛变检测（基于余弦相似度与戏剧权重）

### 快速开始

1. 下载本仓库，用浏览器打开 `index.html`
2. 点击右上角「加载配置 JSON」，选择 `config/example_v32.json`
3. 在左侧面板设置推演步数，点击「运行推演」
4. 切换标签页，拖动时间滑块查看动态演化

### 配置示例

内置两个示例配置：
- `config/example_v32.json` — 基础演示数据
- `config/romeo_juliet_v32.json` — 罗密欧与朱丽叶经典案例

### 关于开源策略

GravityWorld v3.2 是**社区版/教学版**（Community Edition）。核心高斯引力模型与基础推演引擎在此版本中完全开源，采用 **MIT 许可证**。

后续 **GravityWorld 5.0**（高级引擎）与 **NarrativeWave**（产品化应用）为独立开发的进阶版本，不在本仓库开源范围内。

### 兼容性

- ✅ Chrome 90+
- ✅ Edge 90+
- ✅ Firefox 90+
- ⚠️ 不支持 IE

---

## [English]

### 🎉 GravityWorld v3.2 Web Visualizer — Official Release

This is the **first open-source release** of GravityWorld — a fully offline, single-file HTML visualization frontend with a complete v3.2 Gaussian gravity narrative engine built in.

### Key Features

- **🔌 Fully Offline**: No Python, no backend, no network required — open `index.html` in any browser and go
- **🚀 Built-in Engine**: Full port of MetaRule, GravityFactor, Character, FactionManager, and the complete `evolve_full` pipeline
- **📊 6 Analytics Panels**: Raw Data, Trajectory, Network, Faction, Events, Physics
- **⏱️ Dynamic Timeline**: Drag the slider or hit play/pause to inspect any step of the evolution
- **🎛️ Real-time Filtering**: Character and faction checkboxes instantly update all charts
- **💾 Export**: Evolution results exportable as JSON and CSV

### Technical Highlights

- Single `index.html` (~930 lines), pure native HTML/CSS/JS, zero framework dependencies
- ECharts 5.4.3 offline charting library (Graph / Line / Bar / Radar / Heatmap / Scatter)
- Full Gaussian gravity decay model: `F = G·m₁·m₂·sim·peak·(r/R)·exp(-(r/R)²)`
- Dynamic faction affiliation assignment and defection detection (cosine similarity + dramatic/surprise weights)

### Quick Start

1. Download this repository and open `index.html` in your browser
2. Click "加载配置 JSON" in the top-right, select `config/example_v32.json`
3. Set evolution steps in the left sidebar, click "▶ 运行推演"
4. Switch tabs and drag the timeline slider to explore the dynamics

### Example Configs

Two built-in demo configurations:
- `config/example_v32.json` — Basic demo data
- `config/romeo_juliet_v32.json` — Classic Romeo & Juliet case study

### Open Source Strategy

GravityWorld v3.2 is the **Community / Teaching Edition**. The core Gaussian gravity model and basic evolution engine are fully open-sourced under the **MIT License**.

**GravityWorld 5.0** (advanced engine) and **NarrativeWave** (productized application) are separately developed advanced versions and are **not** part of this open-source repository.

### Compatibility

- ✅ Chrome 90+
- ✅ Edge 90+
- ✅ Firefox 90+
- ⚠️ IE not supported

---

<p align="center">GravityWorld · 高斯引力叙事模型 · Gaussian Gravity Narrative Model</p>
