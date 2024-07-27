# 数学预备知识

**在开始正式的内容之前，必须要做一个推荐。关于优化的内容，非常推荐我的大佬同学，知乎用户@金鱼马的[这个知乎专栏](https://www.zhihu.com/column/c_1676006565717573634)，这里的笔记大都只是用作补充其它部分所需而写的，因此如果需要详细学习优化相关知识，快去看知乎专栏！**

本讲的主题是优化领域常用的数学预备知识，主要总结了微积分和线性代数课程中并不强调，但实际应用很丰富的内容。除此之外，还介绍了基本的数值线性代数的内容。

## 分析
有关范数的基础知识已经并入[泛函分析相关章节](../functional_analysis/metric.md)，这里主要介绍闭函数的概念并回顾多元函数微分学中应用较多的部分。

### 闭函数
对于函数 $f: \mathbf{R}^n \to \mathbf{R}$，如果对每个 $\alpha \in \mathbf{R}$，下水平集

$$ \{ x \in \text{dom }f \mid f(x) \leqslant \alpha \} $$

都是闭集，则称 $f$ 为闭函数。根据定义，如果 $f$ 连续，且 $\text{dom }f$ 为闭集，则 $f$ 为闭函数（下水平集相当于两个闭集的交集）。如果 $f$ 连续，但 $\text{dom }f$ 为开集，不难证明 $f$ 是闭函数的充要条件为 $f$ 将沿着任何收敛于 $\text{dom }f$ 的边界点的序列趋于 $\infty$。换言之，如果 $\lim\limits_{i \to \infty} x_i = x \in \partial \text{dom }f$，则 $\lim\limits_{i \to \infty} f(x_i) = \infty$。

!!! question "闭函数的例子"
    - $f: \mathbb{R}^+ \to \mathbb{R}$，$f(x) = x\text{ ln } x$ 不是闭函数；
    - $f: \mathbb{R}^+ \cup \{0\} \to \mathbb{R}$，$f(x) = \begin{cases} x\text{ ln } x & x > 0 \\ 0 & x = 0 \end{cases}$ 是闭函数；
    - $f: \mathbb{R}^+ \to \mathbb{R}$，$f(x) = -\text{ ln } x$ 是闭函数。

### 导数
#### 向量值函数的导数
本节我们回顾多元微积分中不常见的向量值函数的常用概念和结论。首先是导数的概念：
!!! note "导数"
    设 $f: \mathbf{R}^n \to \mathbf{R}^m$，$x \in \text{int dom }f$，则 $f$ 在 $x$ 处可导，当且仅当存在一个矩阵 $Df(x) \in \mathbf{R}^{m \times n}$，使得

    $$ \lim_{h \to 0} \frac{\| f(x + h) - f(x) - Df(x)h \|}{\| h \|} = 0 $$

    此处 $\mathbf{R}^n$ 和 $\mathbf{R}^m$ 上的范数都取欧几里得范数。$Df(x)$ 称为 $f$ 在 $x$ 处的**导数**，也称为 **Jacobian 矩阵**。

1. 可以证明，在可导的情况下，这样的矩阵 $A$ 是唯一的（具体证明可以参考张筑生老师的《数学分析新讲》）
2. 链式法则：设 $f: \mathbf{R}^n \to \mathbf{R}^m$，$g: \mathbf{R}^m \to \mathbf{R}^p$，令 $h(x) = g(f(x))$，则 $Dh(x) = Dg(f(x))Df(x)$
3. 向量值函数 $f(x) = (f_1(x),\cdots,f_m(x))$ 在点 $x_0$ 处可微，当且仅当 $f_1,\cdots,f_m$ 在 $x_0$ 处可微，且此时有

    $$ Df(x_0) = \begin{pmatrix} \dfrac{\partial f_1}{\partial x_1}(x_0) & \cdots & \dfrac{\partial f_1}{\partial x_n}(x_0) \\ \vdots & \ddots & \vdots \\ \dfrac{\partial f_m}{\partial x_1}(x_0) & \cdots & \dfrac{\partial f_m}{\partial x_n}(x_0) \end{pmatrix} $$

    这一矩阵就是 **Jacobian 矩阵**的具体形式。

4. 设 $G \subseteq \mathbf{R}^n$ 是开集，$f: G \to \mathbf{R}^m$，$x \in G$ 在 $G$ 上可微。又设 $a, b \in G$ 满足 $[a,b] \in G$，则存在 $c \in (a,b)$ 使得

$$ \| f(b) - f(a) \| \leqslant \| Df(c) \|\| b - a \| $$

对于实值函数 $f: \mathbf{R}^n \to \mathbf{R}$，导数 $Df(x)$ 是 $1 \times n$ 矩阵，其转置我们称之为梯度：

$$\nabla f(x) = Df(x)^\mathrm{T} = (\dfrac{\partial f}{\partial x_1}(x), \ldots, \dfrac{\partial f}{\partial x_n}(x))^{\mathrm{T}}$$

#### 高阶导数
进一步地，我们可以定义高阶导数。我们讨论实值函数 $f: \mathbf{R}^n \to \mathbf{R}$ 的二阶导数，向量值函数我们拆分成多个实值函数来看即可。事实上若 $f$ 在 $x$ 处二次可微，则 $f$ 在 $x$ 处的二阶导数 $\nabla^2f(x)$ 是一个 $n \times n$ 的矩阵（或称 **Hessian 矩阵**）

$$ \nabla^2f(x) = \begin{pmatrix} \dfrac{\partial^2 f}{\partial x_1^2}(x) & \cdots & \dfrac{\partial^2 f}{\partial x_1 \partial x_n}(x) \\ \vdots & \ddots & \vdots \\ \dfrac{\partial^2 f}{\partial x_n \partial x_1}(x) & \cdots & \dfrac{\partial^2 f}{\partial x_n^2}(x) \end{pmatrix} $$

基于此我们可以得到 $f$ 在 $x$ 处的二次逼近：

$$ f(x + h) \approx f(x) + \nabla f(x)^\mathrm{T}h + \dfrac{1}{2}h^\mathrm{T}\nabla^2f(x)h $$

事实上我们只需要将这些乘法展开就可以意识到这一式与我们熟知的一元函数的泰勒展开的联系。多元函数的泰勒展开较为繁杂，用途也有限，因此我们在这里不再展开。

#### 例子
!!! question "多元函数求导例子"
    1. 二次函数 $f: \mathbb{R}^n \to \mathbb{R}$，$f(x) = \dfrac{1}{2}x^\mathrm{T}Ax + b^\mathrm{T}x + c$，其中 $A$ 是 $n$ 阶对称矩阵，$b \in \mathbb{R}^n$，$c \in \mathbb{R}$
    2. 函数 $f: S_{+ +}^n \to \mathbb{R}$，$f(X) = \text{ln }\det X$
    3. 函数 $f: \mathbb{R}^n \to \mathbb{R}$，$f(x) = \text{ln }\sum\limits_{i = 1}^m \text{exp}(a_i^\mathrm{T}x + b_i)$

!!! note "例子的解答"
    1. 标准的解法就是将表达式展开然后逐个求导，不难得到 $f$ 的梯度为 $\nabla f(x) = Ax + b$，Hessian 矩阵为 $\nabla^2f(x) = A$（常见结论，可以记忆）
    2. 令 $Z \in S_{+ +}^n$ 接近 $X$，令 $\Delta X = Z - X$ 接近于零矩阵，我们有

        $$\begin{aligned}
            \text{ln }\det Z & = \text{ln }\det (X + \Delta X) \\
            & = \text{ln }\det X + \text{ln }\det (X^{1/2}(I + X^{-1/2}\Delta X X^{-1/2})X^{1/2}) \\
            & = \text{ln }\det X + \text{ln }\det (I + X^{-1/2}\Delta X X^{-1/2}) \\
            & = \text{ln }\det X + \sum\limits_{i = 1}^n \text{ln }(1 + \lambda_i)
        \end{aligned}$$

        其中 $\lambda_i$ 是 $X^{-1/2}\Delta X X^{-1/2}$ 的特征值。因为 $\Delta X$ 接近于零矩阵，因此特征值也很小，因此 $\text{ln }(1 + \lambda_i) \approx \lambda_i$，故有

        $$\begin{aligned}
            \text{ln }\det Z & = \text{ln }\det X + \sum\limits_{i = 1}^n \lambda_i \\
            & = \text{ln }\det X + \text{tr }(X^{-1/2}\Delta X X^{-1/2}) \\
            & = \text{ln }\det X + \text{tr }(X^{-1}\Delta X) \\
            & = \text{ln }\det X + \text{tr }(X^{-1}(Z - X))
        \end{aligned}$$

        式中利用了迹 $\text{tr}(AB) = \text{tr}(BA)$ 的性质。因此 $f$ 在 $X$ 处的一次逼近是 $Z$ 的仿射函数

        $$ f(Z) \approx f(X) + \text{tr }(X^{-1}(Z - X)) $$

        由于等号右边第二项就是 $X^{-1}$ 和 $Z - X$ 的标准内积（Frobenius 内积），故 $f$ 在 $X$ 处的梯度为 $\nabla f(X) = X^{-1}$。对这一结果不应感到吃惊，因为 $\text{ln }x$ 在 $\mathbb{R}^+$ 上的导数是 $\dfrac{1}{x}$。

        二阶导数同样考虑 $Z$ 接近 $X$，且 $\Delta X = Z - X$ 接近于零矩阵，我们有

        $$\begin{aligned}
            Z^{-1} & = (X + \Delta X)^{-1} \\
            & = (X^{1/2}(I + X^{-1/2}\Delta X X^{-1/2})X^{1/2})^{-1} \\
            & = X^{-1/2}(I + X^{-1/2}\Delta X X^{-1/2})^{-1}X^{-1/2} \\
            & \approx X^{-1/2}(I - X^{-1/2}\Delta X X^{-1/2})^{-1}X^{-1/2} \\
            & = X^{-1} - X^{-1}\Delta X X^{-1}
        \end{aligned}$$

        其中我们用到了估计 $(I + A)^{-1} \approx I - A$，这一估计在 $A$ 很小的时候成立。接下来为了完成我们找到 “Hessian 矩阵”，我们需要深入理解矩阵到实值的函数的一阶导数和二阶导数究竟是什么。事实上，回顾向量到实值的函数，一次逼近为

        $$ f(x + h) \approx f(x) + \nabla f(x)^\mathrm{T}h = f(x) + \langle \nabla f(x), h \rangle $$
        
        从而一阶导数可以认为是一个映射 $df(x) \in \mathcal{L}(\mathbf{R}^n, \mathbf{R})$，满足 $(df(x))(h) = \langle \nabla f(x), h \rangle$。进一步地，二阶导数是一个矩阵，事实上也就是一个映射 $d^2f(x) \in \mathcal{L}(\mathbf{R}^n, \mathcal{L}(\mathbf{R}^n, \mathbf{R}))$，满足 $(d^2f(x))(h_1)(h_2) = \langle \nabla^2 f(x)h_1, h_2 \rangle$。接下来这些内容可以推广到矩阵到实值的函数，读者可以参考[这个回答](https://math.stackexchange.com/questions/247043/second-order-approximation-of-log-det-x)，从而可以得出最终的结果。
            
    3. 这边建议亲锻炼一下复合函数求导能力，答案是 $\nabla f(x) = \dfrac{1}{\textbf{1}^\mathrm{T}z}A^\mathrm{T}z$，其中 $z_i = \text{exp}(a_i^\mathrm{T}x + b_i)$，进一步可以得到 $\nabla^2 f(x) = A^\mathrm{T} (\dfrac{1}{\textbf{1}^\mathrm{T}z}\text{diag}(z) - \dfrac{1}{(\textbf{1}^\mathrm{T}z)^2}zz^\mathrm{T})A$。

## 线性代数
### 特征值分解
我们记全体 $n$ 阶实对称矩阵构成的集合为 $S^n$，半正定实对称矩阵构成的集合为 $S_+^n$，正定实对称矩阵构成的集合为 $S_{+ +}^n$。对于任意的 $A \in S^n$，根据线性代数的知识可知 $A$ 可正交对角化，则 $A$ 可分解为

$$ A = Q \Lambda Q^\mathrm{T} $$

其中 $Q$ 为 $n$ 阶正交矩阵，满足 $Q^\mathrm{T}Q = E$，$\Lambda$ 为对角矩阵，记为 $\Lambda = \text{diag}(\lambda_1, \ldots, \lambda_n)$，其中 $\lambda_i$ 为 $A$ 的特征值，$Q$ 的列向量为 $A$ 的特征向量。上述分解被称为 $A$ 的**特征值分解**或**谱分解**。

我们对特征值进行排序使其满足 $\lambda_1 \geqslant \lambda_2 \geqslant \ldots \geqslant \lambda_n$，用符号 $\lambda_i(A)$ 指示 $A$ 的第 $i$ 大的特征值。通常将最大特征值称为 $A$ 的**谱半径**，记为 $\rho(A)$，写为 $\lambda_1(A) = \lambda_{\max}(A) = \rho(A)$，最小特征值写为 $\lambda_n(A) = \lambda_{\min}(A)$。

#### 对称平方根
令 $A \in S_{+}^n$ 的特征值分解为 $A = Q \text{diag}(\lambda_1, \ldots, \lambda_n)Q^\mathrm{T}$，则 $A$ 的**对称平方根**定义为

$$ A^{1/2} = Q \text{diag}(\sqrt{\lambda_1}, \ldots, \sqrt{\lambda_n})Q^\mathrm{T} $$

事实上，$A^{1/2}$ 是唯一的对称半正定矩阵满足 $(A^{1/2})^2 = A$：

!!! note "平方根的的唯一性证明"
    假设 $B_1$ 和 $B_2$ 都是 $A$ 的对称平方根，即 $B_1^2 = B_2^2 = A$，则 $\sqrt{\lambda_1}, \ldots, \sqrt{\lambda_n}$ 是 $B_1$ 和 $B_2$ 共同的的特征值。记 $\Lambda = \text{diag}(\lambda_1, \ldots, \lambda_n),\sqrt{\Lambda} = \text{diag}(\sqrt{\lambda_1}, \ldots, \sqrt{\lambda_n})$，因此存在正交矩阵 $Q_1$ 和 $Q_2$ 使得 $B_1 = Q_1 \sqrt{\Lambda} Q_1^\mathrm{T}$ 和 $B_2 = Q_2 \sqrt{\Lambda} Q_2^\mathrm{T}$。

    根据 $B_1^2 = B_2^2$，我们有 $Q_1 \Lambda Q_1^\mathrm{T} = Q_2 \Lambda Q_2^\mathrm{T}$，故 $Q_2^\mathrm{T}Q_1 \Lambda = \Lambda Q_2^\mathrm{T}Q_1$，故 $Q_2^\mathrm{T}Q_1$ 和 $\Lambda$ 可交换。事实上我们可以将 $\Lambda$ 重写为 $\Lambda = \text{diag}(\lambda_1E_{r_1}, \ldots, \lambda_kE_{r_k})$，其中 $r_1 + \ldots + r_k = n$，$E_{r_i}$ 为 $r_i$ 阶单位矩阵，这表明 $\lambda_i$ 为 $r_i$ 重特征值。因此根据可交换的性质，我们有 $Q_2^\mathrm{T}Q_1 = \text{diag}(C_1, \ldots, C_k)$，其中 $C_i$ 为 $r_i$ 阶方阵。

    因此，$Q_2^\mathrm{T}Q_1$ 和 $\sqrt{\Lambda}$ 也可交换，故 $Q_2^\mathrm{T}Q_1 \sqrt{\Lambda} = \sqrt{\Lambda} Q_2^\mathrm{T}Q_1$，即 $Q_1 \sqrt{\Lambda} Q_1^\mathrm{T} = Q_2 \sqrt{\Lambda} Q_2^\mathrm{T}$，故 $B_1 = B_2$。

#### 特征值相关的定理
本节我们介绍一系列与特征值相关的重要结果。在介绍这些结果之前，我们首先复习几个名词。**正交矩阵**是指在实数域上满足 $Q^\mathrm{T}Q = QQ^\mathrm{T} = E$ 的矩阵，**酉矩阵（unitary matrix）**是指在复数域上满足 $U^\mathrm{H}U = UU^\mathrm{H} = I$ 的矩阵，其中 $U^\mathrm{H}$ 为 $U$ 的共轭转置。一个矩阵 $A$ 称为**正规矩阵（normal matrix）**，如果 $AA^\mathrm{H} = A^\mathrm{H}A$，其中 $A^\mathrm{H}$ 为 $A$ 的共轭转置。称 $A$ 为**自伴矩阵（self-adjoint matrix）**（或**Hermite 矩阵**），如果 $A = A^\mathrm{H}$。

!!! note "Rayleigh-Ritz 定理"
    设 $A$ 是一个 $n$ 阶 Hermite 矩阵，则有
    
    \begin{gather*}
        \lambda_{\min}x^\mathrm{H}x \leqslant x^\mathrm{H}Ax \leqslant \lambda_{\max}x^\mathrm{H}x, \quad \forall x \in \mathbf{C}^n, \\
        \lambda_{\max} = \max\limits_{x \neq 0} \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x} = \max\limits_{\| x \| = 1} x^\mathrm{H}Ax, \\
        \lambda_{\min} = \min\limits_{x \neq 0} \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x} = \min\limits_{\| x \| = 1} x^\mathrm{H}Ax.
    \end{gather*}

    注意复数域上 $\| x \| = \sqrt{x^\mathrm{H}x}$，上述结论限制在实数域上只需将共轭转置换为转置即可。

