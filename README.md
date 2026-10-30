# 🏛️ 重生·圆明园 — 艺术设计展示页

> 2026 第19届全国3D大赛 主题作品 · 艺术设计展示仓库
> 参赛主仓库：**yuanmingyuan-3d**（完整工程与参赛材料，见文末说明）

利用 Three.js 程序化建模重建圆明园重点景区，可在浏览器中沉浸式漫游；同时提供 Blender 流水线导出的 GLB 实景模型查看入口。

## 在线演示（无需安装任何依赖）

直接**双击打开 `output/index.html`** 即可在浏览器中浏览程序化场景。

推荐用本地静态服务打开（GLB 实景模型加载更稳定）：

```bash
cd output
python3 -m http.server 8080
# 浏览器打开 http://localhost:8080/
```

> 说明：`file://` 协议下部分浏览器（如 Chrome）会出于安全策略拦截 GLB 模型加载，
> 此时页面会给出"加载失败"降级提示并保留程序化场景；程序化场景本身不受影响。
> 通过 HTTP 服务（本地或 GitHub Pages）访问时全部功能可用。

### 操作方式

- 鼠标：左键旋转 · 滚轮缩放 · 右键平移
- 移动端：单指旋转，页面已做小屏适配（390×844 及以下验证通过）

## 重点景区

页面右侧按钮可切换五个视角，镜头自动飞行并弹出景区详情卡：

| 景区 | 年代 | 简介 |
|------|------|------|
| 🏞️ 全景漫游 | 1707-1860 | 圆明园由圆明园、长春园、绮春园三园组成，占地5200余亩，是清代大型皇家园林，被誉为"万园之园"。 |
| 🏝️ 九州清晏 | 1723·雍正元年 | 后湖中心九座岛屿象征华夏九州，主殿为皇帝寝宫，黄琉璃瓦歇山顶。 |
| 🏛️ 大水法 | 1747·乾隆十二年 | 巴洛克风格喷泉，铜鹿鹿角喷水八道，十只铜犬直射鹿身，"猎狗逐鹿"奇景。 |
| 🏯 方壶胜境 | 1750·乾隆十五年 | 仿神仙仙境，建筑矗立水面，九座仙桥相连，宛如蓬莱。 |
| 👑 正大光明 | 1723·雍正元年 | 圆明园正殿，雍正御笔匾额，重檐歇山顶，华表石狮。 |

## 实景 GLB 模型

- 文件：`output/yuanmingyuan.glb`（glTF 2.0，Khronos glTF Blender I/O 导出，145 个网格构件）
- 入口：页面右侧「🎬 实景模型」按钮，点击后加载并展示（带加载进度百分比），可与程序化场景一键互切
- 加载失败时自动降级：弹出错误提示并保留程序化场景，不影响其余功能
- 技术说明：展示页为单文件 `output/index.html`，基于本地 three.js r128（`three.min.js`）与配套本地 `GLTFLoader.js`，无构建步骤、无外部 CDN 依赖

## pipeline-experimental/（实验性流水线，未完成）

原 `src/` 目录更名而来，是规划中的完整 AI 重建流水线骨架，**当前不可运行**，仅供后续开发参考：

```
pipeline-experimental/
├── ai_rebuild/        # Meshy API 调用与模型下载脚本（半成品）
├── blender_scripts/   # Blender 建模 / 场景组装 / 导出 GLB 脚本
├── backend/           # FastAPI 服务骨架
└── frontend/          # React + Vite 骨架（缺 index.html / main.jsx，无法启动）
```

依赖 Blender、Meshy API Key 等外部环境（见 `requirements.txt`、`.env.example`、`scripts/setup.sh`），均未调通。

## 项目结构

```
art-design/
├── output/                  # 可演示成品（本仓库核心）
│   ├── index.html           # 单文件 3D 展示页（Three.js r128 程序化建模）
│   ├── GLTFLoader.js        # r128 配套本地 GLTF 加载器
│   ├── three.min.js         # three.js r128（本地）
│   └── yuanmingyuan.glb     # Blender 流水线导出的实景模型
├── pipeline-experimental/   # 实验性 AI 重建流水线（未完成）
├── scripts/setup.sh         # 流水线环境初始化脚本（实验性）
└── README.md
```

## 与参赛主仓库 yuanmingyuan-3d 的关系

- **本仓库（art-design）**：面向展示的轻量 Web 演示页与艺术设计成果，双击即可浏览
- **yuanmingyuan-3d**：参赛主仓库，承载完整工程实现、文档与参赛提交材料
- 两仓库共享「重生·圆明园」主题；本仓库的 GLB 资产来自主仓库方向的建模流水线产出

## 许可

MIT License
