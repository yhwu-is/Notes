# 基础知识

## 凸集与分离超平面定理
### 凸集
回忆基础知识，集合 $X \subseteq \mathbb{R}^n$ 是**凸（convex）的**，当且仅当对于任意的 $x, y \in X$ 和 $0 \leqslant \lambda \leqslant 1$，都有 $\lambda x + (1 - \lambda) y \in X$。令 $x^0,x^1,\ldots,x^k \in \mathbb{R}^n$，则 $x^0,x^1,\ldots,x^k$ 的**凸包（convex hull）**$\text{conv}(x^0,x^1,\ldots,x^k)$ 定义为

$$ \text{conv}(x^0,x^1,\ldots,x^k) = \left\{ \sum_{i=0}^k \lambda_i x^i \mid \lambda_i \geqslant 0, \sum\limits_{i=0}^k \lambda_i = 1 \right\} $$

其中 $\sum\limits_{i=0}^k \lambda_i x^i$ 称为 $x^0,x^1,\ldots,x^k$ 的凸组合。凸包是凸集的一个重要概念，不难验证它是包含 $x^0,x^1,\ldots,x^k$ 的最小凸集。

令 $X \subseteq \mathbb{R}^n$ 是一个凸集，向量 $x \in X$ 是 $X$ 的一个**极端点（extreme point）**，当且仅当对于任意的 $y, z \in X$ 和 $0 < \lambda < 1$，都有 $x \neq \lambda y + (1 - \lambda) z$。即极端点无法被表达为两个不同的点的凸组合，或者说不存在一个开区间包含 $x$ 且完全包含在 $X$ 中。下图描述了圆盘和正方形的极端点，实际上非常符合我们的直观：圆盘的极端点就是整个最外圈的圆，正方形的极端点就是正方形的顶点。

<div style="text-align: center;">
<img src="/Notes/assets/images/tcs/optimization/basic/extreme.png" width="25%" style="margin: 0 auto;">
</div>

有一个基本的结果是，如果 $X$ 是一个闭集，那么对每个点 $x \notin X$，至少存在一个点 $y$ 距离 $x$ 最近。我们将要证明的是，如果 $X$ 是闭凸集，这一最近的点是唯一的：

!!! 定理
    令 $X \subseteq \mathbb{R}^n$ 是一个闭凸集，$x \in \mathbb{R}^n$ 是一个不在 $X$ 中的点，则存在唯一的 $y \in X$，使得 $d(x,X) = d(x,y)$。

!!! 证明
    首先根据闭集可知至少存在一个点 $y \in X$，使得 $d(x,X) = d(x,y)$。接下来用反证法，假设存在另一个点 $z \in X$ 使得 $d(x,z) = d(x,X)$，因为 $X$ 是凸集，$\dfrac{y+z}{2} \in X$，我们证明 $d(x,\dfrac{y+z}{2}) < d(x,y)$ 来得到矛盾（因为 $y$ 是距离 $x$ 最近的点）。我们可以定义函数 $D: \mathbb{R} \to \mathbb{R}$ 为 
    
    $$\begin{aligned}
        D(\alpha) &= d(x,\alpha y + (1 - \alpha) z) \\
                  &= \sum\limits_{i=1}^n (x_i - \alpha y_i - (1 - \alpha) z_i)^2 \\
                  &= \sum\limits_{i=1}^n (x_i - z_i - \alpha (y_i - z_i))^2
    \end{aligned}$$

    事实上这是关于 $\alpha$ 的一个二次函数，并且 $\alpha^2$ 的系数是正数，根据 $D(0) = D(1)$ 可知 $D(\alpha)$ 在 $(0,1)$ 内取得最小值，实际上根据对称性就是 $D(1/2)$，因此 $d(x,\dfrac{y+z}{2}) < d(x,y)$，得到矛盾。

下面是一个无关的结论，放在这里只是因为想起来有这么个结果，然后也为了提醒一下我自己学过这一结论：
!!! 一个补充的结论
    设 $X$ 是一个闭集，$Y$ 是一个集合，满足 $X \cap Y = \varnothing$，那么

    1. 若 $Y$ 是紧集，则 $d(X,Y) > 0$；
    2. 若 $Y$ 是闭集，则 $d(X,Y)$ 可能等于 $0$。