这一定理在应用中非常常见，一方面是放缩时常用，另一方面回顾[泛函分析相关章节](../functional_analysis/metric.md)中二次范数的定义，这样的形式也是非常常见的，$\dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x}$ 也被称为 Rayleigh 商。

!!! note "Rayleigh-Ritz 定理的证明"
    由于 $A$ 是 Hermite 矩阵，故可以取一个酉矩阵 $U$ 使得 $A = U \Lambda U^\mathrm{H}$，其中 $\Lambda = \text{diag}(\lambda_1, \ldots, \lambda_n)$。因此，我们有 $x^\mathrm{H}Ax = x^\mathrm{H}U \Lambda U^\mathrm{H}x = (U^\mathrm{H}x)^\mathrm{H} \Lambda (U^\mathrm{H}x) = \sum\limits_{i = 1}^n \lambda_i |(U^\mathrm{H}x)_i|^2$。根据 $|(U^\mathrm{H}x)_i|^2 \geqslant 0$ 可得

    $$ \lambda_{\min} \sum\limits_{i = 1}^n |(U^\mathrm{H}x)_i|^2 \leqslant x^\mathrm{H}Ax \leqslant \lambda_{\max} \sum\limits_{i = 1}^n |(U^\mathrm{H}x)_i|^2 $$

    由于 $U$ 是酉矩阵，故 $\sum\limits_{i = 1}^n |(U^\mathrm{H}x)_i|^2 = \sum\limits_{i = 1}^n |x_i|^2 = x^\mathrm{H}x$，故有

    $$ \lambda_{\min}x^\mathrm{H}x \leqslant x^\mathrm{H}Ax \leqslant \lambda_{\max}x^\mathrm{H}x $$

    因此如果 $x \neq 0$，则有 $\lambda_{\min} \leqslant \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x} \leqslant \lambda_{\max}$。事实上，当 $x$ 是特征值 $\lambda_{\max}$ 对应的特征向量时，有 $x^\mathrm{H}Ax = \lambda_{\max}x^\mathrm{H}x$，故等号可以取得，$\lambda_{\max} = \max\limits_{x \neq 0} \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x}$。同理，当 $x$ 是特征值 $\lambda_{\min}$ 对应的特征向量时，有 $x^\mathrm{H}Ax = \lambda_{\min}x^\mathrm{H}x$，故 $\lambda_{\min} = \min\limits_{x \neq 0} \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x}$。

    进一步地，$\dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x} = \left( \dfrac{x}{\sqrt{x^\mathrm{H}x}} \right)^\mathrm{H}A \left( \dfrac{x}{\sqrt{x^\mathrm{H}x}} \right)$，而 $\left( \dfrac{x}{\sqrt{x^\mathrm{H}x}} \right)^\mathrm{H}\left( \dfrac{x}{\sqrt{x^\mathrm{H}x}} \right) = 1$，故 $\lambda_{\max} = \max\limits_{\| x \| = 1} x^\mathrm{H}Ax$，$\lambda_{\min} = \min\limits_{\| x \| = 1} x^\mathrm{H}Ax$。

