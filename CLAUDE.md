# 数学建模知识分享网站

## 👤 项目背景
- **站长**：KawaiiWarma，一名大二学生
- **参赛经历**：1 次美赛（MCM/ICM）+ 2 次统计建模大赛
- **动机**：把自己学习数学建模的经验整理成网站，分享给身边的老师和同学
- **内容来源**：站长在 Obsidian 中整理的数学建模模型知识库笔记

## 🌐 网站信息
- **网址**：https://kawaiiwarma520.github.io/math-modeling/
- **GitHub 仓库**：https://github.com/KawaiiWarma520/math-modeling
- **技术栈**：Jekyll + GitHub Pages（纯静态网站）
- **域名类型**：项目站点（Project Site），baseurl 为 `/math-modeling`

## 📁 项目文件结构
```
/
├── _config.yml                 # Jekyll 配置文件
├── CLAUDE.md                   # 本项目规范（就是你正在读的）
├── index.html                  # 首页（Hero + 六栏目卡片 + 最新文章）
├── search.json                 # 搜索索引（Jekyll 自动生成）
├── .gitignore
├── _layouts/
│   ├── default.html            # 基础布局（含 KaTeX + 导航切换脚本）
│   ├── page.html               # 栏目页布局（继承 default）
│   └── post.html               # 文章页布局（继承 default，含标签显示）
├── _includes/
│   ├── header.html             # 导航栏（七项：首页+六栏目+标签+搜索）
│   ├── footer.html             # 页脚
│   └── category-emoji.html     # 栏目 → emoji 映射
├── _posts/                     # 📌 所有文章放这里（.md 格式）
│   ├── 2026-05-31-linear-programming.md
│   ├── 2026-05-31-integer-programming.md
│   ├── 2026-05-31-multi-objective-programming.md
│   └── 2026-05-31-ahp.md
├── assets/css/style.css        # 全部样式（蓝紫配色 #2563eb → #7c3aed）
├── beginner-guide/index.html   # 🌟 新手教程 栏目页
├── model-learning/index.html   # 📚 模型百科 栏目页
├── paper-writing/index.html    # ✍️ 论文写作 栏目页（暂无内容）
├── tool-learning/index.html    # 🛠 工具学习 栏目页（暂无内容）
├── past-exams/index.html       # 📝 真题演练 栏目页（暂无内容）
├── resource-sharing/index.html # 📁 资料分享 栏目页（暂无内容）
├── tag/index.html              # 🏷 标签聚合页
└── search/index.html           # 🔍 搜索页（JavaScript 实时搜索）
```

## 📐 栏目结构（共 6 个，按学习路径排序）
1. 🌟 **新手教程** — 零基础入门
2. 📚 **模型百科** — 六大类模型（优化/评价/预测/分类/统计/其他）
3. ✍️ **论文写作** — 论文框架、摘要写法、图表排版
4. 🛠 **工具学习** — LaTeX、Python、VS Code、Zotero、draw.io
5. 📝 **真题演练** — 历年真题 + 解题思路
6. 📁 **资料分享** — 模板、代码库、配置文件、数据集

## 🎨 设计风格
- **配色**：蓝紫渐变（主色 #2563eb → 紫色 #7c3aed）
- **背景**：#f5f7fb 浅灰
- **卡片**：白色，圆角 20px，柔和阴影
- **导航**：白色背景，蓝紫渐变 logo 文字
- **首页网格**：3 列 × 2 行（桌面端），2 列（平板），1 列（手机）

## ⚙️ 已实现的功能
- ✅ 六栏目导航 + 首页卡片
- ✅ KaTeX 数学公式渲染（`$...$` 行内，`$$...$$` 独立行）
- ✅ 文章标签系统 + 标签聚合页（`/tag/`）
- ✅ 全站实时搜索（`/search/`，搜索标题/标签/内容）
- ✅ 每篇文章有自定义 description 摘要
- ✅ 标签点击跳转（`scroll-margin-top` 防遮挡）
- ✅ 响应式设计（桌面/平板/手机）

## 📝 新文章发布流程

### 标准流程（推荐）
1. 用户提供原始 .md 内容（从 Obsidian 等来源）
2. 按 Jekyll 格式整理，添加 Front Matter
3. **完整保留用户原始内容**（见下方规范）
4. 发回给用户审阅
5. 用户确认后，再执行 Git 操作

### 快速 Git 操作（用户确认后）
```bash
cd "D:/My Mathematical Modelling Website"
git add _posts/文件名.md
git commit -m "新文章：xxx"
git push
```
等待约 1-2 分钟，GitHub Pages 构建完成即可看到更新。

## 🔧 技术要点
- **baseurl**：`/math-modeling`（所有链接使用 `relative_url` 过滤器）
- **LaTeX**：通过 KaTeX CDN 渲染，在 `_layouts/default.html` 中配置
- **搜索索引**：`search.json` 由 Jekyll 构建时自动生成
- **标签显示**：纯文字，不带 emoji 前缀
- **日期**：使用实际日期，格式 `YYYY-MM-DD HH:MM:SS +0800`

## ⚠️ 内容处理规范（重要！）

### 用户原创内容
- **完整保留用户原始内容**，不做删减
- 用户的原始文件（Obsidian 笔记等）是最终依据
- **不允许移除**以下完整章节：学术写作（论文写法）、应用场景、注意事项、代码实现、关联模型
- **不允许**替换示例数据或改变代码语言（如 Python ↔ MATLAB）
- 允许移除英文副标题如 `(Core Concept)`，其余内容不变

### 文章格式
```yaml
---
layout: post
title: "标题"
date: 2026-05-31 HH:MM:SS +0800
categories: 栏目名    # 从六栏目中选一个
tags: [标签1, 标签2]  # 相关标签
description: "一段有吸引力的摘要"  # 必填，用于卡片预览
---
```

### 工作流程
1. 用户提供原始内容
2. 按格式整理，完整保留内容
3. 发回给用户审阅
4. 用户确认后再推送上线
5. **推送前检查清单**：
   - [ ] 内容完整性（对比原始文件）
   - [ ] 日期是否正确
   - [ ] LaTeX 语法是否正确
   - [ ] 标签是否合理
   - [ ] description 是否有意义

## 🚫 历史教训（避免再犯）
- 不要过度改写用户内容，以原始文件为准
- 不要删减学术写作模板、应用场景表格等重要章节
- 添加新功能时检查是否影响已有功能
- 日期始终使用实际日期
- 搜索功能必须有完整的错误处理
