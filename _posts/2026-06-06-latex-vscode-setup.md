---
layout: post
title: "小西教你在 VSCode 中配置 LaTeX！"
date: 2026-06-06 12:00:00 +0800
categories: 工具学习
tags: [工具, LaTeX, VS Code, 配置, 编辑器]
description: "手把手教你用 VS Code + LaTeX Workshop + SumatraPDF 搭建 LaTeX 写作环境。从下载安装到 setting.json 配置，从中文编译到参考文献管理，附完整配置代码和双向跳转设置，帮你打造高效 LaTeX 写作工作流。"
---

> 🎯 **适合人群**：已经装了 TeX Live、想用 VS Code 写 LaTeX 的同学

---

## Q1：什么是 VS Code？为什么要用 VS Code 写 LaTeX？

**VS Code**（全称：Visual Studio Code）是微软开发的一款免费、开源、跨平台的代码编辑器。你可以把它理解为一个可以编辑并运行代码的"超级记事本"——在这里可以编辑 LaTeX、Python、HTML 等上百种语言。

VS Code 的生态非常丰富，支持插件安装，从而实现功能扩展、界面自定义、Agent 接入等非常多的功能。

**我的配置方案：** VS Code + LaTeX Workshop 插件 + SumatraPDF

这套方案相比原生的 TeXstudio，支持：
- ✅ 外观自定义（主题、图标随意换）
- ✅ 代码补全
- ✅ 代码与 PDF 双向跳转
- ✅ AI 辅助写作（Copilot、Claude Code 等）

**缺点：** 有一定使用门槛，需要自行配置文件（不过我已经整理好了，可以直接套用，见下文）。

### VS Code vs TeXstudio 对比

| 维度 | TeXstudio | VS Code + LaTeX Workshop |
|:---|:---|:---|
| 开箱即用 | ✅ 安装即用 | ❌ 需要配置 |
| 原生 LaTeX 功能 | ✅ 非常丰富 | ⭐ 依赖插件 |
| 自定义程度 | ⭐⭐⭐ | ✅ 极高 |
| 插件生态 | ⭐⭐ | ✅ 极其丰富 |
| AI 辅助 | ❌ 基本没有 | ✅ Copilot / Claude Code |
| 学习门槛 | 低 | 中高 |
| 适用人群 | 不想折腾的同学 | 愿意折腾、追求高质量环境的同学 |

**一句话选择：**
- 想省事 → **TeXstudio**
- 想折腾 → **VS Code** 🚀

---

## Q2：如何把 LaTeX 接入 VS Code？

下面是我的配置步骤，跟着走就行。

### 第一步：下载 SumatraPDF