!!! note "Courant-Fischer 极小极大定理"
    设 $A$ 是一个 $n$ 阶 Hermite 矩阵，其特征值为 $\lambda_1 \geqslant \lambda_2 \geqslant \ldots \geqslant \lambda_n$，则对每一个 $k = 1, \ldots, n$，有

    $$ \lambda_k = \max\limits_{\text{dim }S = k} \min\limits_{x \in S, x \neq 0} \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x} = \min\limits_{\text{dim }S = n - k + 1} \max\limits_{x \in S, x \neq 0} \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x} $$

同 Rayleigh-Ritz 定理，$x \neq 0$ 也可以改写为 $\| x \| = 1$，分式中的 $x^\mathrm{H}x$ 从而可以略去，即证明

$$ \lambda_k = \max\limits_{\text{dim }S = k} \min\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax = \min\limits_{\text{dim }S = n - k + 1} \max\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax $$

!!! note "Courant-Fischer 极小极大定理的证明"
    由于 $A$ 是 Hermite 矩阵，故它有一组标准正交特征向量 $u_1, \ldots, u_n$，对应的特征值为 $\lambda_1, \ldots, \lambda_n$。考虑一个 $k$ 维子空间 $U_1$ 以及 $U_2 = \text{span}(u_k,\ldots,u_n)$，根据线性空间维数公式可知，$U_1 \cap U_2$ 非空，因此必然存在 $x \in U_1 \cap U_2$。因为 $x \in U_2$，故可以表达为 $x = \sum\limits_{i = k}^n \alpha_i u_i$，当 $\| x \| = 1$ 时，我们有 $\sum\limits_{i = k}^n |\alpha_i|^2 = 1$，故
    
    $$x^\mathrm{H}Ax = \sum\limits_{i = k}^n |\alpha_i|^2 u_i^\mathrm{H}Au_i = \sum\limits_{i = k}^n \lambda_i |\alpha_i|^2 \leqslant \lambda_k$$

    最后的不等号来源于我们的特征值是递减排列的。故 $\min\limits_{x \in U_1, \| x \| = 1} x^\mathrm{H}Ax \leqslant \lambda_k$，而我们知道对于任意 $k$ 维的 $U_1$，我们总是能取到 $x$ 使得$\min\limits_{x \in U_1, \| x \| = 1} x^\mathrm{H}Ax \leqslant \lambda_k$，因此有

    $$ \lambda_k \geqslant \max\limits_{\text{dim }S = k} \min\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax $$

    为了证明另一个方向的不等式，事实上我们只需要取到一个最差情况也很好的 $S$，那我们就可以取 $S = \text{span}(u_1,\cdots,u_k)$，此时对于任意的 $x \in S$ 都可以表达为 $x = \sum\limits_{i = 1}^k \alpha_i u_i$，且 $\| x \| = 1$，故

    $$ x^\mathrm{H}Ax = \sum\limits_{i = 1}^k |\alpha_i|^2 u_i^\mathrm{H}Au_i = \sum\limits_{i = 1}^k \lambda_i |\alpha_i|^2 \geqslant \lambda_k $$

    故此时 $\min\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax \geqslant \lambda_k$，因此 $\lambda_k \leqslant \min\limits_{\text{dim }S = k} \max\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax$。综上有 $\lambda_k = \max\limits_{\text{dim }S = k} \min\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax$。另一个等号通过类似的方法也可以证明，这里略去。

