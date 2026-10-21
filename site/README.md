# 六个世界 · Voxel Worlds

六个可交互的体素场景，全部由 **DeepSeek V4.1 flash（1017 版）** 在 **PTC 模式**下，从一个中文提示词直接写成单文件 HTML。

- 在线游玩：**https://ccbitcode.github.io/voxel-worlds/** （若 GitHub Pages 尚未开启，用下面的镜像）
- 国内镜像：**https://raw.githack.com/CCbitcode/voxel-worlds/main/index.html**
- 制作档案（提示词 / 流程 / 用时 / 花费）：[archive.html](archive.html)

## 六个场景

| # | 场景 | 交互 | 文件 |
| --- | --- | --- | --- |
| 01 | 云鲸星轮 The Cloud Whale & the Astral Wheel | 拖拽 / 滚轮 / WASD / 昼夜 / 5 视点 | `scenes/cloud-whale.html` |
| 02 | 冰湖留声机 The Frozen Gramophone | 拖拽 / 缩放 / 极昼极夜 / 视点 / 声景 | `scenes/ice-lake.html` |
| 03 | 沉钟水母城 The Sunken Bell | 拖拽 / 游动 / 正午午夜 / 自动巡游 | `scenes/jellyfish.html` |
| 04 | 倒木观星台 The Fallen World Tree | 拖拽 / WASD / 昼夜 / 星图校准 | `scenes/observatory.html` |
| 05 | 沙海晷城 The Sundial City | 拖拽 / 漫游 / 时间滑块 / 昼夜流转 | `scenes/sundial.html` |
| 06 | 星舰龙骨村 The Kestrel Wreck | 拖拽 / 缩放 / WASD / 昼夜 / 5 视点 | `scenes/kestrel.html` |

## 本地运行

ES Module 不能直接双击 `file://` 打开，需要一个静态服务器：

```bash
# 任选其一
python -m http.server 8088
# 或
npx serve -l 8088
```

然后打开 http://127.0.0.1:8088/ 。

## 部署

- **GitHub Pages**：仓库 Settings → Pages → Build and deployment → Source 选 `Deploy from a branch`，Branch 选 `main` / `(root)` → Save。约 1 分钟后可访问 `https://<用户名>.github.io/voxel-worlds/`。
- **任意静态托管**：把仓库根目录整个上传到 Netlify / Cloudflare Pages / Vercel 即可，不需要构建命令，输出目录填 `/`。
- **raw.githack 镜像**：无需 Pages，直接访问 `https://raw.githack.com/CCbitcode/voxel-worlds/main/index.html`。

## 技术说明

- 每个场景都是**单文件 HTML**，贴图 0 张，全部程序化生成。
- 依赖已本地化在 `vendor/`（Three.js r160 / r170 + OrbitControls + 后处理），**不依赖 jsDelivr 等外网 CDN**，断网也能跑；只有 `scenes/observatory.html` 与 `scenes/sundial.html` 是 r180 全内联版本。
- 展厅用 iframe 全屏加载场景，带返回按钮和逐场景深链：`index.html#cloud-whale`、`#ice-lake` 等。
- 手机端建议横屏；场景支持单指旋转、双指缩放。

## 制作

- 模型：`deepseek-flash`（界面名 DeepSeek-V4.1-Flash），`reasoningEffort: max`
- 模式：PTC（Programmatic Tool Calling）
- 六场独立会话，合计约 4 小时 51 分；六个成品场景 + 一次 QA 费用约 ¥19.09
- 提示词、流程与星舰龙骨村的两轮人工反馈见 [archive.html](archive.html)

## 目录

```
index.html            展厅
archive.html          制作档案
scenes/               六个独立场景
assets/thumbs/        展厅缩略图
vendor/three160/      Three.js r160（本地）
vendor/three170/      Three.js r170（本地）
404.html
.nojekyll
```

---

场景代码与画面由 DeepSeek V4.1 flash 1017 生成；展厅、文案与制作档案整理 by 汐汐。仅供展示，转载或商用请先联系。
