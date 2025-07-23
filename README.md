
# 🦅 鹰眼：智慧畜牧巡检系统  
> 基于无人机载多模态融合增强与文心大模型的智能化解决方案

[![License](https://img.shields.io/github/license/forever218/Eagle-eye?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/forever218/Eagle-eye?style=flat-square)](https://github.com/forever218/Eagle-eye/stargazers)
[![Issues](https://img.shields.io/github/issues/forever218/Eagle-eye?style=flat-square)](https://github.com/forever218/Eagle-eye/issues)



## 📌 项目简介

**“鹰眼”**是一套集成了**无人机巡检系统**、**多模态感知技术**与**大语言模型智能分析**的智慧畜牧解决方案。该系统可实现对牧场环境和牲畜状态的**高效监控**与**自动化分析**，显著提升畜牧业管理的智能化与自动化水平。

> 🧠 本项目融合了计算机视觉、遥感图像处理、LLM 智能问答、多模态数据融合、语义分析、目标检测等前沿技术。

| 功能点/创新点               | 技术应用                                      | 进展     |
|----------------------------|-----------------------------------------------|----------|
| 图像去雾增强               | DCP、CLAHE、Wavelet                           | 已部署   |
| 强度-偏振双模协同          | Stokes Vectors、Laplacian Pyramid             | 已部署   |
| 多相机同步触发与并行采集   | DDS 信号发生器                               | 已部署   |
| 三模态的图像配准           | Lightblue、Superpoint、Rasanc                 | 训练完毕 |
| 偏振-RGB-红外三模态融合    | Swin Transformer                              | 训练中   |



## ✨ 核心功能

- 🚁 **无人机自主巡检**：基于 GPS 路径规划的自动飞行，覆盖牧场全区域。
- 👁 **多模态感知增强**：集成 RGB、热红外、语音、环境传感器等多种传感器。
- 🧮 **智能识别分析**：结合 YOLO 系列模型与文心大模型，实现牲畜计数、行为识别、健康监测等。
- 🌐 **图文语义问答**：通过自然语言与文心对话，支持巡检总结、数据查询等功能。
- 📊 **可视化平台**：提供 Web 可视化面板，实时显示巡检轨迹、识别结果和异常告警。



## 🧠 技术架构 | Tech Stack

| 模块 | 技术栈 |
|------|--------|
| 无人机平台 | DJI SDK / 自主平台 + ROS |
| 感知算法 | YOLOv8 / 多模态融合 / OpenCV / PaddlePaddle |
| 大语言模型 | 文心大模型（ERNIE-Bot）|
| 后端服务 | Python / FastAPI / Flask |
| 前端展示 | Vue / Echarts / Cesium |
| 数据平台 | MongoDB / InfluxDB / Redis |

---

## 📸 系统截图 | Demo Screenshots

> 🚧 *开发中，敬请期待系统截图...*

---

## 🚀 快速开始 | Getting Started

### 环境依赖

```bash
Python >= 3.8
paddlepaddle
opencv-python
flask / fastapi
requests
```