接下来我们应用前面证明的结果得到一个重要的定理：
!!! note "Weyl 定理"
    设 $A,B$ 是 $n$ 阶 Hermite 矩阵，特征值 $\lambda_j(A),\lambda_j(B),\lambda_j(A + B)$ 均按降序排列，则对于任意的 $k = 1, \ldots, n$，有

    $$ \lambda_k(A) + \lambda_n(B) \leqslant \lambda_k(A + B) \leqslant \lambda_k(A) + \lambda_1(B) $$

有一个误区需要提醒，即 $A + B$ 的特征值不一定是 $A$ 的特征值加上 $B$ 的特征值，因为两个矩阵的特征向量不一定一致。因此这一定理给出了两个 Hermite 矩阵之和的特征值的一个上下界。

!!! note "Weyl 定理的证明"
    对于 $x \neq 0$，由 Rayleigh-Ritz 定理可知对于任意的 $\| x \| = 1$ 有 $\lambda_n(B) \leqslant x^\mathrm{H}Bx \leqslant \lambda_1(B)$，从而结合 Rayleigh-Ritz 定理以及 Courant-Fischer 极小极大定理可得

    $$\begin{aligned}
        \lambda_k(A+B) & = \max\limits_{\text{dim }S = k} \min\limits_{x \in S, \| x \| = 1} x^\mathrm{H}(A+B)x \\
        & = \max\limits_{\text{dim }S = k} \min\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax + x^\mathrm{H}Bx \\
        & \geqslant \max\limits_{\text{dim }S = k} \min\limits_{x \in S, \| x \| = 1} x^\mathrm{H}Ax + \lambda_n(B) \\
        & = \lambda_k(A) + \lambda_n(B)
    \end{aligned}$$

    另一个不等式的证明完全类似，这里略去。

