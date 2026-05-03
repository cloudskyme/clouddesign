# Open Design 使用手册

## 目录
1. [简介](#简介)
2. [系统要求](#系统要求)
3. [安装与启动](#安装与启动)
4. [界面概览](#界面概览)
5. [核心功能](#核心功能)
6. [技能使用指南](#技能使用指南)
7. [设计体系](#设计体系)
8. [媒体生成](#媒体生成)
9. [高级功能](#高级功能)
10. [故障排除](#故障排除)

---

## <a id="简介"></a>1. 简介

Open Design 是 Claude Design 的开源替代品，采用本地优先架构，支持部署到 Vercel。它通过 10 种 coding-agent CLI（Claude Code、Codex、Cursor Agent、Gemini CLI、OpenCode、Qwen、GitHub Copilot CLI、Hermes、Kimi、Pi）作为设计引擎，由 31 个可组合技能（Skills）和 72 套品牌级设计体系（Design Systems）驱动。

**核心特点：**
- ✅ 本地运行，数据完全私有
- ✅ 支持 Vercel 部署
- ✅ BYOK（自带 Key）架构，支持任意 OpenAI 兼容 API
- ✅ 31 个内置技能，覆盖原型、幻灯片、移动端、仪表盘等场景
- ✅ 72 套设计体系，包括 Linear、Stripe、Vercel、Airbnb、Tesla 等
- ✅ 中文界面支持
- ✅ 完整的媒体生成能力（图像、视频、音频）

---

## <a id="系统要求"></a>2. 系统要求

### 硬件要求
- CPU：Intel Core i5 或 AMD Ryzen 5 及以上
- 内存：8GB RAM（推荐 16GB）
- 存储：至少 2GB 可用空间

### 软件要求
- Node.js：版本 ~24（推荐 v24.12.2）
- pnpm：版本 10.33.2
- Git：最新版本
- 浏览器：Chrome、Edge 或 Firefox（最新版）

> 💡 提示：如未安装 Node.js 和 pnpm，建议先安装 [Node Version Manager (nvm)](https://github.com/coreybutler/nvm-windows) 或 [fnm](https://github.com/Schniz/fnm)，然后执行 `nvm install 24 && nvm use 24` 和 `corepack enable`

---

## <a id="安装与启动"></a>3. 安装与启动

### 3.1 克隆仓库
```bash
# 克隆项目
git clone https://github.com/cloudskyme/clouddesign.git
cd clouddesign
```

### 3.2 安装依赖
```bash
# 启用 corepack
corepack enable

# 检查 pnpm 版本（应为 10.33.2）
corepack pnpm --version

# 安装所有依赖
pnpm install
```

### 3.3 启动应用
```bash
# 启动开发服务器
pnpm tools-dev run web
```

启动成功后，您会看到类似以下的输出：
```
  Open Design dev server ready

  ➜  Web:    http://127.0.0.1:3000/
  ➜  Daemon: http://127.0.0.1:29993/
  Press Ctrl+C to stop
```

### 3.4 访问应用
在浏览器中打开 `http://127.0.0.1:3000` 即可使用 Open Design。

> 📝 注意：首次启动时，系统会自动检测您 PATH 中已安装的 coding-agent CLI，并加载所有技能和设计体系。

---

## <a id="界面概览"></a>4. 界面概览

Open Design 采用现代化的三栏布局：

### 左侧导航栏
- **我的设计**：查看和管理您的项目
- **示例**：浏览预置的设计示例
- **设计体系**：选择和预览 72 套设计体系
- **图片模板**：浏览图像生成模板
- **视频模板**：浏览视频生成模板

### 中间主工作区
- **新建项目**：创建新设计项目
- **项目列表**：显示所有项目，支持搜索和筛选
- **文件工作区**：上传、管理设计文件
- **对话区域**：与 AI 进行交互

### 右侧设置面板
- **设置**：配置执行模式、模型、API Key 等
- **账户**：管理代理和模型设置
- **语言**：切换界面语言（当前为中文）

---

## <a id="核心功能"></a>5. 核心功能

### 5.1 设计工作流

Open Design 的设计工作流遵循严格的五步流程：

1. **需求输入**：在对话框中描述您的设计需求
2. **初始化表单**：填写 Surface（表面）、受众、调性、品牌上下文、规模等关键信息
3. **方向选择**：从 5 套精选视觉方向中选择（编辑风、现代简约、科技实用、粗野主义、温暖柔和）
4. **实时进度**：查看 AI 的实时任务卡片和工具调用
5. **沙盒预览**：在安全的 iframe 中预览生成的设计成果

### 5.2 文件管理

- **上传文件**：拖拽或点击上传设计文件（HTML、CSS、JS、图片等）
- **设计文件**：管理项目中的所有文件
- **保存模板**：将优秀的设计保存为模板供后续使用
- **导出格式**：支持 HTML、PDF、PPTX、ZIP、Markdown 等多种格式

### 5.3 设置管理

- **执行模式**：
  - **本机 CLI**：使用本地安装的 coding-agent CLI
  - **Anthropic API**：使用 Anthropic API（需提供 API Key）
- **代码代理**：自动检测并选择可用的 CLI
- **模型选择**：选择不同模型进行设计生成
- **界面语言**：切换中文/英文等语言
- **外观主题**：浅色、深色或跟随系统设置

---

## <a id="技能使用指南"></a>6. 技能使用指南

Open Design 内置 31 个技能，分为两大类：

### 6.1 原型类技能（27 个）

| 技能 | 适用场景 | 主要产出 |
|------|----------|----------|
| `web-prototype` | 网页原型 | 单页 HTML landing page |
| `saas-landing` | SaaS 营销 | Hero/Features/Pricing/CTA 版式 |
| `dashboard` | 数据仪表盘 | 带侧栏的数据密集型后台 |
| `mobile-app` | 移动端应用 | iPhone/Pixel 外壳的移动应用 |
| `email-marketing` | 邮件营销 | 品牌新品发布邮件 |
| `social-carousel` | 社交媒体 | 1080×1080 三连社媒轮播图 |
| `magazine-poster` | 杂志海报 | 单页杂志风海报 |
| `motion-frames` | 动态图形 | CSS 循环动画 hero |
| `sprite-animation` | 像素动画 | 像素/8-bit 动画解释器 |
| `dating-web` | 约会平台 | 消费级约会/婚恋仪表盘 |
| `digital-eguide` | 数字指南 | 两页数字 e-guide |
| `wireframe-sketch` | 线框图 | 手绘风线框稿 |
| `critique` | 设计评审 | 五维自评分卡 |
| `tweaks` | 参数调整 | AI 自吐 tweaks 面板 |

### 6.2 幻灯片类技能（4 个）

| 技能 | 特点 | 适用场景 |
|------|------|----------|
| `guizang-ppt` | 杂志风网页 PPT | 种子轮路演、产品演示 |
| `simple-deck` | 极简横滑 deck | 快速演示 |
| `replit-deck` | Replit 风格 | 产品演示 |
| `weekly-update` | 团队周报 | 进度/阻塞/下一步 |

### 6.3 使用步骤

1. 在左侧导航栏选择 **「我的设计」**
2. 点击 **「新建项目」** 按钮
3. 选择合适的技能类型（原型、幻灯片、从模板等）
4. 输入项目名称和设计需求
5. 填写初始化表单（Surface、受众、调性等）
6. 点击 **「创建」** 开始生成
7. 查看实时任务进度和沙盒预览

---

## <a id="设计体系"></a>7. 设计体系

Open Design 预置了 72 套设计体系，每套都包含完整的 `DESIGN.md` 文件，定义了：
- 颜色系统（Color）
- 字体排版（Typography）
- 间距系统（Spacing）
- 布局规范（Layout）
- 组件样式（Components）
- 动效规则（Motion）
- 品牌声音（Voice）
- 品牌规范（Brand）
- 反模式（Anti-patterns）

### 7.1 主要设计体系分类

- **AI & LLM**：Claude、Cohere、Mistral、Minimax、Together AI 等
- **开发者工具**：Cursor、Vercel、Linear、Stripe、Figma、Supabase 等
- **生产力**：Notion、Figma、Miro、Airtable、Intercom 等
- **金融科技**：Stripe、Coinbase、Binance、Mastercard 等
- **电商/出行**：Shopify、Airbnb、Uber、Nike 等
- **媒体**：Spotify、PlayStation、Wired、The Verge 等
- **汽车**：Tesla、BMW、Ferrari、Lamborghini 等
- **其他**：Apple、IBM、NVIDIA、SpaceX 等

### 7.2 使用方法

1. 在新建项目时，选择 **「设计体系」** 选项卡
2. 搜索或浏览您需要的设计体系
3. 点击预览查看色卡和完整规范
4. 选择后，AI 将严格按照该体系生成设计

---

## <a id="媒体生成"></a>8. 媒体生成

Open Design 支持三种媒体类型的生成：

### 8.1 图像生成

- **模型**：`gpt-image-2`（Azure / OpenAI）
- **用途**：海报、头像、城市插画地图、信息图、杂志风社媒卡等
- **模板**：43 条预置图像模板，支持一键复刻

### 8.2 视频生成

- **模型**：
  - `seedance-2.0`（字节跳动）：15 秒电影感 t2v + i2v
  - `hyperframes-html`（HeyGen 开源）：HTML→MP4 动态图形
- **用途**：叙事短片、人物特写、产品片、MV 编排、动态图表等
- **模板**：39 条 Seedance 模板 + 11 条 HyperFrames 模板

### 8.3 音频生成

- **模型**：Suno v5/v4.5、Udio v2、Lyria 2（音乐）、GPT-4o-mini-tts（语音）
- **用途**：背景音乐、配音、音效等

### 8.4 使用步骤

1. 在新建项目时选择 **「图片」** 或 **「视频」** 类型
2. 选择合适的模板
3. 编辑提示词
4. 点击生成
5. 下载生成的 `.png` 或 `.mp4` 文件

---

## <a id="高级功能"></a>9. 高级功能

### 9.1 Claude Design ZIP 导入

将 Claude Design 导出的 ZIP 文件直接拖拽到欢迎弹窗，系统会：
- 解压成真实项目目录
- 自动打开入口文件
- 预置提示词「接着 Anthropic 停下的地方继续编辑」

### 9.2 BYOK 代理

支持任意 OpenAI 兼容的 API：
- 填写 `baseUrl`、`apiKey`、`model`
- 支持 Anthropic-via-OpenAI、DeepSeek、Groq、MiMo、OpenRouter、自托管 vLLM 等
- 内置 SSRF 防御机制

### 9.3 用户自存模板

- 喜欢某次渲染？点击 **「保存为模板」**
- 模板会保存到 SQLite 数据库
- 下次新建项目时可在「您的模板」中选择

### 9.4 Tab 持久化

- 每个项目会记住您打开的文件和当前 tab
- 关闭后重新打开，工作区保持原样

### 9.5 Artifact lint API

- 对生成的设计进行结构性检查
- 返回详细的问题报告
- AI 可以根据报告进行修正

---

## <a id="故障排除"></a>10. 故障排除

### 10.1 常见问题

#### Q：启动时出现 "Cannot find module" 错误
A：请确保已运行 `pnpm install` 安装所有依赖，然后重试 `pnpm tools-dev run web`

#### Q：界面没有显示中文
A：请检查 `apps/web/app/layout.tsx` 文件中的 `<html lang='zh-CN'>` 是否正确设置，或者清除浏览器缓存

#### Q：无法检测到 coding-agent CLI
A：请确认相关 CLI 已正确安装并添加到系统 PATH 环境变量中，然后点击「重新扫描」

#### Q：生成的 HTML 预览不显示
A：请检查网络连接，或尝试刷新页面；如果问题持续，请检查 `apps/web/src/artifacts/parser.ts` 中的解析器配置

### 10.2 调试命令

| 命令 | 用途 |
|------|------|
| `pnpm tools-dev status` | 查看当前服务状态 |
| `pnpm tools-dev logs` | 查看服务日志 |
| `pnpm tools-dev check` | 快速诊断状态和日志 |
| `pnpm tools-dev stop` | 停止所有服务 |
| `pnpm tools-dev start web` | 仅启动 Web 服务 |

### 10.3 重置环境

如果遇到严重问题，可以完全重置：
```bash
# 停止服务
pnpm tools-dev stop

# 删除运行时数据
rm -rf .od

# 重新安装依赖
pnpm install

# 重新启动
pnpm tools-dev run web
```

---

## 获取帮助

- **文档**：[docs/](docs/) 目录包含详细的技术文档
- **贡献指南**：[CONTRIBUTING.zh-CN.md](CONTRIBUTING.zh-CN.md)
- **问题反馈**：在 GitHub 上提交 [Issue](https://github.com/cloudskyme/clouddesign/issues)
- **社区支持**：加入我们的 Discord 或 Telegram 社区

> 🌟 如果这个使用手册对您有帮助，请给项目点个 Star！
> [https://github.com/cloudskyme/clouddesign](https://github.com/cloudskyme/clouddesign)

© 2026 Open Design Team | Apache-2.0 License