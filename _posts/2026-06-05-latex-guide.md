---
layout: post
title: "小西带你轻松掌握 LaTeX 语言！"
date: 2026-06-05 12:00:00 +0800
categories: 工具学习
tags: [工具, LaTeX, 论文写作, 排版]
description: "LaTeX 是数学建模论文排版的利器，自动管理图表编号、公式排版、参考文献引用。本文从零基础出发，详解 LaTeX 文档结构、宏包、标题层级、插图表格、公式矩阵、参考文献管理等完整知识体系，附模板使用技巧和 AI 协作方法。"
---

> 🎯 **适合人群**：数学建模参赛者、论文写作者、想写出高质量排版文档的同学

<a id="toc"></a>
## 📖 本文目录

1. [写在前面的话](#写在前面的话)
2. [第一章 LaTeX 扫盲](#第一章-latex-扫盲)
   - [Q1：什么是 LaTeX？](#q1什么是-latex)
   - [Q2：为什么要学 LaTeX？](#q2为什么要学-latex)
   - [Q3：怎么开始学？](#q3怎么开始学)
3. [第二章 LaTeX 学习](#第二章-latex-学习)
   - [1. 初识 LaTeX](#1-初识-latex)
   - [2. LaTeX 文档的结构](#2-latex-文档的结构)
   - [3. LaTeX 的宏包](#3-latex-的宏包)
   - [4. 论文信息显示——maketitle](#4-论文信息显示maketitle)
   - [5. 标题层级——搭建论文骨架](#5-标题层级搭建论文骨架)
   - [6. 目录](#6-目录)
   - [7. 字体格式——加粗、斜体等](#7-字体格式加粗斜体等)
   - [8. 特殊字符与转义](#8-特殊字符与转义)
   - [9. 段落样式——分段、分页等](#9-段落样式分段分页等)
   - [10. 列表](#10-列表)
   - [11. 插图——让图表自动编号](#11-插图让图表自动编号)
   - [12. 表格——数据与模型对比](#12-表格数据与模型对比)
   - [13. 公式——数学建模的核心武器](#13-公式数学建模的核心武器)
   - [14. 参考文献——自动管理与引用](#14-参考文献自动管理与引用)
   - [15. 附录](#15-附录)
   - [16. 插入代码块](#16-插入代码块)
4. [第三章 写在后面的话](#第三章-写在后面的话)

---

<a id="写在前面的话"></a>
## 写在前面的话

哈喽！这里是小西的知识分享系列之——带你轻松掌握 LaTeX 语言！

在学习之前，不知道你有没有遇到过这样的情况……

当你用 Word 或 WPS 写一份长篇文档时（尤其写论文），经常会在文档排版上花费很多时间和精力——在菜单栏翻来覆去地改标题和字体，怎么改都不理想；或者在论文中插入了一张图表，导致后面的编号直接乱套；特别是插入复杂的数学公式时，一个一个敲字母非常麻烦……

如果你也在为 Word 或 WPS 的排版而烦恼的话，不妨来学习一下 LaTeX！

在本攻略中，一共包括三个章节的内容，分别为 LaTeX 扫盲、语言学习和写在后面的话，希望看完后可以让你熟练掌握 LaTeX 语言，用 LaTeX 高效地写出一篇美观的论文！

> 💡 **小提示**：如果你还没看过我的 Markdown 攻略，建议先去了解一下。Markdown 和 LaTeX 是最好的搭档——**思路整理用 Markdown，论文排版用 LaTeX**！

⬇️ 下方进入正篇

在学习一门语言之前，我们需要知道这门语言是什么。那么，什么是 LaTeX 呢……

---

<a id="第一章-latex-扫盲"></a>
## 第一章 LaTeX 扫盲🧹

<a id="q1什么是-latex"></a>
### Q1：什么是 LaTeX？

LaTeX 是一门**基于代码的文档排版系统**，广泛应用于学术论文、期刊、书籍和学位论文的写作。

听到"代码排版"你可能觉得很难，但实际上——**LaTeX 的核心思想不是"画"排版，而是"写"排版**。你告诉它"这里是一级标题""这里插入公式""这里放图片"，LaTeX 会自动帮你处理好字体、间距、编号等细节。

**和 Markdown 的区别：**

| | Markdown | LaTeX |
|:---|:---|:---|
| 定位 | 轻量快速记录 | 专业排版输出 |
| 学习成本 | 极低，10 分钟上手 | 中等，但有模板就不怕 |
| 公式能力 | 支持基础 LaTeX 公式 | 完整数学排版体系 |
| 自动编号 | ❌ | ✅ 图表公式全自动 |
| 参考文献 | 不支持 | ✅ `.bib` 文件自动管理 |
| 适合场景 | 记笔记、打草稿、AI 协作 | 论文、报告、书籍出版 |

**打个比方：** Markdown 是随手画草图的铅笔，LaTeX 是精雕细琢的刻刀。两者搭配，天下无敌 👊

---

<a id="q2为什么要学-latex"></a>
### Q2：为什么要学 LaTeX？

数模比赛的论文排版直接影响到评委的阅读体验，而 LaTeX 在这几个方面完胜 Word：

**1. 数学公式——专业且高效**

在 Word 里敲个矩阵要一个个点符号，在 LaTeX 里几行代码搞定：

```latex
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
```

> 💡 插入公式的代码看不懂也没关系，可以借助 AI 把公式快捷"翻译"为 LaTeX 代码粘贴插入哦！

**2. 自动图表编号——再也不怕编号乱**

在 Word 里插入一张新图，后面所有图号都得手动改。LaTeX 里只要用 `\label` 和 `\ref`，编号自动管理，顺序永不乱。

> 💡 不只是图表，公式、表格、章节……所有带编号的东西，都可以用同一套 `\label{}` / `\ref{}` 机制来管理！

**3. 模板即用——不需要纠结排版**

美赛、国赛都有现成的 LaTeX 模板，套进去只管填内容，格式已经帮你排好了。不需要像 Word 那样反复调字号、行距、页边距，非常方便！

**4. 支持 Git 存档——版本保存非常方便**

LaTeX 的源文件是纯文本，而不是像 Word 那样的二进制文件，因此可以通过 Git 来进行文档的保存和回档，不需要自己手打"格式修改版""1.2 版"这样的文件名。

> ⚠️ **注意**：LaTeX功能虽然强大，但LaTeX更适合撰写图表公式较多，篇幅较长的文档。如果是小篇幅或对格式无严格要求的内容（如笔记，演讲稿等）用Word或WPS会更加方便。以及LaTeX仅能直接编译出.pdf格式的文件，如果需要切换为.docx，则需要使用pandoc等工具转换，且极大概率会出现排版错乱，图表不清晰的情况，因此如果需要直接提交.docx的文档，需要考虑后再使用哦。

---

<a id="q3怎么开始学"></a>
### Q3：怎么开始学？

学习 LaTeX 有两种方式，你可以根据自己的情况选择：

**方式一：Overleaf（在线，不需要下载）** 🚀

👉 [Overleaf - Online LaTeX Editor](https://www.overleaf.com/)

Overleaf 是目前最流行的在线 LaTeX 编辑器，它最大的优点是**不用安装任何软件**、**打开网页就能写**、**可以和队友实时协作**！

> ⚠️ **注意**：Overleaf 功能虽然强大，但是免费版本对单次的编译时长存在限制，如果文件内容较多则会限制其使用，因此免费版仅适用于新手学习，不太适合写长论文。如果担心付费问题，建议本地安装 LaTeX。

**方式二：本地安装**

如果你更习惯本地写作，或者期间网络不稳定、不想付费使用的话，可以在本地搭建 LaTeX 环境：

- **编译器**：TeX Live（完整版，约 6GB）
- **编辑器**：TeXstudio（TeX Live 下载后的原生编辑界面）或 VS Code + LaTeX Workshop 插件（最主流编辑方式，支持 Agent 协作、拼写检查、代码补全等功能）

> 💡 **小建议**：前期在 Overleaf 上学语法、写初稿，到了比赛后期如果模板编译超时，可以下载 .zip 到本地 TeX Live 编译，两条路都走得通。

---

<a id="第二章-latex-学习"></a>
## 第二章 LaTeX 学习✍️

<a id="1-初识-latex"></a>
### 1. 初识 LaTeX

拿到一份 LaTeX 模板压缩包时，会看到里面有很多文件。作为模板的使用者，我们一般只关心这两个文件：

1. **xxx.tex**：这是你的 LaTeX 源文件！编译 LaTeX 需要的全部代码都放到了这里，最为重要。
2. **xxx.pdf**：这是你编译后得到的 PDF 文件，每进行一次编译，PDF 文档都会随之更新。

我们想要编辑，就需要用编辑器（如 TeXstudio）来打开这里的 .tex 文件才可以进行编辑哦！

当你用编辑器打开 .tex 文件后，你会看到界面左边是我们的代码编辑区域，而右边是我们的代码所生成的 PDF 文档。

LaTeX 中的命令都以反斜杠 `\` 开头，用到的符号均为英文符号，需要注意切换输入法。有些命令后面经常会跟随大括号 `{ }`，里面的内容则是该命令的参数。

---

<a id="2-latex-文档的结构"></a>
### 2. LaTeX 文档的结构

新手拿到一篇 LaTeX 模板时，往往会被眼前的代码搞得眼花缭乱。但实际上，每一篇模板的代码都是有迹可循的，我们来拆开看一下！

一篇 LaTeX 文档最基础的结构是：

```latex
\documentclass{article} % 声明文章的类型

\begin{document} % 文本开始
Hello LaTeX！
\end{document} % 文本结束
```

> `%` 在 LaTeX 中起到注释的作用，`%` 号后面的内容不会运行，也不会显示到 PDF 中。

其中，`\begin{document}` 前的内容叫做**"导言区"**，负责详细调控文档的格式、文档的信息等；而 `\begin{document}` 之后的内容叫做**"文本编辑区"**，负责文档内容的填充。

| 区域 | 作用 | 你需要注意的 |
|:---:|:---:|:---:|
| **导言区** | 提前声明：文章类型、用到的包、标题信息 | 模板已经写好了，一般不用动 |
| **正文区** | 你的论文内容 | 在 `\begin{document}` 和 `\end{document}` 之间写 |

在导言区，`\documentclass{article}` 负责声明该文档的类型，比如 `article`、`report`、`book` 等等。当你填入不同的文档类型时，文档的字体、页面大小、编号样式等也会随之发生变化。

在文本编辑区，`\begin{document}` 和 `\end{document}` 声明这里是文档的内容编辑区域。LaTeX 里经常会用到 `begin` 和 `end` 的语法，两层语法中间则是大括号里内容对应的**环境**。

> 💡 **小比喻**：就像是在包汉堡——上下两片面包是 `begin` 和 `end`，中间的肉饼蔬菜则是我们的内容（Hello LaTeX）。

当你编辑完代码后，右侧的 PDF 并不会自动刷新，需要我们在每编辑完一段内容后，点击上方的 ▶（像一个播放键）。左下角会显示构建进度，当构建完成后，你就可以看到右边的 PDF 文档发生变化了。如果无法编译，则新添加的内容会无法正常显示，你可以查看左下角的提示，观测是代码存在问题还是运行环境存在问题，然后进行调整修改。

看到这里有的小伙伴可能会有疑问：LaTeX 可以写中文吗？为什么我写中文会报错？

那么这就涉及到了下一个内容——LaTeX 的**"宏包"**。

---

<a id="3-latex-的宏包"></a>
### 3. LaTeX 的宏包

我们来看这一串代码：

```latex
\documentclass{article} % 声明这是一篇文章

\begin{document} % 正文开始
你好，LaTeX！
\end{document} % 正文结束
```

看起来很正常，但是运行后却发生了报错！这是为什么呢？

这是因为 LaTeX 默认是仅支持英文的，如果需要支持中文编译，则需要用到中文显示的**"宏包"**。

这里的宏包不是过年过节亲戚长辈们发的红包，而是可以让你的原生 LaTeX 拥有更多功能的"插件"。例如，插入表格有表格的宏包，插入图片有图片的宏包，中文字体也是一样。

> 💡 **小比喻**：就像用手机点外卖。手机并不能直接帮你点外卖，真正可以帮你点外卖的是 APP。手机在这里是 LaTeX，APP 是宏包。

在 LaTeX 中，添加宏包并不需要像 Python 那样自己手动下载各种库，我们只需要在导言区的文档类型下面添加：

```latex
\usepackage{ }
```

大括号里填写宏包类型，就可以直接调用该宏包，使用该宏包的功能了：

```latex
\documentclass{article}
\usepackage{ctex} % 加载中文支持宏包

\begin{document}
你好 LaTeX！% 正常显示
\end{document}
```

这里，我们因为导入了支持中文的宏包，所以可以正常显示中文啦！在后面的学习中，有些功能必须要在添加了宏包后才可以使用，否则会出现报错，需要大家注意！

下方我们正式进入基础语言的学习 👇

---

<a id="4-论文信息显示maketitle"></a>
### 4. 论文信息显示——maketitle

导言区里，我们一般还需要写上论文的信息，如标题、作者、日期等：

```latex
\title{城市交通拥堵评价与优化模型}
\author{参赛队号 2501234}
\date{\today}
```

这些信息默认是不显示在文章中的。如果我们想让这些信息显示出来，则需要在文本编辑区添加一行 `\maketitle` 的命令，这样文档的信息就会在文档中显示出来了：

```latex
\documentclass{article}           % 文档类型
\usepackage{ctex}                 % 中文支持包

\title{城市交通拥堵评价与优化模型}
\author{参赛队号 2629737}
\date{\today}

\begin{document}

\maketitle                        % 生成标题等信息

\end{document}
```

> ⚠️ **注意**：从这里开始，下方列出的代码为避免演示重复，仅会列出与该内容相关的代码进行展示。这些代码不能直接全部粘贴到 LaTeX 中运行，如需运行，则必须依赖于最基础的 `\documentclass` 和 `\begin{document}`、`\end{document}` 结构。

---

<a id="5-标题层级搭建论文骨架"></a>
### 5. 标题层级——搭建论文骨架

LaTeX 的标题层级和你的论文结构一一对应：

```latex
\section{问题重述}           % 一级标题 → 1. 问题重述
\subsection{问题背景}        % 二级标题 → 1.1 问题背景
\subsubsection{数据来源}     % 三级标题 → 1.1.1 数据来源
```

> 💡 LaTeX 中的标题是自动编号的，不需要我们自己手动更改哦！

---

<a id="6-目录"></a>
### 6. 目录

在文本编辑区添加：

```latex
\tableofcontents % 生成目录
\newpage         % 让目录单独成页
```

就可以直接生成目录了！但这样的目录格式非常简单，可能不太符合我们的需求，可以使用 `\usepackage{tocloft}` 宏包对目录进行定制。不过这点可以不用太在意，一般的模板都会对目录进行详细设定的 ✅

> 💡 国赛（全国大学生数学建模比赛）的论文是不需要目录的。

---

<a id="7-字体格式加粗斜体等"></a>
### 7. 字体格式——加粗、斜体等

| 效果 | 命令 | 说明 |
|:---|:---|---:|
| **加粗** | `\textbf{文字}` | 大部分语言都支持 |
| *斜体* | `\textit{文字}` | 用于英文术语 |
| **加粗斜体** | `\textbf{\textit{文字}}` | 命令可以嵌套 |
| 下划线 | `\underline{文字}` | 出现了下划线 |

---

<a id="8-特殊字符与转义"></a>
### 8. 特殊字符与转义

在 LaTeX 中，有几个符号有特殊含义，如果你想在正文中**显示它们本身**（而不是触发功能），需要在前面加反斜杠 `\` 来"转义"。

**最常见的需要转义的符号：**

| 符号 | 本来用途 | 想显示它需写成 |
|:---|:---|---:|
| `%` | 注释标记，`%` 后面所有内容不显示 | `\%` |
| `_` | 数学模式下标，如 `$x_1$` | `\_` |
| `&` | 表格列分隔符 | `\&` |
| `$` | 数学模式标记 | `\$` |
| `#` | 宏定义参数占位 | `\#` |
| `{``}` | 分组或参数 | `\{` `\}` |
| `~` | 不可断行空格 | `\textasciitilde{}` |
| `^` | 数学模式上标 | `\textasciicircum{}` |

**新手最常踩的两个坑：**

```latex
本文中超过 80% 的数据来自实验。   % ← ❌ 报错！% 后面全变注释了
```

正确写法：

```latex
本文中超过 80\% 的数据来自实验。   % ← ✅
```

```latex
将结果保存为 output_file.csv。     % ← ❌ 报错！_ 会进入数学模式
```

正确写法：

```latex
将结果保存为 output\_file.csv。    % ← ✅
```

> 💡 **小技巧**：如果不想逐个加反斜杠，可以用 `\verb|...|` 命令原样输出——`\verb|output_file.csv|` 或 `\verb|80%|`，里面的特殊符号不会被解析。

---

<a id="9-段落样式分段分页等"></a>
### 9. 段落样式——分段、分页等

| 命令 | 说明 |
|:---:|:---:|
| `\newpage` | 分页 |
| `\par` | 分段 |

在一段文字的末尾按两次回车键，让两端文本之间空一行，也可以实现分段。但如果两段文字只有一段回车，则会显示为一个空格。

---

<a id="10-列表"></a>
### 10. 列表

在论文中经常需要列出模型假设、算法步骤等内容，LaTeX 提供了两种列表环境。

**无序列表：** 用 `itemize` 环境，适合罗列假设条件：

```latex
\begin{itemize}
    \item 假设市场是完全竞争的
    \item 假设消费者是理性的
    \item 忽略税收和交易成本
\end{itemize}
```

效果：

- 假设市场是完全竞争的
- 假设消费者是理性的
- 忽略税收和交易成本

**有序列表：** 用 `enumerate` 环境，适合展示步骤顺序：

```latex
\begin{enumerate}
    \item 数据预处理
    \item 特征选择
    \item 模型训练
    \item 结果评估
\end{enumerate}
```

效果：

1. 数据预处理
2. 特征选择
3. 模型训练
4. 结果评估

> 💡 **嵌套技巧**：列表可以嵌套使用，只需在 `\item` 内部再放一个 `itemize` 或 `enumerate` 环境，LaTeX 会自动调整不同层级的编号样式。

---

<a id="11-插图让图表自动编号"></a>
### 11. 插图——让图表自动编号

在插入图片之前，我们一般会在论文模板所在的文件夹下，新建一个 `figures` 文件夹来存放图片文件，以便于文档路径的填写。

```latex
\usepackage{ctex}        % 支持中文字体
\usepackage{graphicx}    % 提供 \includegraphics 命令，插入图片必须
\usepackage{caption}     % 控制图注格式

\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/技术路线图.png}
    \caption{技术路线图}
\end{figure}
```

**参数说明：**

- `[htbp]`：按照顺序尝试放置该图片
- `width=0.8\textwidth`：图片宽度占页面 80%
- `figures/技术路线图.png`：图片的相对路径，图片格式推荐使用 PDF、PNG 或 JPG
- `\caption{}`：图题，LaTeX 自动编号为"图 1""图 2"……

> 💡 论文中的格式一般要求"**上表下图**"，所以表注一般在表格上方，图注一般在图片下方。

**关于 `[htbp]` 浮动位置：**

| 字母 | 含义 | 优先级 |
|:---|:---|---:|
| `h` | here，尽量放在这个位置 | 最高 |
| `t` | top，可以放在页面顶部 | 次高 |
| `b` | bottom，可以放在页面底部 | 第三 |
| `p` | page，可以单独占一页 | 最低 |

LaTeX 会按 `h → t → b → p` 的顺序尝试放置。写成 `[htbp]` 就是"给最大自由度"。如果图片浮动位置不理想，可以在导言区添加 `\usepackage{float}` 宏包，把 `[htbp]` 换成 `[H]`，表示"图片严格放在此处，不浮动"。

**不同 `width` 值的效果：**

| 数值 | 效果 | 推荐场景 |
|:---|:---|:---|
| `0.3~0.4\textwidth` | 小图 | 两个小图并排、小图标 |
| `0.5~0.6\textwidth` | 中等图 | 普通大小的图表，旁边可以排文字 |
| `0.7~0.8\textwidth` | 大图 | 论文中最常用，清晰且不溢出 |
| `1.0\textwidth` | 占满宽度 | 大图、表格截图、地图 |
| `>1.0\textwidth` | 超出页面 | ❌ 不推荐，会溢出到右边界外 |

**在正文中引用图片编号：**

```latex
\usepackage{ctex}        % 支持中文字体
\usepackage{graphicx}    % 提供 \includegraphics 命令，插入图片必须
\usepackage{caption}     % 控制图注格式
\usepackage{float}       % 支持图片严格放在此处的功能

\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/技术路线图.png}
    \caption{技术路线图}
    \label{Technology Roadmap}
\end{figure}
```

在正文中引用：

```latex
如图 \ref{Technology Roadmap} 所示，数据呈现明显的线性趋势……
```

> 💡 第一次编译时可能显示 `??`，需要**编译两次**才可以显示编号。命令缩进非必须，但缩进后代码更易于阅读。无论前面插了多少张图，`\ref{}` 永远指向正确的图号——再也不用像 Word 那样手动改编号了！表格也是同理哦！

> 💡 **偷懒技巧**：如果你的图片还没有做好，想先占一个位置，可以用 `%` 把 `\includegraphics` 这一行注释掉，等图片有了之后再取消注释。

---

<a id="12-表格数据与模型对比"></a>
### 12. 表格——数据与模型对比

论文中使用的一般都是三线表，第一行是字段，下方是内容：

```latex
\usepackage{ctex}       % 支持中文字体
\usepackage{booktabs}   % 三线表必须
\usepackage{caption}    % 优化表注样式
\captionsetup[table]{font={bf}} % 表注加粗

\begin{table}[htbp]
    \centering
    \caption{各变量统计描述}
    \label{Description of Variables}
    \begin{tabular}{l c c c}
        \toprule
        变量 & 样本量 & 均值 & 标准差 \\
        \midrule
        房价（万元） & 500 & 3.25 & 1.02 \\
        面积（m²）  & 500 & 89.6 & 15.3 \\
        房龄（年）  & 500 & 5.8  & 3.1  \\
        \bottomrule
    \end{tabular}
\end{table}
```

**各部分详解：**

`table` 负责表格的位置浮动和编号，`tabular` 负责画表格和内容的填充。

`\captionsetup[table]{font={bf}}` 的含义：

| 部分 | 含义 |
|:---|:---|
| `\captionsetup` | 标题格式设置命令（来自 `caption` 宏包） |
| `[table]` | 只对**表格**的标题生效（不影响图片的标题） |
| `font={bf}` | 把字体设置为 **bf**（boldface，粗体） |

`{l c c c}` 定义了**四列**的对齐方式：

| 列号 | 对齐方式 | 含义 |
|:---|:---|---:|
| 第1列 | `l` | 左对齐（left） |
| 第2列 | `c` | 居中对齐（center） |
| 第3列 | `c` | 居中对齐 |
| 第4列 | `c` | 居中对齐 |

如果想要竖线，可以写 `|l|c|c|c|`，但三线表**不需要竖线**。

**三线表的横线命令：**

| 命令 | 作用 |
|:---|:---|
| `\toprule` | 三线表的**最上面那条横线**（比普通的 `\hline` 更粗、上下间距更好） |
| `\midrule` | **表头和数据之间**的那条横线（比 `\toprule` 细） |
| `\bottomrule` | 表格的**最下面那条横线**（和 `\toprule` 一样粗） |

**分隔符说明：**

| 符号 | 含义 |
|:---|:---|
| `&` | 分隔列。一行有 4 列，就需要 3 个 `&` |
| `\\` | 换行。表示这一行结束，下一行是新的一行 |

> 💡 数字之间的空格不影响编译结果，只是为了让你在代码中看得更清楚。
>
> 💡 **偷懒技巧**：把表格拍照发给 AI，说"请给我该公式的 LaTeX 代码"，粘贴代码也很方便！

---

<a id="13-公式数学建模的核心武器"></a>
### 13. 公式——数学建模的核心武器

LaTeX 的公式能力是它最大的优势之一，也是数模论文中最常用的功能。

**行内公式：** 用单个 `$` 包裹，放在文字段落中：

```latex
设回归模型为 $y = \beta_0 + \beta_1 x + \varepsilon$，其中……
```

效果：设回归模型为 $y = \beta_0 + \beta_1 x + \varepsilon$，其中……

**不带编号的行间公式：** 用 `\[ ... \]`：

```latex
\[
\hat{\beta} = (X^T X)^{-1} X^T Y
\]
```

**带编号的公式：** 使用 `equation` 环境：

```latex
\begin{equation}
R^2 = 1 - \frac{SS_{res}}{SS_{tot}} = 1 - \frac{\sum (y_i - \hat{y}_i)^2}{\sum (y_i - \bar{y})^2}
\label{eq:rsquared}
\end{equation}
```

**多行公式对齐：** 使用 `align` 环境：

```latex
\usepackage{amsmath}   % 必须的宏包
\usepackage{amssymb}   % 提供额外的数学符号

\begin{align}
\min \quad & Z = \sum_{i=1}^{n} \sum_{j=1}^{m} c_{ij} x_{ij} \\
\text{s.t.} \quad & \sum_{j=1}^{m} x_{ij} = 1, \quad \forall i \\
& x_{ij} \in \{0, 1\}, \quad \forall i, j
\label{eq:model}
\end{align}
```

**矩阵：**

```latex
\usepackage{amsmath}
\usepackage{amssymb}

\[
A = \begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
\]
```

**分段函数：**

```latex
\usepackage{amsmath}
\usepackage{amssymb}

\begin{equation}
f(x) =
\begin{cases}
x^2, & x \geq 0 \\
-x, & x < 0
\end{cases}
\label{eq:piecewise}
\end{equation}
```

> 💡 **偷懒技巧**：
> 1. 把公式拍照发给 AI，说"请给我该公式的 LaTeX 代码"，或使用 LaTeX Snipper 等截图转 LaTeX 工具，快速插入
> 2. 你在 Markdown 攻略里写的公式，可以**直接复制**到 LaTeX 中使用——语法完全一致！

---

<a id="14-参考文献自动管理与引用"></a>
### 14. 参考文献——自动管理与引用

手动管理参考文献在 Word 中非常麻烦——文献引用顺序一变，引用编号和参考文献顺序都需要自己手动修改。在 LaTeX 中，有两种插入参考文献的方式。

#### 方式一：`thebibliography` 环境（适合文献数量少的情况）

比如数学建模论文的参考文献一般较少，用这种方式就够了：

```latex
\usepackage[super, square, sort&compress]{natbib} % 设置上标样式

\begin{thebibliography}{99}
    \bibitem{1} Breiman L. Random forests[J]. Machine Learning, 2001, 45(1): 5-32.
    \bibitem{2} Soltani A, Lee C L. The non-linear dynamics of south australian regional housing markets: a machine learning approach[J]. Applied Geography, 2024, 166: 103248.
    \bibitem{3} ......
\end{thebibliography}
```

**在正文中引用：**

```latex
随机森林由Breiman \cite{1}于2001年提出……
```

> ⚠️ 同样需要编译两次才可以正常显示引用的编号。图注标注的引用是 `\ref{}`，参考文献的引用是 `\cite{}`，注意区分哦。

**参数说明：**

| 代码 | 作用 |
|:---|:---|
| `\cite{1}` | 在正文中引用，编译后显示为 `[1]` |
| `\begin{thebibliography}{99}` | 开始参考文献环境，`99` 表示最大编号范围 |
| `\bibitem{1}` | 定义一条参考文献，大括号里的内容是它的名字（和 `\cite` 中的名字对应） |
| `...` | 文献的具体信息（作者、题目、期刊等） |
| `\end{thebibliography}` | 结束环境 |

#### 方式二：BibTeX（适合文献数量多或需要换期刊格式的场景）

> 注意：该方式支持 Overleaf 和 TeXstudio 环境，VSCode 中默认不支持，需要在 `setting.json` 中额外配置。

**步骤 1：创建 `.bib` 文件**

创建一个 `references.bib` 文件放到 .tex 所在的文件夹中，其内容一般是这样的：

```bibtex
@article{he2016resnet,
    author  = {He, Kaiming and Zhang, Xiangyu and Ren, Shaoqing and Sun, Jian},
    title   = {Deep Residual Learning for Image Recognition},
    journal = {CVPR},
    year    = {2016},
    pages   = {770--778}
}

@article{lecun1998lenet,
    author  = {LeCun, Yann and Bottou, Léon and Bengio, Yoshua and Haffner, Patrick},
    title   = {Gradient-Based Learning Applied to Document Recognition},
    journal = {Proceedings of the IEEE},
    year    = {1998},
    volume  = {86},
    number  = {11},
    pages   = {2278--2324}
}
```

**`.bib` 文件格式说明：**

| 部分 | 含义 | 示例 |
|:---|:---|---:|
| `@article` | 文献类型（期刊论文） | |
| `{he2016resnet}` | 引用标签（唯一标识，自己起名） | 正文中用 `\cite{he2016resnet}` |
| `author = {}` | 作者 | |
| `title = {}` | 标题 | |
| `journal = {}` | 期刊名 | |
| `year = {}` | 年份 | |

**常见文献类型：**
- `@article`：期刊论文
- `@book`：书籍
- `@inproceedings`：会议论文
- `@misc`：网页、报告等

> 💡 实际写作中，`.bib` 文件手动创建非常麻烦，所以我们一般使用知网或 Zotero 的 Better BibTeX 插件来快速导出我们需要的 `.bib` 文件，具体步骤见我后面的文献导出教程及 Zotero 教程。

**步骤 2：在 `.tex` 文件中引用**

```latex
\usepackage[super, square, sort&compress]{natbib} % 设置上标样式

\begin{document}
残差网络\cite{he2016resnet}解决了深层网络退化问题。
手写数字识别\cite{lecun1998lenet}是卷积神经网络的经典应用。

\bibliographystyle{unsrt}  % 参考文献格式
\bibliography{references}  % 引用 .bib 文件
\end{document}
```

**编译流程（重要）：**

BibTeX 需要**多次编译**才能正确生成引用：

```
pdflatex main.tex      # 第一次编译，生成 .aux 文件
bibtex main            # 处理文献，生成 .bbl 文件
pdflatex main.tex      # 第二次编译，嵌入文献
pdflatex main.tex      # 第三次编译，解决交叉引用
```

> 💡 如果你使用的是 Zotero 的 Better BibTeX 插件生成的 `.bib` 文件，还可以实现参考文献目录的实时更新哦！
>
> 同一篇论文的参考文献格式应该保持一致。国内论文的参考文献格式一般是 GB/7714-2015，国外论文使用的一般是 APA。

---

<a id="15-附录"></a>
### 15. 附录

```latex
\usepackage{appendix}   % 支持附录环境

\begin{document}

\section{正文}
\centerline{\Large\bfseries 附 录}   % 添加附录标题
\begin{appendices}
    \section{数据说明}
    \section{核心代码}
    ......
\end{appendices}

\end{document}
```

---

<a id="16-插入代码块"></a>
### 16. 插入代码块

论文的附录经常需要插入代码块。在 LaTeX 中插入代码块有两种方式：

#### 方式一：从文件插入（推荐，适合代码文件较多）

新建一个 `codes` 文件夹，将代码放进去，LaTeX 通过路径引用：

```latex
\usepackage{listings}        % 代码插入宏包
\usepackage{xcolor}          % 颜色支持（可选）
\lstset{                             % 代码样式设置
    basicstyle=\ttfamily\small,      % 等宽字体，小号字
    keywordstyle=\color{blue},       % 关键字蓝色
    commentstyle=\color{green!50!black}, % 注释绿色
    stringstyle=\color{red},         % 字符串红色
    numbers=left,                    % 行号在左侧
    numberstyle=\tiny,               % 行号字体大小
    breaklines=true,                 % 自动换行
    frame=single,                    % 加边框
    tabsize=4                        % Tab 缩进 4 空格
}

\lstinputlisting[language=Python, caption={随机森林模型代码}, label={code:model}]{codes/model.py}
```

#### 方式二：直接写在 .tex 文件中（适合代码文件较少）

```latex
\usepackage{listings}
\usepackage{xcolor}
\lstset{
    basicstyle=\ttfamily\small,
    keywordstyle=\color{blue},
    commentstyle=\color{green!50!black},
    stringstyle=\color{red},
    numbers=left,
    breaklines=true,
    frame=single
}

\begin{lstlisting}[language=Python, caption={随机森林模型代码}, label={code:model}]
import numpy as np
import pandas as pd

def train_model(X, y):
    """训练模型"""
    model = RandomForestRegressor()
    model.fit(X, y)
    return model

if __name__ == "__main__":
    print("训练完成")
\end{lstlisting}
```

**正文中的引用：**

```latex
核心代码详见代码\ref{code:model}。
```

#### 伪代码

如果你插入的是算法伪代码（不是可运行的代码）：

```latex
\usepackage{algorithm}
\usepackage{algpseudocode}

\begin{algorithm}
    \caption{梯度下降}
    \label{alg:gd2}
    \begin{algorithmic}[1]
        \Require 学习率 $\alpha$，初始参数 $\theta_0$，迭代次数 $T$
        \Ensure 最优参数 $\theta^*$
        \State $\theta \leftarrow \theta_0$
        \For{$t = 1$ to $T$}
            \State $g \leftarrow \nabla L(\theta)$
            \State $\theta \leftarrow \theta - \alpha g$
        \EndFor
        \State \Return $\theta$
    \end{algorithmic}
\end{algorithm}
```

> 💡 **小提示**：比赛时如果代码太长，附录只放核心函数即可。伪代码比完整代码更适合放在正文中，评委更关注算法思路而非编程细节。

---

<a id="第三章-写在后面的话"></a>
## 第三章 写在后面的话💬

看到这里的你可能已经被各种 `\` 开头的命令看晕了……没关系，这是正常的！

学习 LaTeX 最好的方式不是死记硬背命令，而是——

**直接从模板开始，边用边学。**

你不需要记住所有命令，你需要记住的是：

1. **哪里找模板**——Overleaf、GitHub、Bilibili 上都能找到模板库，搜 "MCM""国赛" 都可以
2. **怎么用模板**——知道模板中不同代码的用途和含义，学会使用模板撰写论文
3. **哪里问 AI**——把需求告诉 AI："帮我生成该公式的 LaTeX 代码"，快捷方便

**Markdown + LaTeX 的最佳搭档**

如果你完整看完了小西的 Markdown 攻略和这篇 LaTeX 教程，你就拥有了数模比赛中最强的写作武器：

> **思路整理** → Markdown 快速记录，公式 / 代码 / 想法全部存好<br>
> **论文写作** → LaTeX 套用模板，把 Markdown 的内容迁移过来，排版自动完成<br>
> **最终提交** → 一键编译生成 PDF，格式完美，评委看了都舒服 💯

就是这样！

---

> 📝 我的经验还很有限，攻略内容可能还有很多不足之处，欢迎大家提出修改意见！

---

版本 1.0 | 更新于 2026 年 6 月 5 日 | 和小西 Markdown 攻略搭配食用效果更佳 🚀