下面这一定理也是前面的结果的重要应用：
!!! note "Cauchy 交错定理, Cauchy’s Interlacing Theorem"
    设 $\hat{A}$ 是一个 $(n+1) \times (n+1)$ 的 Hermite 矩阵, 其特征值 $\hat{\lambda}_j$ 按降序排列。设 $A$ 是 $\hat{A}$ 的一个 $n$ 阶主子阵，其特征值 $\lambda_j$ 按降序排列，则有

    $$ \hat{\lambda}_1 \geqslant \lambda_1 \geqslant \hat{\lambda}_2 \geqslant \lambda_2 \geqslant \ldots \geqslant \hat{\lambda}_n \geqslant \lambda_n \geqslant \hat{\lambda}_{n+1} $$

!!! note "Cauchy 交错定理的证明"
    不失一般性地，假设 $\hat{A} = \pmatrix{A & y \\ y^\mathrm{H} & a}$。我们只需证明，对任意的 $1 \leqslant k \leqslant n$，有 $\hat{\lambda}_k \geqslant \lambda_k \geqslant \hat{\lambda}_{k+1}$ 即可。设 $\hat{x} = (x^\mathrm{T}\ c)^{\mathrm{T}} \in \mathbb{C}^{n+1}$，其中 $x \in \mathbb{C}^n$，$c \in \mathbb{C}$。令 $U$ 表示最后一维为 $0$ 的向量构成的线性空间，根据 Courant-Fischer 极小极大定理可得

    $$\begin{aligned}
        \hat{\lambda}_k & = \max\limits_{\text{dim }S = k} \min\limits_{\hat{x} \in S, \hat{x} \neq 0} \dfrac{\hat{x}^\mathrm{H}\hat{A}\hat{x}}{\hat{x}^\mathrm{H}\hat{x}} \\
        & \geqslant \max\limits_{\text{dim }S = k, S = U} \min\limits_{\hat{x} \in S, \hat{x} \neq 0} \dfrac{\hat{x}^\mathrm{H}\hat{A}\hat{x}}{\hat{x}^\mathrm{H}\hat{x}} \\
        & = \max\limits_{\text{dim }S = k} \min\limits_{x \in S, x \neq 0} \dfrac{x^\mathrm{H}Ax}{x^\mathrm{H}x} = \lambda_k
    \end{aligned}$$

    第二行的大于等于号来源于我们将可取的 $S$ 限制在最后一维为 $0$ 的向量构成的线性空间，第三行的等号是因为将最后一维为 $0$ 的 $n+1$ 元向量构成的线性空间的所有向量的最后一个元素删去后就是全体符合条件的长度为 $n$ 的向量，并且后续表达式的值也完全一致。另一方向的不等式利用 Courant-Fischer 极小极大定理的 $\min\max$ 式证明即可。

