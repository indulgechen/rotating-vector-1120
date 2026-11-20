# 旋转矢量与简谐运动 · 交互课件

面向大学物理「第九章 振动」的课堂演示，用旋转矢量（phasor）把简谐运动拆成两个同时发生的画面：

- 一个长度等于振幅 `A` 的矢量，以角速度 `ω` 匀速旋转；
- 矢量端点在 `x` 轴上的投影，随时间做简谐运动；
- 下方同步绘制投影点的 `x-t` 曲线。

页面使用原生 Canvas 2D 和原生 JavaScript，不依赖任何外部库、CDN 或网络资源，单个 `index.html` 即可离线运行。

![桌面端预览](assets/preview-desktop.png)

## 功能

- 旋转矢量与 `x-t` 曲线实时同步
- 可调振幅 `A = 2–10 cm`
- 可调角频率 `ω = 0.5–3.5 rad/s`
- 可调初相位 `φ = 0–360°`
- 初相位快捷预设：`0° / 90° / 180° / 270°`
- 投影辅助线、相位角显示开关
- 播放 / 暂停、时间归零、`0.25×–2×` 速度调节
- 实时读数：`t / θ / x / v / T`
- `x-t` 图使用滚动 `2T` 窗口，带 ±A 包络线和当前时刻标记
- 桌面端与移动端响应式布局
- 键盘操作：`Space` 暂停，`R` 时间归零，方向键调整初相位（±15°）

![手机端预览](assets/preview-mobile.png)

## 物理模型

简谐运动：

```text
x(t) = A cos(ωt + φ)
```

速度与加速度：

```text
v(t) = −Aω sin(ωt + φ)
a(t) = −ω² x(t)
```

周期：

```text
T = 2π / ω
```

旋转矢量的长度表示振幅 `A`，它与 `x` 轴正方向的夹角表示相位 `ωt + φ`，端点在 `x` 轴上的投影就是位移 `x(t)`。

## 操作

| 操作 | 效果 |
| --- | --- |
| 拖动 `A` 滑块 | 改变振幅 |
| 拖动 `ω` 滑块 | 改变角频率，并重置时间 |
| 拖动 `φ` 滑块 | 改变初相位，并重置时间 |
| 点击相位预设 | 快速切换到 0°、90°、180°、270° |
| 播放 / 暂停 | 控制动画 |
| 时间归零 | 将时间重置为 0，保留当前参数 |
| 速度滑块 | 调整动画播放速度 |
| `Space` | 暂停 / 播放 |
| `R` | 时间归零 |
| `←` / `→` | 初相位 ±15° |

## 文件结构

```text
.
├── index.html
├── README.md
├── .nojekyll
└── assets
    ├── preview-desktop.png
    └── preview-mobile.png
```

## 本地预览

直接双击 `index.html` 即可。也可以在目录中启动静态服务器：

```bash
python -m http.server 8000
```

然后访问 `http://localhost:8000/`。

## 部署到 GitHub Pages

1. 新建公开仓库，例如 `rotating-vector-shm`。
2. 将本目录中的 `index.html`、`README.md`、`.nojekyll` 和 `assets/` 上传到仓库根目录。
3. 打开仓库 **Settings → Pages**。
4. **Build and deployment** 选择：
   - Source：**Deploy from a branch**
   - Branch：**main**，目录 **/(root)**
5. 点击 **Save**，等待约 1 分钟。
6. 访问：

```text
https://<你的用户名>.github.io/rotating-vector-shm/
```

## 浏览器建议

建议使用较新的 Chrome、Edge、Firefox 或 Safari。页面使用 Canvas 2D、CSS Grid/Flex、`ResizeObserver` 和 Pointer Events，不支持 Internet Explorer。

## 说明

- 本页面为独立打包版本，原文件《旋转矢量与简谐运动-交互课件.html》未被修改。
- 相位读数按 `2π` 取模显示，角度同时以弧度和角度给出。
- 演示中的 `A` 以 cm 为单位，角度以度或弧度显示，时间为 s。