👉 [Sumatra PDF 下载页](https://www.sumatrapdfreader.org/download-free-pdf-viewer)

选择 **64-bit builds → Installer** 下载安装即可。SumatraPDF 是一个非常轻量的 PDF 阅读器（仅约 5MB），是 VS Code 写 LaTeX 时的"最佳搭档"——它负责把编辑器和 PDF 连起来，让你点击代码就能跳到 PDF，双击 PDF 就能跳回代码。

> ⚠️ 一定要记住这里的安装位置，后面配置 json 文件会用到哦！

### 第二步：下载 VS Code

👉 [VS Code 下载页](https://code.visualstudio.com/Download)

根据你的电脑系统选择对应的安装程序。运行安装程序时无特殊要求，建议安装到 D 盘并勾选"创建快捷方式"。

### 第三步：安装中文语言包

打开 VS Code 后，界面默认是英文。点击左侧工具栏的"方块"图标（扩展商店），在搜索栏输入 `chinese`，找到 **Chinese (Simplified) (简体中文) Language Pack for Visual Studio Code** 并安装。安装完毕后右下角会弹出切换语言的提示，点击后重启 VS Code，就可以看到汉化后的界面了。

### 第四步：安装 LaTeX Workshop 插件

同样在扩展商店搜索栏输入 `LaTeX`，找到 **LaTeX Workshop** 并安装。

### 第五步：禁用内置 PDF 查看器

在扩展商店找到 `vscode-pdf` 插件（默认已安装），点击齿轮图标，选择**禁用**（避免和 SumatraPDF 冲突）。

此时重启 VS Code。在菜单栏点击**文件 → 打开文件夹**，选择你的 LaTeX 模板文件夹。接着点击左侧文件栏的 `.tex` 文件，再点击右上角的"放大镜"图标即可预览 PDF。点击 ▶ 编译，左下角显示构建进度——如果可以正常构建，说明基础配置成功了 ✅

> 💡 构建过一次 PDF 后，就可以支持双向跳转了：
> - **代码 → PDF**：选中代码，按 `Ctrl + Alt + J`
> - **PDF → 代码**：选中文本，按住 `Ctrl`，鼠标左键点击 PDF 中的内容

> ⚠️ 但此时功能还不完善，可能存在中文字体兼容性问题，且不支持 BibTeX 导入参考文献，需要在 `setting.json` 中额外配置。

### 第六步：配置 setting.json

点击 VS Code 最上方的搜索栏（或按 `Ctrl + Shift + P`），输入 `Preferences Open User Settings (JSON)`，点击该选项，跳转到配置文件编辑界面。

> ⚠️ 先把你当前的配置代码复制到记事本里保存一份！不同电脑的配置文件兼容性可能有差别——如果下方代码无法使用，可以粘贴回原来的代码，恢复之前的配置环境。

然后**全部替换**为以下代码：

```json
{
    // ========== LaTeX Workshop 核心配置 ==========
    // 定义编译工具
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": ["%DOCFILE%"]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-xelatex",
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        }
    ],

    // 定义编译方案（Recipe）
    "latex-workshop.latex.recipes": [
        {
            "name": "xelatex (中文推荐)",
            "tools": ["xelatex"]
        },
        {
            "name": "pdflatex (英文)",
            "tools": ["pdflatex"]
        },
        {
            "name": "xelatex → bibtex → xelatex×2 (中文+参考文献)",
            "tools": ["xelatex", "bibtex", "xelatex", "xelatex"]
        },
        {
            "name": "pdflatex → bibtex → pdflatex×2 (英文+参考文献)",
            "tools": ["pdflatex", "bibtex", "pdflatex", "pdflatex"]
        },
        {
            "name": "latexmk (自动: 中文+参考文献)",
            "tools": ["latexmk"]
        }
    ],

    // 默认编译方案（自动模式）
    "latex-workshop.latex.recipe.default": "latexmk (自动: 中文+参考文献)",

    // ========== PDF 查看器设置（SumatraPDF）==========
    // 使用外部 PDF 查看器
    "latex-workshop.view.pdf.viewer": "external",

    // SumatraPDF 路径（⚠️ 请修改为你的实际安装路径）
    "latex-workshop.view.pdf.external.viewer.command": "C:/Program Files/SumatraPDF/SumatraPDF.exe",
    "latex-workshop.view.pdf.external.synctex.command": "C:/Program Files/SumatraPDF/SumatraPDF.exe",

    // 正向同步：从 VS Code 跳转到 SumatraPDF
    "latex-workshop.view.pdf.external.synctex.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "%PDF%"
    ],

    // 保存时自动编译
    "latex-workshop.latex.autoBuild.run": "onSave",

    // 编译失败时自动清理辅助文件并重试
    "latex-workshop.latex.autoBuild.cleanAndRetry": true,

    // ========== 通用 VS Code 设置 ==========
    "editor.mouseWheelZoom": true,
    "explorer.confirmDelete": false,
    "files.autoSave": "afterDelay",
    "editor.unicodeHighlight.allowedLocales": {
        "ja": true,
        "zh-hans": true
    },
    "git.openRepositoryInParentFolders": "always",

    // PDF 文件默认用 SumatraPDF 打开（双击左侧文件树时）
    "workbench.editorAssociations": {
        "*.pdf": "latex-workshop"
    }
}
```

**记得修改 SumatraPDF 路径：**

找到代码中的这两行：

```json
"latex-workshop.view.pdf.external.viewer.command": "C:/Program Files/SumatraPDF/SumatraPDF.exe",
"latex-workshop.view.pdf.external.synctex.command": "C:/Program Files/SumatraPDF/SumatraPDF.exe",
```

把路径换成你电脑上 SumatraPDF 的实际安装路径。
> ⚠️ **注意斜杠方向**：这里一定要用 `/`，**不要**用 Windows 默认的 `\`。
> 原因是在 JSON 中，`\` 是转义字符（比如 `\n` 代表换行、`\t` 代表制表符），如果写成 `C:\Users\你的用户名`，JSON 会把 `\U` 当作无效转义序列，直接报错。
> 所以路径一律写成 `C:/Program Files/SumatraPDF/SumatraPDF.exe` 这种格式，或者写成 `C:\\Program Files\\SumatraPDF\\SumatraPDF.exe`（双反斜杠也可以，但 `/` 更简洁）。

粘贴后按 `Ctrl + S` 保存，重启 VS Code。

### 第七步：验证配置

1. 点击 VS Code 最上方的搜索栏，输入 `LaTeX Workshop: Build with recipe`
2. 选择 `latexmk (自动: 中文+参考文献)`
3. 重启 VS Code
4. 打开一个 `.tex` 文件，点击 ▶ 编译

如果可以正常编译出 PDF，配置就成功了 ✅

---

## 还想继续折腾？

VS Code 的魅力在于它可以无限扩展。如果想继续优化你的写作环境，可以尝试：

- 换个漂亮的主题（搜索 `theme`）
- 接入 AI 助手（GitHub Copilot、Claude Code 等）
- 配置代码片段（snippets），一键插入常用模板

祝你配置顺利，从此在 VS Code 里愉快地写 LaTeX！🚀

---

> 📝 配置文件在不同电脑上可能存在兼容性差异，如果遇到问题，可以恢复之前备份的旧配置。
