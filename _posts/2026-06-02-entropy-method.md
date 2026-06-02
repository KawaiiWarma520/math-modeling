---
layout: post
title: "熵权法：基于数据离散程度的客观赋权方法"
date: 2026-06-02 12:00:00 +0800
categories: 模型百科
tags: [评价模型, 熵权法, 客观赋权, 综合评价]
description: "熵权法通过分析指标数据的离散程度（信息熵）客观确定权重，是数学建模中最常用的客观赋权方法之一。本文详解归一化→比重→熵值→差异系数→权重完整流程，附 Python 代码及与 AHP 的对比分析。"
---

## 🧠 基本概念

**一句话定义**：熵权法是一种根据各指标数据的**离散程度**（变异程度）客观计算权重的多指标决策方法。

**核心思想**：
- **熵**在信息论中代表“混乱程度”或“不确定性”
- 数据越混乱（差异越大）→ 信息量越大 → 权重越高
- 数据越一致（大家差不多）→ 信息量越小 → 权重越低

**与 AHP 的对比**：

| 维度 | AHP（主观赋权） | 熵权法（客观赋权） |
|:---|:---|:---|
| 依据 | 专家判断、主观经验 | 数据本身的离散程度 |
| 优点 | 能反映实际情况 | 完全客观、可复现 |
| 缺点 | 主观性强 | 依赖数据质量 |
| 适用 | 无数据、定性问题 | 有数据、定量问题 |

## 📊 适用场景

| 场景 | 说明 | 例子 |
|:---|:---|:---|
| 多指标综合评价 | 有客观数据，需要确定各指标权重 | 城市空气质量评价、学生综合素质评价 |
| 与 AHP 结合 | 主客观结合，更科学 | 先用 AHP 得主观权重，再用熵权法得客观权重，取平均 |
| 数据驱动的决策 | 完全靠数据说话，避免人为偏见 | 供应商选择、投资方案评价 |
| 作为 TOPSIS 的前置 | 熵权法算权重，TOPSIS 算得分 | 国赛 C 题常用组合 |

## 🏆 经典例子

**城市环境质量评价**：

> 评价三个城市的环境质量，考虑两个指标：空气质量（越高越好）和污染排放（越低越好）

| 城市 | 空气质量 | 污染排放 |
|:---|:---|:---|
| A | 80 | 30 |
| B | 60 | 50 |
| C | 40 | 70 |

**计算过程**（见解题步骤）得出两个指标权重各为 0.5。


## 🛠️ 解题步骤

### Step 1：数据准备

构造评价矩阵：$n$ 个评价对象，$m$ 个评价指标

$$
X = \begin{bmatrix}
x_{11} & x_{12} & \cdots & x_{1m} \\
x_{21} & x_{22} & \cdots & x_{2m} \\
\vdots & \vdots & \ddots & \vdots \\
x_{n1} & x_{n2} & \cdots & x_{nm}
\end{bmatrix}
$$

### Step 2：数据归一化（消除量纲，统一为越大越好）

| 指标类型 | 公式 |
|:---|:---|
| 正向指标（越大越好） | $p_{ij} = \frac{x_{ij} - \min(x_j)}{\max(x_j) - \min(x_j)}$ |
| 负向指标（越小越好） | $p_{ij} = \frac{\max(x_j) - x_{ij}}{\max(x_j) - \min(x_j)}$ |

得到归一化矩阵 $P$。

### Step 3：计算比重（第 j 个指标下，第 i 个对象的占比）

$$
q_{ij} = \frac{p_{ij}}{\sum_{i=1}^{n} p_{ij}}
$$

**注意**：若 $p_{ij}=0$，则直接取 $q_{ij}=0$（避免后续 $\ln(0)$ 出错）。

### Step 4：计算第 j 个指标的熵值

$$
e_j = -\frac{1}{\ln n} \sum_{i=1}^{n} q_{ij} \ln(q_{ij})
$$

其中 $0 \leq e_j \leq 1$，规定当 $q_{ij}=0$ 时，$q_{ij} \ln(q_{ij}) = 0$。

**理解**：
- $e_j$ 越大 → 数据越一致 → 信息量越小
- $e_j$ 越小 → 数据差异越大 → 信息量越大

### Step 5：计算差异系数

$$
d_j = 1 - e_j
$$

差异系数越大，说明该指标越重要。

### Step 6：计算权重

$$
w_j = \frac{d_j}{\sum_{j=1}^{m} d_j}
$$

所有权重之和为 1。

## ⚠️ 注意事项

**1. 熵权法不能单独使用**
- 熵权法只给权重，不给最终得分
- 通常搭配 TOPSIS 或加权求和使用

**2. 必须做归一化**
- 消除量纲，统一为“越大越好”
- 与多目标规划的归一化公式相同，但熵权法多了一步“计算比重”

**3. 零值处理**
- 当 $p_{ij}=0$ 时，$q_{ij}=0$，直接令 $q_{ij} \ln(q_{ij}) = 0$
- 也可以给所有 $p_{ij}$ 加一个极小值（如 $10^{-8}$）避免零值

**4. 熵权法的局限性**
- 权重完全依赖数据，不考虑指标的实际意义
- 对异常值敏感（一个极端值会放大差异）
- 样本量太小时不适用（建议 $n > m$）