反复应用 Cauchy 交错定理可以迅速得到如下推论：
!!! note "Cauchy 交错定理的推论"
    设 $A$ 是一个 $n$ 阶 Hermite 矩阵，$B$ 是 $A$ 的任意一个 $r$ 阶主子阵，则对任意的 $1 \leqslant k \leqslant r$，有

    $$ \lambda_k(A) \geqslant \lambda_k(B) \geqslant \lambda_{n-r+k}(A) $$

#### 广义特征值分解
!!! note "广义特征值"
    设 $A,B$ 是 $n$ 阶 Hermite 矩阵，则 $(A,B)$ 的**广义特征值**定义为多项式 $\det (sB-A)$ 的根。

通常我们感兴趣 $B$ 是正定矩阵的情况，此时我们可以将广义特征值问题转化为标准特征值问题。则不难计算得到 $(A,B)$ 的广义特征值等价于 $B^{-1/2}AB^{-1/2}$ 的特征值。不难发现 $B^{-1/2}AB^{-1/2}$ 是一个 Hermite 矩阵，故我们可以写出其特征值分解 $B^{-1/2}AB^{-1/2} = Q \Lambda Q^\mathrm{T}$，其中 $\Lambda = \text{diag}(\lambda_1, \ldots, \lambda_n)$，$Q$ 是正交矩阵。现在我们取 $V = B^{1/2}Q$（这是一个可逆矩阵），则有

