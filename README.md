# Markdown 文档库 - 文档网站 v1.0

一个简洁优雅的纯前端 Markdown 文档展示平台，支持明暗主题、分类浏览、实时搜索与代码高亮。

---

## 功能特性

| 功能 | 说明 |
|------|------|
| 毛玻璃 UI | 现代化毛玻璃（Glassmorphism）设计风格 |
| 明暗主题 | 一键切换浅色/深色模式，自动记忆用户偏好 |
| 分类浏览 | 支持多分类文档管理（学术、游戏、项目、工作室等） |
| 实时搜索 | 文档名称/分类实时模糊搜索，支持 Ctrl+F 快捷键 |
| 轮播展示 | 首页精美轮播图，支持自动播放与手动切换 |
| Markdown 渲染 | 基于 marked.js 的完整 Markdown 渲染支持 |
| 代码高亮 | 集成 highlight.js，支持多种编程语言高亮 |
| 响应式布局 | 完美适配桌面端、平板与移动端 |
| 纯前端部署 | 无需后端，可部署于 GitHub Pages / 任意静态服务器 |

---

## 界面预览

```
+-----------------------------------------------------+
|  文档库    首页 关于   搜索  [] 主题切换            |
+---------+-----------------------+-------------------+
|  分类    |  文档标题.md         |  概览             |
|  - 全部  |  另一篇文档.md       |  - 12 篇          |
|  - 学术  |  README.md           |  - 5 个分类       |
|  - 游戏  +-----------------------+  分布             |
|  - 项目  |  Markdown 预览区域  |  [====]           |
|  - 其他  |                       |  最近             |
+---------+-----------------------+-------------------+
```

---

## 快速开始

### 方式一：本地预览（推荐）

```bash
# 1. 进入项目目录
cd "文档网站v1.0"

# 2. 启动本地 HTTP 服务器（Python 3 自带）
python -m http.server 8080

# 3. 浏览器访问
# http://localhost:8080
```

注意：必须通过 HTTP 服务器访问，直接双击 index.html 会因浏览器安全策略导致 files.json 加载失败。

### 方式二：直接打开（仅限已部署）

若已部署至 GitHub Pages 或任意 Web 服务器，直接访问对应 URL 即可。

---

## 项目结构

```
文档网站v1.0/
+-- index.html          # 主页面（核心文件）
+-- files.json         # 文档索引配置文件
+-- generate.ps1       # 自动生成 files.json 的 PowerShell 脚本
+-- md/                # Markdown 文档存放目录
|   +-- Academic/              # 学术文档
|   +-- Game_Information/      # 游戏资讯
|   +-- Github_Project/        # GitHub 项目文档
|   +-- Studio_Documents/      # 工作室文档
|   +-- Other/                 # 其他
+-- img/                # 图片资源目录
|   +-- A_Img/               # 轮播图等展示图片
+-- 说明.txt            # 本地运行说明
```

---

## 添加文档

### 步骤一：放入 Markdown 文件

将你的 .md 文件放入对应的分类目录（如 md/Academic/我的论文.md）。

### 步骤二：更新文档索引

运行 generate.ps1 脚本自动生成 files.json：

```powershell
# 在项目目录打开 PowerShell 运行
./generate.ps1
```

或手动编辑 files.json：

```json
[
  {
    "name": "我的论文.md",
    "path": "Academic/我的论文.md",
    "category": "Academic",
    "size": 1234
  }
]
```

---

## 自定义配置

### 修改站点名称

在 index.html 中找到以下位置并修改：

```html
<!-- 约第 956 行 -->
<span class="logo-text">文档库</span>
```

### 修改主题色

在 index.html 的 <style> 中修改 CSS 变量：

```css
:root {
    --accent: #4a6cf7;        /* 主题色 */
    --accent-light: #eef1ff;    /* 主题浅色 */
}
```

### 修改轮播内容

在 index.html 中找到 initCarousel 函数（约第 1631 行），修改 slides 数组：

```javascript
var slides = [
    {
        tag: '标签',
        title: '标题文字',
        sub: '副标题说明',
        img: 'img/你的图片.png',   // 使用图片背景
        // bg: 'linear-gradient(...)'  // 或使用渐变背景
    },
    // 可添加更多轮播项...
];
```

---

## 部署到 GitHub Pages

1. 将项目推送至 GitHub 仓库
2. 进入仓库 Settings -> Pages
3. 选择分支（通常为 main）和 / (root) 目录
4. 点击 Save，等待部署完成
5. 访问 https://你的用户名.github.io/仓库名/

注意：若仓库名不是 用户名.github.io，需在 index.html 中的资源路径前加上 /仓库名/ 前缀。

---

## 技术栈

| 技术 | 用途 |
|------|------|
| marked.js | Markdown 解析与渲染 |
| highlight.js | 代码语法高亮 |
| iconfont SVG | 矢量图标（阿里巴巴矢量图标库） |
| CSS Variables | 主题切换与样式管理 |
| CSS Grid / Flexbox | 响应式布局 |
| Fetch API | 异步加载 files.json 与 .md 文件 |

---

## License

本项目采用 **GPLv3.0** 开源协议发布。

GPLv3.0 是一款强Copyleft协议，核心要求：
- 任何人可以免费使用、修改、分发本项目的代码
- **任何基于本项目修改或集成的衍生项目，必须以同样的 GPLv3.0 协议开源**
- 修改过的文件必须标明变更说明
- 必须保留原作者的版权声明

```
GNU GENERAL PUBLIC LICENSE
Version 3, 29 June 2007

Copyright (C) 2026 AEjunjun

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
```

完整协议文本请参阅项目根目录下的 `LICENSE` 文件。

---

## 作者

AEjunjun

- GitHub：https://github.com/AEjunjun
- 项目主页：https://github.com/AEjunjun/仓库名

---

## Star History

如果这个项目对你有帮助，欢迎点个 Star，你的支持是我维护的动力！

---

<div align="center">

用心整理，开源分享

实话说，我认为这是一个失败的垃圾作品，当做练手可能不错...

</div>