!!! 补充结论的证明
    1. 因为 $X \cap Y = \varnothing$，因此对于任意的 $y \in Y$，都存在 $\delta_y$ 使得 $d(y,X) > 2\delta_y$，故 $B(y,\delta_y) \cap X = \varnothing$。因为 $Y$ 是紧集，因此存在有限个 $y_1,y_2,\ldots,y_k$ 使得 $Y \subseteq \bigcup\limits_{i=1}^k B(y_i,\delta_{y_i})$。令 $\delta = \min\{\delta_{y_1},\delta_{y_2},\ldots,\delta_{y_k}\}$，则 $\forall x \in X, y \in Y$，都存在一个 $i$ 使得 $y \in B(y_i,\delta_{y_i})$，即 $|y - y_i| \leqslant \delta_{y_i}$，因此 $|x - y| \geqslant |x - y_i| - |y - y_i| > 2\delta_{y_i} - \delta_{y_i} = \delta_{y_i} \geqslant \delta$，即 $d(X,Y) \geqslant \delta > 0$。
    2. 只需注意到 $y = 1/x$ 的函数曲线与 $x$ 轴都是闭集，但它们之间的距离为 $0$ 即可。

### 分离超平面定理
在应用中有一个非常常用的结论，即**分离超平面定理（Separating Hyperplane Theorem）**。为了描述这一定理，我们首先需要定义一些术语：

!!! 超平面定义
    $\mathbb{R}^n$ 中的一个**超平面（hyperplane）** $H(\alpha,\beta)$ 可以由一个法向量 $\alpha \in \mathbb{R}^n$ 和一个标量 $\beta \in \mathbb{R}$ 确定，即

    $$ H(\alpha,\beta) = \{ x \in \mathbb{R}^n \mid \langle \alpha,x \rangle = \beta \} $$

    其中 $\langle \alpha,x \rangle = \alpha_1 x_1 + \alpha_2 x_2 + \cdots + \alpha_n x_n$ 是 $\alpha$ 和 $x$ 的内积。我们记 $H^+(\alpha,\beta) = \{ x \in \mathbb{R}^n \mid \langle \alpha,x \rangle \geqslant \beta \}$ 和 $H^-(\alpha,\beta) = \{ x \in \mathbb{R}^n \mid \langle \alpha,x \rangle \leqslant \beta \}$ 分别为超平面 $H(\alpha,\beta)$ 的**半空间（half-space）**。
    
事实上我们可以将超平面的定义 $\alpha_1 x_1 + \alpha_2 x_2 + \cdots + \alpha_n x_n = \beta$ 视为用一个线性约束得到了一个 $n-1$ 维的“平面”。$\alpha$ 被称为法向量的原因是，如果我们任取 $x_1,x_2 \in H(\alpha,\beta)$，则有 $\langle \alpha,x_1 \rangle = \langle \alpha,x_2 \rangle = \beta$，因此 $\langle \alpha,x_1 \rangle - \langle \alpha,x_2 \rangle = 0$，即 $\langle \alpha,x_1 - x_2 \rangle = 0$，这说明 $\alpha$ 与 $H(\alpha,\beta)$ 上的任意向量正交。

一个超平面将一个集合和一个点分离，条件是：这个集合被包含在超平面的一个半空间中，而这个点在另一个半空间中。这一定义的形式化描述如下：

!!! 分离的定义
    令 $S \subseteq \mathbb{R}^n$ 是一个集合，$x \in \mathbb{R}^n$ 是一个向量。超平面 $H(\alpha,\beta)$ 将 $S$ 和 $x$ 分开，条件是

    1. $S \subseteq H^+(\alpha,\beta)$ 且 $x \in H^-(\alpha,\beta)$，或者
    2. $S \subseteq H^-(\alpha,\beta)$ 且 $x \in H^+(\alpha,\beta)$。

    如果 $x$ 和 $S$ 的分离是严格的，如果

    1. $S \subseteq H^+(\alpha,\beta)\backslash H(\alpha,\beta)$ 且 $x \in H^-(\alpha,\beta)\backslash H(\alpha,\beta)$，或者
    2. $S \subseteq H^-(\alpha,\beta)\backslash H(\alpha,\beta)$ 且 $x \in H^+(\alpha,\beta)\backslash H(\alpha,\beta)$。

## 仿射无关性


## 单纯形