$$ A = V \Lambda V^\mathrm{T}, \quad B = VV^\mathrm{T} $$

上述分解被称为 $(A,B)$ 的**广义特征值分解**。

### 奇异值分解
#### 奇异值分解
设 $A \in \mathbb{C}^{m \times n}$，则 $A$ 的**奇异值分解（singular value decomposition, SVD）**为

$$ A = U \Sigma V^\mathrm{H} $$

其中 $U \in \mathbb{C}^{m \times m}$ 和 $V \in \mathbb{C}^{n \times n}$ 是酉矩阵，$\Sigma \in \mathbb{R}^{m \times n}$ 是一个对角矩阵，对角线上的元素称为 $A$ 的**奇异值**，记为 $\sigma_1 \geqslant \sigma_2 \geqslant \ldots \geqslant \sigma_p \geqslant 0$，其中 $p = \min(m,n)$。$U$ 的列向量称为 $A$ 的**左奇异向量**，$V$ 的列向量称为 $A$ 的**右奇异向量**。

事实上奇异值分解可以视为内积空间上的相抵标准形分解，上式的推导可见一般的线性代数教材。事实上，如果我们将 $U$ 和 $V$ 按奇异向量分块，可以得到 $A = (u_1, \ldots, u_m) \Sigma (v_1, \ldots, v_n)^\mathrm{H}$，类似于二次型的展开方式可以得到

