# 基础知识

## 凸集与分离超平面定理
回忆基础知识，集合 $X \subseteq \mathbb{R}^n$ 是凸（convex）的，当且仅当对于任意的 $x, y \in X$ 和 $0 \leqslant \lambda \leqslant 1$，都有 $\lambda x + (1 - \lambda) y \in X$。令 $x^0,x^1,\ldots,x^k \in \mathbb{R}^n$，则 $x^0,x^1,\ldots,x^k$ 的凸包（convex hull）$\text{conv}(x^0,x^1,\ldots,x^k)$ 定义为

$$ \text{conv}(x^0,x^1,\ldots,x^k) = \left\{ \sum_{i=0}^k \lambda_i x^i \mid \lambda_i \geqslant 0, \sum\limits_{i=0}^k \lambda_i = 1 \right\} $$

其中 $\sum\limits_{i=0}^k \lambda_i x^i$ 称为 $x^0,x^1,\ldots,x^k$ 的凸组合。凸包是凸集的一个重要概念，不难验证它是包含 $x^0,x^1,\ldots,x^k$ 的最小凸集。

<div style="text-align: center;">
<img src="/assets/images/tcs/optimization/basic/extreme.png" width="50%" style="margin: 0 auto;">
</div>

## 仿射无关性


## 单纯形
