---
layout: post
title: "MATLAB 建模入门：这些函数你必须知道"
date: 2025-03-20 10:00:00 +0800
categories: 工具学习
tags: [MATLAB, 入门]
---

MATLAB 是数学建模中最常用的工具之一，强大的矩阵运算和丰富的工具箱让它成为比赛利器。这篇文章整理了我认为最实用的 MATLAB 函数。

## 数据读写

```matlab
% 读取 Excel 文件
data = xlsread('data.xlsx');

% 写入 Excel 文件
xlswrite('result.xlsx', output);

% 读取 CSV
data = csvread('data.csv');

% 保存/加载 .mat 文件
save('workspace.mat');
load('workspace.mat');
```

## 矩阵操作（重中之重）

```matlab
% 创建矩阵
A = [1 2 3; 4 5 6; 7 8 9];
B = zeros(3, 4);      % 全零矩阵
C = ones(3);          % 全一矩阵
D = eye(4);           % 单位矩阵
E = rand(3, 5);       % 均匀分布随机矩阵

% 矩阵运算
A * B;                % 矩阵乘法
A .* B;               % 元素乘法
A';                   % 转置
inv(A);               % 逆矩阵
eig(A);               % 特征值、特征向量
```

## 绘图函数

```matlab
% 二维图
x = 0:0.1:10;
y = sin(x);
plot(x, y, 'r-', 'LineWidth', 2);
xlabel('x'); ylabel('y');
title('正弦曲线');
grid on;

% 三维图
[X, Y] = meshgrid(-3:0.1:3);
Z = X.^2 + Y.^2;
surf(X, Y, Z);
colorbar;

% 子图
subplot(2, 2, 1);
```

## 统计与优化

```matlab
% 描述统计
mean(data); median(data); std(data);
max(data); min(data);

% 拟合
p = polyfit(x, y, n);     % 多项式拟合
y_fit = polyval(p, x);

% 线性规划
f = [-2, -3];             % 目标函数系数
A = [1, 1; 1, 0];         % 不等式约束
b = [8; 4];
lb = [0; 0];
[x, fval] = linprog(f, A, b, [], [], lb, []);
```

## 常用技巧

1. **向量化运算**：能用 `A.*B` 就别用 for 循环，速度差几十倍
2. **匿名函数**：`f = @(x) x^2 + sin(x);`
3. **计时**：`tic` 和 `toc` 配合使用
4. **帮助文档**：遇到不会的函数直接用 `doc 函数名`

---

*下一期我们讲 Python 做数据分析的常用库！*
