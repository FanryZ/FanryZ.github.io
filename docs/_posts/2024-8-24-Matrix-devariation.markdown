---
layout: post
title:  "矩阵求导"
date: 2024-8-24
categories: math matrix
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

研究生之后很少钻研数学了，以至于现在看到论文中的数学推导竟会产生一种畏惧感。这两天把本科时候的数学笔记从书架上找出来，找找有哪些遗忘又有用的知识点，趁着空闲时间转录到个人博客上。这个系列从矩阵求导开始。

我们采用矩阵求导的分子布局，$f(x) \in \mathbb{R}^{n\times 1}, x \in \mathbb{R}^{m \times 1}, A \in \mathbb{R}^{n\times m}$ ：

$$ f(x) = Ax \Rightarrow \frac{\partial}{\partial x}f(x)\ or\ \triangledown_x f(x) = A $$

按照定义，Hessian 矩阵可以表示为 $\frac{\partial^2 f}{\partial x \partial x^T}$ .

矩阵求导存在如下性质：

$$\frac{\partial f(x)^T}{\partial x} = (\frac{\partial f(x)}{x})^T $$

$$\frac{\partial W}{\partial U} = \frac{\partial W}{\partial V} \frac{\partial V}{\partial U}$$

<!-- $$ 规定 \frac{\partial (WX)}{\partial X} = W$$ -->

实值与向量的相互求导可以通过函数元素与变量元素的两两标量求导理解。我们考虑标量 $f$ 对矩阵 $A$ 的求导，这也是优化中最常见的求导形式：

$$ \delta f = \sum_{i, j}(\triangledown_x f)_{ij}(\delta x)_{ij} = tr((\triangledown_x f)^T \delta x)$$

于是我们存在两种矩阵求导方法：直接求导与微分法。

例：学习仿射变换 $argmin_{A, b}f(A, b) = \frac{1}{2m}\sum ||Ax_i + b - y_i||_2^2$

有

$$ f(A, b) = \frac{1}{2m}||AX + be^T - Y||_F^2 $$

其中 $X = [x_1, x_2, \cdots, x_m]$, $Y = [y_1, y_2, \cdots, y_m]$, $e = [1\ 1\ \cdots\ 1]^T$.

$$ f(A, b) = \frac{1}{2m} tr((AX + be^T - Y)^T(AX + be^T - Y)) $$

所以

$$ \triangledown_Af = \frac{1}{m} X(AX + be^T - Y)^T$$

$$ \triangledown_bf = \frac{1}{m} e^T(AX + be^T - Y)$$

令 $\triangledown_Af = 0, \triangledown_bf = 0$ 解得最终结果。

练习：推导 PCA (主成分分析) 。