$$ A = \sum\limits_{i = 1}^p \sigma_i u_i v_i^\mathrm{H} $$

其中 $u_i$ 和 $v_i$ 分别是 $U$ 和 $V$ 的第 $i$ 列向量，即左右奇异向量。

$A$ 的奇异值分解和 $A^\mathrm{H}A$ 的特征值分解之间有着密切的联系，事实上我们不难得到

$$ A^\mathrm{H}A = V \Sigma^\mathrm{H} U^\mathrm{H} U \Sigma V^\mathrm{H} = V \pmatrix{\sigma_1^2 & & \\ & \ddots & \\ & & \sigma_p^2} V^\mathrm{H} $$

即 $A^\mathrm{H}A$ 的特征值为 $\sigma_1^2, \ldots, \sigma_p^2$，特征向量为 $V$ 的列向量，故我们可以很轻松地利用这一结论求出矩阵的奇异值，例如对称矩阵的奇异值就是其特征值的绝对值。进一步地，根据 Rayleigh-Ritz 定理，我们有

$$ \sigma_{\max} = \max\limits_{x \neq 0} \sqrt{\dfrac{x^\mathrm{H}A^\mathrm{H}Ax}{x^\mathrm{H}x}} = \max\limits_{x \neq 0} \dfrac{\| Ax \|_2}{\| x \|_2} = \| A \|_2 $$

进一步地，类似于 Rayleigh-Ritz 定理的证明，我们可以得到当 $x,y \neq 0$ 时，

$$ \dfrac{x^\mathrm{H}Ay}{\| x \|_2 \| y \|_2} = \dfrac{(U^\mathrm{H}x)^\mathrm{H} \Sigma (V^\mathrm{H}y)}{\| U^\mathrm{H}x \|_2 \| V^\mathrm{H}y \|_2} = \dfrac{z^\mathrm{H} \Sigma w}{\| z \|_2 \| w \|_2} = \dfrac{\sum\limits_{i = 1}^p \sigma_i z_i w_i}{\| z \|_2 \| w \|_2} $$

事实上取 $z^* = z / \| z \|_2$ 和 $w^* = w / \| w \|_2$，不难得到

$$ \max\limits_{x,y \neq 0} \dfrac{x^\mathrm{H}Ay}{\| x \|_2 \| y \|_2} = \max\limits_{\|z^*\|_2 = \|w^*\|_2 = 1} \sum\limits_{i = 1}^p \sigma_i z_i w_i \leqslant \sigma_{\max} (z^*)^\mathrm{H} w^* \leqslant \sigma_{\max} \| z^* \|_2 \| w^* \|_2 = \sigma_{\max} $$

其中用到了 Cauchy-Schwarz 不等式。不难看出这些不等号的取等条件，因此我们可以得到 $\sigma_{\max} = \max\limits_{x,y \neq 0} \dfrac{x^\mathrm{H}Ay}{\| x \|_2 \| y \|_2}$。

#### 条件数

!!! note "条件数"
    设 $A$ 是一个 $n$ 阶方阵，则 $A$ 的**条件数**定义为 $\kappa(A) = \sigma_{\max} / \sigma_{\min}$。

条件数是一个矩阵的数值稳定性的一个重要指标，之后的讨论中可能会使用。

#### 伪逆


### Schur 补


## 数值线性代数
