# GravityWorld v3.2 Web Visualizer

<p align="center">
  <b>离线叙事推演可视化引擎 · 单文件 HTML 即开即用</b><br>
  <b>Offline Narrative Evolution Engine · Single-file HTML, Zero Dependencies</b>
</p>

<p align="center">
  <a href="https://github.com/yourusername/gravityworld-v3.2-web/blob/main/README.md">中文</a> |
  <a href="#english">English</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/browser-Chrome%20%7C%20Edge%20%7C%20Firefox-green.svg" alt="Browser">
  <img src="https://img.shields.io/badge/engine-Gaussian%20Gravity-orange.svg" alt="Engine">
</p>

---

## 简介 / Introduction

**GravityWorld** 是一个基于**高斯引力模型**的叙事推演系统。它将角色建模为 4 维向量空间中的粒子，通过引力相互作用模拟角色价值观的演化、势力归属的变化以及关键剧情节点的涌现。

本项目是 GravityWorld **v3.2 社区版**的 Web 可视化前端——**完全离线**，**单文件 HTML**，内置完整 JavaScript 推演引擎，浏览器打开即可运行。

> **GravityWorld** is a narrative evolution system based on the **Gaussian Gravity Model**. It models characters as particles in a 4D vector space and simulates value evolution, faction dynamics, and emergent plot events through gravitational interactions.
>
> This repository contains the **v3.2 Community Edition** Web visualizer — **fully offline**, **single-file HTML**, with a complete JavaScript evolution engine built-in. Open in browser and run.

---

## 快速开始 / Quick Start

```bash
# 1. 下载 / Clone
git clone https://github.com/yourusername/gravityworld-v3.2-web.git

# 2. 打开 / Open
# 直接用浏览器打开 index.html（无需服务器）
# Simply open index.html in your browser (no server needed)
```

1. 点击右上角「加载配置 JSON」/ Click "加载配置 JSON"
2. 选择 `config/example_v32.json` 或 `romeo_juliet_v32.json`
3. 设置推演步数（10–200），点击「▶ 运行推演」
4. 切换 6 大标签页，拖动时间滑块查看动态演化

---

## 功能特性 / Features

| 特性 / Feature | 说明 / Description |
|----------------|-------------------|
| 🔌 **完全离线 / Fully Offline** | 单文件 `index.html` + `echarts.min.js`，无网络依赖 |
| 🚀 **内置引擎 / Built-in Engine** | 完整 v3.2 推演：MetaRule、GravityFactor、Character、FactionManager |
| 📊 **8 面板可视化 / 8-Panel Viz** | 轨迹、网络、势力、事件、物理、原始数据 |
| ⏱️ **时间滑块 / Timeline Slider** | 任意步数回放，支持播放/暂停 |
| 🎛️ **动态筛选 / Dynamic Filter** | 角色/势力勾选实时影响全部图表 |
| 💾 **导出 / Export** | JSON + CSV 推演结果导出 |

---

## 6 大分析面板 / 6 Analytics Panels

| 标签页 / Tab | 内容 / Content |
|-------------|---------------|
| 📋 **原始数据 / Raw Data** | 配置表、MetaRule 参数、当前步数据、余弦/引力热力图 |
| 📈 **轨迹演化 / Trajectory** | 4D 向量投影轨迹、雷达图 |
| 🕸️ **关系网络 / Network** | 角色关系网络（共振/冲突/中性）、势力隶属网络 |
| 🏛️ **势力分析 / Faction** | 牵引力分解 stacked bar、兴衰动态 area line |
| ⚡ **事件时间线 / Events** | 叛变事件、锚点事件散点图、动态检测表 |
| 🔬 **物理引擎 / Physics** | 高斯力曲线 `F = G·m₁·m₂·sim·peak·(r/R)·exp(-(r/R)²)`、艺术节奏曲线 |

---

## 配置格式 / Configuration

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
  ]
}
```

---

## 文件结构 / File Structure

```
├── index.html          # 主文件：UI + 内置 JS 引擎 (~930 lines)
├── js/
│   └── echarts.min.js  # ECharts 5.4.3 离线库
├── config/
│   ├── example_v32.json
│   └── romeo_juliet_v32.json
├── LICENSE             # MIT
└── README.md
```

---

## 浏览器兼容性 / Browser Compatibility

- ✅ Chrome 90+
- ✅ Edge 90+
- ✅ Firefox 90+
- ⚠️ IE not supported

---

## 技术细节 / Technical Details

- **前端 / Frontend**：纯原生 HTML/CSS/JS，无框架依赖
- **图表库 / Charting**：ECharts 5.4.3（Graph / Line / Bar / Radar / Heatmap / Scatter）
- **物理引擎 / Physics**：高斯引力模型 `r_norm * exp(-r_norm²)`
- **势力管理 / Factions**：余弦相似度隶属分配、叛变检测（戏剧权重调节阈值）

---

## 许可证 / License

本项目采用 **MIT 许可证** 开源。

> **注意 / Note**：GravityWorld v3.2 是"社区版/教学版"（Community Edition）。后续 **GravityWorld 5.0** 及 **NarrativeWave** 为独立开发的进阶版本，不在本仓库开源范围内。
>
> GravityWorld v3.2 is the "Community/Teaching Edition". **GravityWorld 5.0** and **NarrativeWave** are separately developed advanced versions and are not part of this open-source repository.

详见 [LICENSE](./LICENSE)。

---

<p align="center">
  <b>GravityWorld · 高斯引力叙事模型 · Gaussian Gravity Narrative Model</b>
</p>
