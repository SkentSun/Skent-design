# Fluidity — Three.js 流体粒子演示

## 简介

Fluidity 是一个基于 Three.js GPGPU 的实时流体粒子交互演示。数十万 GPU 粒子在 curl 噪声湍流场中持续流动，可实时切换形状（球体 / 立方体 / 圆环 / 苹果 / 耐克 SVG 模板，或上传自定义 SVG），并通过液态玻璃风格的控制面板调节湍流、黏度、辉光、旋转、发射强度、粒子尺寸等参数，呈现「流体可见化」的视觉体验。整套演示为纯前端单文件，开箱即用。

## 特性

- **GPU 粒子模拟**：基于 `GPUComputationRenderer` 的位置 / 速度计算着色器，支持 30 万 – 80 万粒子
- **多种形状**：球、立方、圆环三种解析 SDF，以及内置苹果 / 耐克 SVG 模板 + 任意 SVG 上传（自动转距离场约束壳）
- **流体观感**：curl 噪声湍流 + 速度衰减（黏度）+ 鼠标力场实时交互
- **色彩预设**：6 组渐变配色（含默认），点击即平滑过渡
- **液态玻璃 UI**：可拖拽设置弹窗、胶囊 tab、极简滚动条
- **响应式**：桌面与 9:16 手机竖屏均保持模型居中自适应
- **落地页**：`Fluidity, Made Tangible` 封面 + Play Now 进入 / Replay 返回

## 在线演示

> https://4a33da1d669e4c12adc62a5483406114.gz3.agentos-app.net

## 本地运行（用法）

**方式一：直接打开**

用现代浏览器打开 `particle_sphere_demo.html` 即可（需联网，Three.js 通过 CDN import map 加载）。

**方式二：本地静态服务器（推荐，避免 `file://` 下的 ES Module 限制）**

```bash
cd <项目目录>
python3 -m http.server 8000
# 然后浏览器访问 http://localhost:8000/particle_sphere_demo.html
```

## 操作说明

- **进入演示**：点击封面 `Play Now` 进入交互；右下角 `Replay` 可返回封面
- **切换形状**：底部胶囊 tab（Sphere / Cube / Torus / Apple / Nike），切换为溶解式平滑过渡
- **切换配色**：tab 上方 6 个圆点，点击即时切换渐变
- **参数调节**：右侧齿轮按钮打开可拖拽设置弹窗，调节湍流 / 黏度 / 辉光 / 旋转 / 发射 / 尺寸 / 粒子数 / 厚度 / 鼠标力等
- **交互**：移动鼠标产生力场扰动粒子；滚轮缩放视图

## 技术栈

- **Three.js**（ES Module via import map / unpkg CDN）
- **GPUComputationRenderer**：GPGPU 粒子模拟
- **自定义 GLSL 着色器**：位置 / 速度 / 渲染（含 SDF 约束壳、边界淡出、SVG 亮度补偿）
- 原生 **HTML / CSS / JS**，无构建步骤

## 文件结构

```
particle_sphere_demo.html   # 主演示文件（单文件自包含）
deploy/index.html           # 用于云端部署的同步副本
README.md                   # 本说明
.gitignore
```

## 许可

仅供学习与演示使用。
