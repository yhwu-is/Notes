# 度量空间

## 度量空间

### 度量空间的定义
!!! definition "度量空间"
    一个**度量空间（metric space）**是一个集合 $X$，并有度量（距离函数）$d:X\times X\to \mathbb{R}$，使得对于任意 $x, y, z \in X$，满足以下性质：
   
    1. 正定性：$d(x,y) \geqslant 0$，且 $d(x,y) = 0$ 当且仅当 $x = y$；
    2. 对称性：$d(x,y) = d(y,x)$；
    3. 三角不等式：$d(x,y) \leqslant d(x,z) + d(z,y)$。

度量空间的定义是非常自然的，因为它提取了欧式空间中的距离概念的基本性质：距离大于等于 $0$，两点距离的对称性以及三角不等式，从而抽象为一个更一般的概念。

### 度量空间的例子

!!! question "$l_p$-空间"
    令 $p \geqslant 1$，$l_p$-空间中的每个元素是一个数列 $x = (x_1, x_2, \ldots)$，满足 $\sum\limits_{i=1}^\infty |x_i|^p < \infty$。定义 $l_p$-空间上的度量为：

    $$ d(x, y) = \left( \sum\limits_{i=1}^\infty |x_i - y_i|^p \right)^{1/p} $$

    证明 $l_p$-空间是一个度量空间。

在给出证明之前，我们先说明这一度量空间的重要性。事实上，当 $p = 2$ 时，这一空间称为希尔伯特序列空间 $l_2$，这一空间时希尔伯特于 1912 年引入并加以研究的，当时主要是根据积分方程的研究需要提出的，现在看来是所谓希尔伯特空间的最早的例子（希尔伯特空间之后会详细研究）。下面我们开始证明：

!!! note "$l_p$-空间是度量空间的证明"
    正定性和对称性显然，接下来我们分为如下四步证明三角不等式：

    1. 回忆 Jensen 不等式：对于凸函数 $f$，有 $f(\theta a + (1-\theta) b) \leqslant \theta f(a) + (1-\theta) f(b)$，其中 $a, b \in \mathbb{R}$ 且 $0 \leqslant \theta \leqslant 1$，凹函数将不等号反向即可。

    2. 证明 Hölder 不等式：对于任意 $p, q > 1$ 且 $\dfrac{1}{p} + \dfrac{1}{q} = 1$，有

        $$ \sum\limits_{i=1}^\infty |x_i y_i| \leqslant \left( \sum\limits_{i=1}^\infty |x_i|^p \right)^{1/p} \left( \sum\limits_{i=1}^\infty |y_i|^q \right)^{1/q} $$

        根据 $\ln$ 函数的凹性以及 Jensen 不等式，不难得到 $a^\theta b^{1-\theta} \leqslant \theta a + (1-\theta) b$，其中 $a, b \geqslant 0$ 且 $0 \leqslant \theta \leqslant 1$。取

        $$ a = \dfrac{|x_i|^p}{\sum\limits_{j=1}^\infty |x_j|^p}, \quad b = \dfrac{|y_i|^q}{\sum\limits_{j=1}^\infty |y_j|^q}, \quad \theta = \dfrac{1}{p} $$

        即可得到

        $$ \left( \dfrac{|x_i|^p}{\sum\limits_{j=1}^\infty |x_j|^p} \right)^{1/p} \left( \dfrac{|y_i|^q}{\sum\limits_{j=1}^\infty |y_j|^q} \right)^{1/q} \leqslant \dfrac{|x_i|^p}{p \sum\limits_{j=1}^\infty |x_j|^p} + \dfrac{|y_i|^p}{q \sum\limits_{j=1}^\infty |y_j|^q} $$

        根据级数收敛性，两边对 $i$ 求和即可得到 Hölder 不等式。事实上，当 $p = q = 2$ 时，Hölder 不等式即为著名的 Cauchy-Schwarz 不等式。可以验证，Hölder 不等式的等号成立（通过上面的推导，实际上就是 Jensen 不等式等号成立，故 $a = b$）当且仅当至少一个数列为 $0$ 数列或 $|x_i|^p = c |y_i|^q$，其中 $c > 0$，$i = 1, 2, \ldots$。

    3. 证明 Minkowski 不等式：对于任意 $p \geqslant 1$，有

        $$ \left( \sum\limits_{i=1}^\infty |x_i + y_i|^p \right)^{1/p} \leqslant \left( \sum\limits_{i=1}^\infty |x_i|^p \right)^{1/p} + \left( \sum\limits_{i=1}^\infty |y_i|^p \right)^{1/p} $$

        当 $p = 1$ 时，根据绝对值的三角不等式可知 Minkowski 不等式成立。当 $p > 1$ 时，为简化记号，记 $z_i = x_i + y_i$，则根据绝对值的三角不等式有
        
        $$|z_i|^p = |x_i + y_i||z_i|^{p-1} \leqslant |x_i||z_i|^{p-1} + |y_i||z_i|^{p-1}$$
        
        两边对 $i$ 从 $1$ 到某个固定的 $n$ 求和有

        $$\sum\limits_{i=1}^n |z_i|^p \leqslant \sum\limits_{i=1}^n |x_i||z_i|^{p-1} + \sum\limits_{i=1}^n |y_i||z_i|^{p-1}$$

        对于上式右端第一个求和，根据 Hölder 不等式有

        $$\sum\limits_{i=1}^n |x_i||z_i|^{p-1} \leqslant \left( \sum\limits_{i=1}^n |x_i|^p \right)^{1/p} \left( \sum\limits_{i=1}^n |z_i|^{(p-1)q} \right)^{1/q}$$

        因为 $\dfrac{1}{p} + \dfrac{1}{q} = 1$，所以 $(p-1)q = p$，因此上式右端第一个求和满足

        $$\sum\limits_{i=1}^n |x_i||z_i|^{p-1} \leqslant \left( \sum\limits_{i=1}^n |x_i|^p \right)^{1/p} \left( \sum\limits_{i=1}^n |z_i|^p \right)^{1/q}$$

        同理，对于上式右端第二个求和，有

        $$\sum\limits_{i=1}^n |y_i||z_i|^{p-1} \leqslant \left( \sum\limits_{i=1}^n |y_i|^p \right)^{1/p} \left( \sum\limits_{i=1}^n |z_i|^p \right)^{1/q}$$

        将上述两式代入原式可得 $n < +\infty$ 时的 Minkowski 不等式。令 $n \to \infty$，不等式右端极限存在，因此根据正项级数性质可知左端极限也存在，由此即可得到 Minkowski 不等式。
        

    4. 证明三角不等式

        $$\begin{aligned}
            d(x, y) &= \left( \sum\limits_{i=1}^\infty |x_i - y_i|^p \right)^{1/p} \\
            &= \left( \sum\limits_{i=1}^\infty |x_i - z_i + z_i - y_i|^p \right)^{1/p} \\
            &\leqslant \left( \sum\limits_{i=1}^\infty |x_i - z_i|^p \right)^{1/p} + \left( \sum\limits_{i=1}^\infty |z_i - y_i|^p \right)^{1/p} \\
            &= d(x, z) + d(z, y)
        \end{aligned}$$

事实上上面的证明对于有限维空间 $\mathbb{R}^n$ 也是成立的，即对空间中元素不是数列而是 $n$ 元向量的情况也是成立的。需要注意的是，证明过程中得到的 Hölder 不等式和 Minkowski 不等式是非常重要的不等式，它们有广泛的应用。