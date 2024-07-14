# 线性规划对偶

注：本节部分内容参考[贺老师的知乎专栏](https://zhuanlan.zhihu.com/p/681165783)。

## 引入：影子价格

考虑一个线性规划问题（我们将其记作问题 $(P)$）：

$$(P) \qquad \begin{align}
    \max\;& 4x_1 + 3x_2 \\ \text{s.t. }\; & 2x_1 + 3x_2 \leqslant 24 \\ & 5x_1 + 2x_2 \leqslant 26 \\ & x_1,x_2 \geqslant 0
\end{align}$$

我们可以把这个问题看作一个生产模型：一份产品 A 可以获利 4 单位价格，生产一份需要 2 单位原料 C 和 5 单位原料 D；一份产品 B 可以获利 3 单位价格，生产一份需要 3 单位原料 C 和 2 单位原料 D。现有 24 单位原料 C，26 单位原料 D，问如何分配生产方式才能让获利最大。

但假如现在我们不生产产品，而是要把原料都卖掉。设 1 单位原料 C 的价格为 $y_1$，1 单位原料 D 的价格为 $y_2$，每种原料制定怎样的价格才合理呢？

一方面，产品 A 和 B 的价格反映了两种原料的使用价值，如果我们希望出售原料，那么不应该让原料的价格低于产出的产品价格——否则自己使用这些原料进行生产能获得更大的利润。于是，可以获得约束：

$$\begin{align} 2y_1 + 5y_2 &\geqslant 4 \\ 3y_1 + 2y_2 &\geqslant 3 \end{align}$$

对卖方来说，只有满足该约束的报价才不亏。而站在买方的角度，自然希望购得这批原料的钱越少越好。由于共有 24 单位原料 C，26 单位原料 D，那么买方一共应该花费 $24y_1 + 26y_2$。合起来就得到了下面的线性规划问题，我们称之为问题 $(D)$：

$$(D) \qquad \begin{align*} \min\; & 24y_1 + 26y_2 \\ \text{s.t. }\; & 2y_1 + 5y_2 \geqslant 4 \\ & 3y_1 + 2y_2 \geqslant 3 \\ & y_1,y_2 \geqslant 0
\end{align*}$$

问题 $(D)$ 就是问题 $(P)$ 的对偶问题。这个例子在经济学中十分经典。求解 $(D)$ 得到的最优解 $y_1$ 和 $y_2$ 被称作**影子价格**（shadow price），它代表了这些原材料的估价，也是在最优经济结构中，在资源得到最优配置前提下资源的边际使用价值。