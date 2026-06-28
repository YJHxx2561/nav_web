# SunPanel 导航页

一个基于 SunPanel 设计的网站导航页，简洁美观，支持多平台部署。

## 功能特性

- **随机背景图片** - 每次打开页面自动获取精美的随机壁纸
- **响应式设计** - 支持桌面端和移动端访问
- **多搜索引擎** - 支持 Bing、Google、Baidu 搜索
- **实时时间显示** - 显示当前时间和农历日期
- **玻璃拟态风格** - 现代美观的 UI 设计
- **分类导航** - 常用网站、工具、服务等多个分类

## 快速开始

直接在浏览器中打开 `index.html` 即可使用。

## 一键部署

点击下方按钮即可快速部署到相应平台：

| 平台 | 一键部署 |
|:---:|:---:|
| Cloudflare Pages | [![Deploy to Cloudflare Pages](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/YOUR_USERNAME/YOUR_REPO) |
| GitHub Pages | [![Deploy to GitHub Pages](https://img.shields.io/badge/Deploy_to-GitHub_Pages-2088FF?style=for-the-badge&logo=github)](https://github.com/YOUR_USERNAME/YOUR_REPO/fork) |
| EdgeOne Pages | [![Deploy to EdgeOne Pages](https://img.shields.io/badge/Deploy_to-EdgeOne_Pages-00C389?style=for-the-badge&logo=cloudflare)](https://edgeone.ai/pages/new) |
| ESA Pages | [![Deploy to ESA Pages](https://img.shields.io/badge/Deploy_to-ESA_Pages-FF6A00?style=for-the-badge&logo=huawei)](https://console.huaweicloud.com/esa) |

> **注意**: 请将上方链接中的 `YOUR_USERNAME/YOUR_REPO` 替换为你的 GitHub 用户名和仓库名。

---

## 部署指南

### 部署到 Cloudflare Pages

#### 方法一：连接 GitHub 仓库
1. 将项目推送到 GitHub 仓库
2. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)
3. 进入 **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**
4. 选择你的 GitHub 仓库
5. 配置构建设置：
   - **构建命令**: 留空
   - **构建输出目录**: `/`
6. 点击 **Save and Deploy**

#### 方法二：直接上传
1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. 进入 **Workers & Pages** → **Create application** → **Pages** → **Upload assets**
3. 上传 `index.html` 和 `404.html` 文件
4. 点击 **Deploy site**

---

### 部署到 GitHub Pages

#### 方法一：从分支部署
1. Fork 或将项目推送到你的 GitHub 仓库
2. 进入仓库的 **Settings** → **Pages**
3. 在 **Source** 下选择 `Deploy from a branch`
4. 选择分支（如 `main`）和目录（`/root`）
5. 点击 **Save**，等待几分钟后即可访问

#### 方法二：使用 GitHub Actions 自动部署
1. 在仓库中创建 `.github/workflows/deploy.yml` 文件：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ "main" ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v4
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

2. 提交并推送到 GitHub，Actions 会自动部署
3. 在 **Settings** → **Pages** 中查看部署地址

---

### 部署到 EdgeOne Pages

1. 访问 [EdgeOne Pages](https://edgeone.ai/pages)
2. 点击 **Create Project** 或 **Import from Git**
3. 连接你的 GitHub 仓库
4. 配置构建设置：
   - **构建命令**: 留空
   - **输出目录**: `/`
5. 点击 **Deploy** 完成部署

---

### 部署到 ESA Pages（华为云边缘安全加速）

1. 登录 [华为云 ESA 控制台](https://console.huaweicloud.com/esa)
2. 创建站点，选择 **静态站点** 类型
3. 连接 Git 仓库或直接上传文件
4. 配置构建设置：
   - **构建命令**: 无需配置
   - **输出目录**: `/`
5. 完成创建后，ESA 会自动分配域名

---

## 其他部署平台

<details>
<summary>展开查看更多部署选项</summary>

### Vercel
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/YOUR_USERNAME/YOUR_REPO)

1. 点击上方按钮或访问 [Vercel](https://vercel.com)
2. 导入 GitHub 仓库
3. 框架预设选择 **Other**
4. 点击 **Deploy**

### Netlify
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start)

1. 点击上方按钮或访问 [Netlify](https://app.netlify.com)
2. 选择 **Add new site** → **Import an existing project**
3. 连接 GitHub 仓库
4. 构建命令留空，发布目录为 `/`
5. 点击 **Deploy site**

### Render
1. 访问 [Render](https://render.com)
2. 创建新的 **Static Site**
3. 连接 GitHub 仓库
4. 构建命令留空，发布目录为 `/`
5. 点击 **Create Static Site**

</details>

## 项目结构

```
├── index.html          # 主页面
├── 404.html            # 404错误页面
└── README.md           # 项目说明
```

## 技术栈

- HTML5 + Tailwind CSS 3
- Lucide Icons 图标库
- JavaScript 动态背景加载
- 玻璃拟态设计（Glassmorphism）