**5. 与 AHP 结合是加分项**
- 主观权重 + 客观权重 → 组合权重更科学

## ✏️ 学术写作

**摘要中的表述**：
> 本文采用熵权法确定各评价指标的权重。首先对原始数据进行归一化处理，计算各指标的信息熵，进而得到差异系数和客观权重。结果表明，XX 指标的权重最大，说明其对评价结果影响最为显著。

**模型建立部分的模板**：

> **1. 数据归一化**
>
> 为消除量纲影响并统一指标方向，对原始数据进行归一化处理。对于正向指标（越大越好）：
> $$p_{ij} = \frac{x_{ij} - \min(x_j)}{\max(x_j) - \min(x_j)}$$
> 对于负向指标（越小越好）：
> $$p_{ij} = \frac{\max(x_j) - x_{ij}}{\max(x_j) - \min(x_j)}$$
>
> **2. 计算比重**
>
> $$q_{ij} = \frac{p_{ij}}{\sum_{i=1}^{n} p_{ij}}$$
>
> **3. 计算熵值**
>
> $$e_j = -\frac{1}{\ln n} \sum_{i=1}^{n} q_{ij} \ln(q_{ij})$$
>
> **4. 计算差异系数**
>
> $$d_j = 1 - e_j$$
>
> **5. 计算权重**
>
> $$w_j = \frac{d_j}{\sum_{j=1}^{m} d_j}$$

**结果分析中的表述**：
> 由熵权法计算得到的权重可知，XX 指标的权重为 0.42，显著高于其他指标（YY 权重 0.28，ZZ 权重 0.30），说明该指标在不同对象间的差异最大，是评价优劣的关键因素。

**与 AHP 结合的组合权重**：
> 本文采用 AHP 法得到主观权重 $w_j^{(1)}$，采用熵权法得到客观权重 $w_j^{(2)}$，取算术平均得到组合权重：
> $$w_j = \frac{w_j^{(1)} + w_j^{(2)}}{2}$$

## 💻 代码实现


```Python
import numpy as np
import pandas as pd

def entropy_weight(data, direction='positive'):
    """
    熵权法计算权重
    data: numpy array, 形状 (n_samples, n_features)
    direction: 各指标的方向，'positive'表示越大越好，'negative'表示越小越好
               可以是字符串（所有指标相同）或列表（逐个指定）
    """
    X = np.array(data)
    n, m = X.shape
    
    # Step 1: 归一化（统一为越大越好）
    P = np.zeros_like(X)
    for j in range(m):
        min_j = np.min(X[:, j])
        max_j = np.max(X[:, j])
        
        # 处理全为常数的情况
        if max_j - min_j == 0:
            P[:, j] = 1
        else:
            if (isinstance(direction, str) and direction == 'positive') or \
               (isinstance(direction, list) and direction[j] == 'positive'):
                # 正向指标
                P[:, j] = (X[:, j] - min_j) / (max_j - min_j)
            else:
                # 负向指标
                P[:, j] = (max_j - X[:, j]) / (max_j - min_j)
    
    # Step 2: 计算比重 q_{ij}
    # 防止除零，加极小值
    row_sum = np.sum(P, axis=0)
    row_sum[row_sum == 0] = 1e-10
    Q = P / row_sum
    
    # Step 3: 计算熵值 e_j
    # 处理 q=0 的情况：0 * ln(0) = 0
    with np.errstate(divide='ignore', invalid='ignore'):
        lnQ = np.where(Q == 0, 0, np.log(Q))
    entropy = -1 / np.log(n) * np.sum(Q * lnQ, axis=0)
    
    # Step 4: 计算差异系数
    d = 1 - entropy
    
    # Step 5: 计算权重
    weights = d / np.sum(d)
    
    return weights, entropy

# ========== 例子：城市环境质量评价 ==========
data = np.array([
    [80, 30],  # 城市A：空气质量，污染排放
    [60, 50],  # 城市B
    [40, 70]   # 城市C
])

# 空气质量是正向指标（越大越好），污染排放是负向指标（越小越好）
weights, entropies = entropy_weight(data, direction=['positive', 'negative'])

print("=== 熵权法计算结果 ===")
print(f"指标熵值: {entropies}")
print(f"指标权重: {weights}")
print(f"权重之和: {np.sum(weights)}")

# ========== 通用模板 ==========
def get_weights(data, directions):
    """
    获取权重的快捷函数
    data: 数据矩阵，每列是一个指标，每行是一个样本
    directions: 每个指标的方向列表，如 ['positive', 'negative', 'positive']
    """
    weights, _ = entropy_weight(data, directions)
    return weights

# 使用示例
# directions = ['positive'] * data.shape[1]  # 所有指标都是正向
# weights = get_weights(data, directions)
```


## 🔗 关联模型

| 模型              | 关系     | 何时使用                      |
| --------------- | ------ | ------------------------- |
| **AHP**         | 主观赋权法  | 与熵权法形成主客观对比，可组合使用         |
| **TOPSIS**      | 综合评价方法 | 熵权法提供权重，TOPSIS 计算得分（经典组合） |
| **多目标规划**       | 目标赋权   | 归一化公式相同，但用途不同             |
| **主成分分析 (PCA)** | 降维方法   | 另一种客观赋权思路                 |
| **CRITIC 法**    | 客观赋权法  | 同时考虑变异性和相关性               |