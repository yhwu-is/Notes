# 贝叶斯执行

## 基本定义

在本节，我们研究贝叶斯纳什均衡中的执行问题。我们首先回忆贝叶斯纳什均衡概念，即在事中阶段后验概率下所有参与人都不愿意偏离均衡策略组合：

!!! note "定义 1：贝叶斯纳什均衡"
    策略组合 $s^*(\cdot) = (s_1^*(\cdot), \ldots, s_I^*(\cdot))$ 是机制 $F = (S_1, \ldots, S_I, g(\cdot))$ 的一个贝叶斯纳什均衡，如果对于所有 $i$ 和所有 $\theta_i \in \Theta_i$，我们有

    $$ E_{\theta_{-i}}[u_i(g(s_i^*(\theta_i), s_{-i}^*(\theta_{-i})), \theta_i) \mid \theta_i] \geqslant E_{\theta_{-i}}[u_i(g(s_i', s_{-i}(\theta_{-i})), \theta_i) \mid \theta_i] $$

    对于所有 $s_i' \in S_i$ 成立。

对应的，我们有社会选择函数在贝叶斯纳什均衡下的可执行的概念，这里不再赘述。与上一讲占优策略中的执行一样，我们可以利用显示原理得到一个社会选择函数是贝叶斯可执行的当且仅当它在下面定义的意义上如实可执行：

!!! note "定义 2：贝叶斯激励相容"
    社会选择函数 $f(\cdot)$ 在**贝叶斯纳什均衡中如实可执行（truthfully implementable in Bayesian Nash equilibrium）**或是**贝叶斯激励相容（Bayesian incentive compatible）**的，如果 $s_i^*(\theta) = \theta_i$ 对于所有 $\theta_i \in \Theta_i$ 和 $i = 1, \cdots, I$ 是直接显示机制 $\Gamma = (\Theta_1, \cdots, \Theta_I, f(\cdot))$ 的一个贝叶斯纳什均衡，也就是说，如果对于所有 $i = 1, \ldots, I$ 和所有 $\theta_i \in \Theta_i$，成立

    $$ E_{\theta_{-i}}[u_i(f(\theta_i,\theta_{-i}), \theta_i) \mid \theta_i] \geqslant E_{\theta_{-i}}[u_i(f(\theta_i', \theta_{-i}), \theta_i) \mid \theta_i] \tag{1} \label{eq1} $$

    对于所有 $\theta_i' \in \Theta_i$ 成立。

于是，根据显示原理表明，在寻找可执行的社会选择函数集（现在为在贝叶斯纳什均衡中执行）时，我们只需要找到那些如实可执行的函数即可，即满足 $\eqref{eq1}$ 的函数即可。

我们可以立即注意到，贝叶斯执行概念严格弱于占优策略执行概念。由于任何占优策略均衡必然是个贝叶斯纳什均衡，任何可在占优策略中执行的社会选择函数，在贝叶斯纳什均衡中必定是可执行的。因此，我们自然希望与占优策略执行相比，贝叶斯纳什均衡能执行范围更大的社会选择函数。当然，缺点是，与占优策略执行相比，我们对贝叶斯纳什均衡执行的信心不是那么足。在本节余下内容中，我们首先举例说明在贝叶斯纳什执行情形下我们的确可以执行范围更大的社会选择函数。具体地说，我们将证明在拟线性环境下，当参与人的类型在统计上彼此独立时，我们在贝叶斯纳什均衡中总可以执行至少一个事后有效率的社会选择函数（即该函数有着有效率的项目选择，而且满足预算平衡），而在上一讲中，我们看到这在占优策略执行中可能无法实现（Green 和 Laffont，1979）。证明此事之后，我们详细考察贝叶斯可执行社会选择函数的性质，我们主要分析拟线性情形，即参与人的效用函数关于他们的类型是拟线性的。

## AGV 机制

现在我们考察拟线性环境（当然除此之外，因为涉及概率分布，我们还需要假设参与人的风险中性偏好）。特别地，现在一个备选方案是个向量 $x = (k, t_1, \ldots, t_I)$，其中 $k$ 是有限集 $K$ 的一个元素，$t_i \in \mathbb{R}$ 是转移给参与人 $i$ 的计价物商品（“货币”）。参与人 $i$ 的效用函数具有下列拟线性形式

$$ u_i(x, \theta_i) = v_i(k, \theta_i) + (\overline{m}_i + t_i) \tag{2} \label{eq2} $$

其中 $\overline{m}_i$ 是参与人 $i$ 的计价物禀赋。为简单起见，我们标准化 $\overline{m}_i = 0$。我们假设 $I$ 个参与人无法向外部借贷资金，因此 $X = \{(k, t_1, \ldots, t_I) : k \in K, t_i \in \mathbb{R},\ \forall i, \text{ 以及 } \sum\limits_{i=1}^I t_i \leqslant 0\}$。在这个环境下，社会选择函数具有形式 $f(\cdot) = (k(\cdot), t_1(\cdot), \ldots, t_I(\cdot))$。注意到，如果 $f(\cdot)$ 是事后有效率的，那么对于所有 $\theta \in \Theta$，我们有

$$ \sum\limits_{i=1}^I v_i(k(\theta), \theta_i) \geqslant \sum\limits_{i=1}^I v_i(k, \theta_i),\ \forall k \in K \tag{3} \label{eq3} $$

和

$$ \sum\limits_{i=1}^I t_i(\theta) = 0 \tag{4} \label{eq4} $$

在上一讲中我们看到，在某些条件下，对于满足 $\eqref{eq3}$ 和 $\eqref{eq4}$ 的社会选择函数，不可能在占优策略中如实执行。我们现在证明，当参与人的类型在统计上彼此独立（即概率密度 $\phi(\cdot)$ 具有形式 $\phi(\theta) = \phi_1(\theta_1) \times \cdots \times \phi_I(\theta_I)$）时，这样的社会选择函数能在贝叶斯纳什均衡中执行。

为了证明此事，令 $k^*(\cdot)$ 满足 $\eqref{eq3}$（这就保证了事后有效率），考虑一个社会选择函数 $f(\cdot) = (k^*(\cdot), t_1(\cdot), \ldots, t_I(\cdot))$，其中对于所有 $i = 1, \ldots, I$（注意独立性使得我们无须考虑条件概率），

$$ t_i(\theta) = E_{\theta_{-i}} \left[\sum\limits_{j \neq i} v_j(k^*(\hat{\theta_i}, \theta_{-i}),\theta_j)\right] + h_i(\theta_{-i}) \tag{5} \label{eq5} $$

其中，我们暂时令 $h_i(\cdot)$ 为关于 $\theta_{-i}$ 的一个任意函数。注意到，$\eqref{eq5}$ 中的期望项表示当参与人 $i$ 报告自己的类型为 $\hat{\theta}_i$ 而参与人 $j \neq i$ 如实报告时，参与人 $j \neq i$ 的**期望收益（expected benefits）**。这样，它是仅关于参与人 $i$ 报告的类型 $\hat{\theta}_i$ 的函数，而不是关于参与人 $j \neq i$ 报告的类型 $\theta_{-i}$ 的函数。因此，当参与人 $i$ 改变自己报告的类型时他的转移改变量，正好等于这一改变对参与人 $j \neq i$ 施加的**期望外部性（expected externality）**。

我们首先证明，形如 $\eqref{eq5}$ 的任何选择函数 $f(\cdot)$ 是贝叶斯激励相容的。为了看清这一点，注意到当参与人 $j \neq i$ 如实报告他们的类型时，参与人 $i$ 发现如实报告是他的最优策略，这是因为（记住，$\theta_i$ 和 $\theta_{-i}$ 在统计上是独立的）

$$ \begin{aligned}
    E_{\theta_{-i}}[v_i(k^*(\theta), \theta_i) + t_i(\theta) \mid \theta_i] &= E_{\theta_{-i}}\left[\sum\limits_{j=1}^I v_j(k^*(\theta), \theta_j)\right] + E_{\theta_{-i}}[h_i(\theta_{-i})] \\
    &\geqslant E_{\theta_{-i}}\left[\sum\limits_{j=1}^I v_j(k^*(\hat{\theta}_i, \theta_{-i}), \theta_j)\right] + E_{\theta_{-i}}[h_i(\theta_{-i})] \\
    &= E_{\theta_{-i}}[v_i(k^*(\hat{\theta}_i, \theta_{-i}), \theta_i) + t_i(\hat{\theta}_i, \theta_{-i}) \mid \theta_i]
\end{aligned} $$

对于所有 $\hat{\theta}_i \in \Theta_i$ 成立。上式中的不等式可从 $k^*(\cdot)$ 满足 $\eqref{eq3}$ 这一事实推出。剩下的任务是证明，我们可以选择函数 $h_i(\cdot)$（对 $i = 1, \ldots, I$）使得我们也满足预算平衡条件 $\eqref{eq4}$。出于表达上的方便，定义 $\xi_i(\hat{\theta}_i) = E_{\theta_{-i}}\left[\sum\limits_{j \neq i} v_j(k^*(\hat{\theta}_i, \theta_{-i}), \theta_j)\right]$。现在对于 $i = 1, \ldots, I$，令

$$ h_i(\theta_{-i}) = -\left(\dfrac{1}{I-1}\right)\sum\limits_{j \neq i} \xi_j(\hat{\theta}_j) \tag{6} \label{eq6} $$

选择了这些 $h_i(\cdot)$ 之后，我们有

$$ \begin{aligned}
    \sum\limits_{i=1}^I t_i(\hat{\theta}) &= \sum\limits_{i=1}^I E_{\theta_{-i}}\left[\sum\limits_{j \neq i} v_j(k^*(\hat{\theta}_i, \theta_{-i}), \theta_j)\right] + \sum\limits_{i=1}^I h_i(\theta_{-i}) \\
    &= \sum\limits_{i=1}^I \xi_i(\hat{\theta}_i) - \dfrac{1}{I-1} \sum\limits_{i=1}^I \sum\limits_{j \neq i} \xi_j(\hat{\theta}_j) \\
    &= \sum\limits_{i=1}^I \xi_i(\hat{\theta}_i) - \sum\limits_{i=1}^I \xi_i(\hat{\theta}_i) = 0
\end{aligned} $$

在直觉上，我们可以将 $\eqref{eq6}$ 中的函数 $h_i(\cdot)$ 形式想象如下：我们已经看到，当参与人的类型为 $(\theta_1,\cdots,\theta_I)$ 时，每个参与人 $i = 1, \ldots, I$ 得到的收入等于 $\xi_i(\hat{\theta}_i)$（$\eqref{eq5}$ 中的第一项）。现在如果每个参与人对所有其他参与人的收入分担 $\dfrac{1}{I-1}$ 的支出，那么给定参与人 $i$，他向其他 $I-1$ 个参与人支付的钱数之和为 $\left(\dfrac{1}{I-1}\right)\sum\limits_{j \neq i} \xi_j(\hat{\theta}_j)$，与此同时，其他 $I-1$ 个参与人支付给他的钱数之和为 $\xi_i(\hat{\theta}_i)$。因此，参与人 $i$ 得到的净转移为 $\xi_i(\hat{\theta}_i) - \dfrac{1}{I-1}\sum\limits_{j \neq i} \xi_j(\hat{\theta}_j)$。**也就是说，这里的设计思路是，所有其它 $I - 1$ 个参与人分摊一个人的收入，如此循环可以实现预算平衡。**

这个直接显示机制称为**期望外部性机制（expected externality mechanism）**（归功于 d'Aspremont 和 Gerard-Varet（1979）以及 Arrow（1979），因此也简称为 AGV 机制）。总之我们已经证明了，当参与人的伯努利效用函数形如 $\eqref{eq2}$ 而且参与人的类型在统计上彼此独立时，存在能在贝叶斯纳什均衡中可执行的事后有效率的社会选择函数。

!!! question "与 VCG 机制比较"
    敏锐的读者不难发现，$\eqref{eq5}$ 和 VCG 机制中的 $t_i(\theta)$ 的定义差距仅仅在于第一项有没有求期望，所以有的读者可能会怀疑：是不是直接套用上面 $\eqref{eq6}$ 的 $h_i$ 就可以实现 VCG 机制的预算平衡呢？显然是不对的，因为 $\eqref{eq5}$ 中我们通过对 $\theta_{-i}$ 求期望，使得第一项是一个与 $\theta_{-i}$ 无关的函数了，所以基于此定义的 $h_i$ 才可以只是 $\theta_{-i}$ 的函数；在 VCG 机制中的第一项则仍然是与 $\theta_{-i}$ 有关的，所以直接套用 $\eqref{eq6}$ 后得到的将是一个与 $\theta_i$ 有关的函数，不合要求。

尽管这是个有趣的结论，但它不是故事的全部，即使当我们仅考察形如 $\eqref{eq2}$ 的伯努利效用函数以及在统计上独立分布的类型时。原因在于，在很多情形下，参与人可以选择不参与机制，因此，对于我们想执行的任何机制来说，它们必须不仅满足激励相容约束，而且必须满足**个人理性约束（individual rationality constraints）**或**称参与约束（participation constraints）**。这个问题，我们将在下一节讨论，在本节余下内容中，我们先考察一种特殊但常见的情形，即参与人的偏好关于他们的类型是线性的，而且他们的类型是独立分布的。

## 线性效用情形下的贝叶斯激励相容

现在假设每个参与人i的伯努利效用函数具有下列形式

$$ u_i(x, \theta_i) = \theta_i v_i(k) + (\overline{m}_i + t_i) $$

与以前一样，对于所有 $i$，我们标准化 $\overline{m}_i = 0$。我们还假设每个参与人 $i$ 的类型位于区间 $\Theta_i = [\underline{\theta}_i, \overline{\theta}_i] \subset \mathbb{R}$，其中 $\underline{\theta}_i \neq \overline{\theta}_i$；而且，参与人的类型在统计上彼此独立。我们将 $\theta_i$ 的分布函数记为 $\Phi_i(\cdot)$，我们假设与 $\Phi_i(\cdot)$ 相伴的密度为 $\phi_i(\cdot)$，其中 $\phi_i(\theta_i) > 0$ 对于所有 $\theta_i \in [\underline{\theta}_i, \overline{\theta}_i]$。

我们首先关注社会选择函数 $f(\cdot) = (k(\cdot), t_1(\cdot), \ldots, t_I(\cdot))$ 何时是贝叶斯激励相容的，并给出它的必要且充分条件（这个条件比 $\eqref{eq1}$ 要具体很多，还可以得到更进一步的推论）。这就是所谓的**迈尔森引理**，定理的陈述与证明见下一讲最优机制，模型的基本假定与上面完全一致。除此之外，这里我们还可以得到一个推论，即拍卖的收入等价定理，我们也放到最优机制一讲进一步讨论，这里不再赘述。

## 参与约束

### 基本定义

此前的讨论研究了私人信息对可执行的社会选择函数集施加的约束。然而，直到目前我们的分析一直隐含地假设每个参与人必须参与机制设计者选择的任何机制。也就是说，参与人i的自行决定权受到限制，他只能在机制允许的行动中选择自己的最优行动。然而，在很多情形下，参与人是可以自愿选择是否参与机制的。因此，对于一个社会选择函数来说，如果某个机制想要成功执行它，那么该函数必须不仅是激励相容的，而且必须满足某种**参与约束**或称**个人理性约束**。在本节，我们简要考察这些施加在可执行社会选择函数集上的额外约束。为了提供一些直觉，下面的例子说明了参与约束的存在如何限制了能成功执行的社会选择函数集：

!!! question "例 1：公共项目选择的参与约束"
    回忆此前对公共项目选择的讨论，这里我们考虑一个简单的例子。参与人必须决定是否建设某个给定的项目，因此 $K = \{0, 1\}$。参与人有两个：1 和 2。对于每个参与人 $i$，$\Theta_i = \{\underline{\theta}, \overline{\theta}\}$，因此，每个参与人对该公共项目的评价要么为 $\overline{\theta}$，要么为 $\underline{\theta}$。我们假设 $\overline{\theta} > 2\underline{\theta} > 0$。该项目的成本为 $c \in (2\underline{\theta}, \overline{\theta})$。假设我们想执行有着事后有效率的项目选择的社会选择函数；也就是说，在这样的函数中：
    
    1. 如果 $\theta_1$ 或 $\theta_2$ 等于 $\overline{\theta}$，那么 $k^*(\theta_1, \theta_2) = 1$；
    2. 如果 $\theta_1 = \theta_2 = 0$，那么 $k^*(\theta_1, \theta_2) = 0$。
    
    如果没有保证自愿参与的约束，我们在上一讲已经知道，在这种情形下，我们可以使用 VCG 机制在占优策略中执行某个这样的社会选择函数。

    然而，假设每个参与人有权在任何时候退出机制（也许是退出团伙），而且如果他退出，他将不能得到公共项目的收益，当然他也能避免支付任何货币转移。我们能执行一个保证自愿参与而且有着事后有效率的项目选择水平的社会选择函数吗？答案是否定的。为了看清这一点，注意到如果参与人 1 能在任何时候退出，那么为了保证他参与，必须使得 $t_1(\underline{\theta}, \overline{\theta}) \geqslant -\underline{\theta}$。也就是说，必须使得当参与人 1 对项目的评价为 $\underline{\theta}$ 时，他支付的钱数不大于 $\underline{\theta}$。现在考虑当两个参与人报告他们的评价都为 $\overline{\theta}$ 时，参与人 1 的转移为多少：如果如实报告是占优策略，那么 $t_1(\overline{\theta}, \overline{\theta})$ 必定满足

    $$ \overline{\theta}k^*(\overline{\theta}, \overline{\theta}) + t_1(\overline{\theta}, \overline{\theta}) \geqslant \overline{\theta}k^*(\underline{\theta}, \overline{\theta}) + t_1(\underline{\theta}, \overline{\theta}) $$

    或者，记住 $k^*(\overline{\theta}, \overline{\theta}) = 1$，$k^*(\underline{\theta}, \overline{\theta}) = 1$；在上式中替换它们，可得

    $$ \overline{\theta} + t_1(\overline{\theta}, \overline{\theta}) \geqslant \overline{\theta} + t_1(\underline{\theta}, \overline{\theta}) $$

    或

    $$ t_1(\overline{\theta}, \overline{\theta}) \geqslant t_1(\underline{\theta}, \overline{\theta}) $$

    由于 $t_1(\underline{\theta}, \overline{\theta}) \geqslant -\underline{\theta}$，这意味着 $t_1(\overline{\theta}, \overline{\theta}) \geqslant -\underline{\theta}$。因此，我们断言当 $(\theta_1, \theta_2) = (\overline{\theta}, \overline{\theta})$ 时，参与人 1 对项目支付的钱数不大于 $\underline{\theta}$。而且，根据对称性，当 $(\theta_1, \theta_2) = (\overline{\theta}, \overline{\theta})$ 时，参与人 2 支付的钱数也不大于 $\underline{\theta}$，即 $t_2(\overline{\theta}, \overline{\theta}) \geqslant -\underline{\theta}$。因此，$t_1(\overline{\theta}, \overline{\theta}) + t_2(\overline{\theta}, \overline{\theta}) \geqslant -2\underline{\theta}$。但如果这样，那么由于 $2\underline{\theta} < c$，可行性条件 $t_1(\overline{\theta}, \overline{\theta}) + t_2(\overline{\theta}, \overline{\theta}) \leqslant -c$ 无法得到满足。因此，我们断言，当参与人能在任何时候退出机制时，不可能执行事后有效率的社会选择函数。

    还要注意到，即使存在着不关心项目决策的“外部参与人”（比如“参与人 0”），当他也能够在任何时候退出时，上述结论仍然成立。这是因为，为了保证参与人 0 参与机制，他的转移 $t_0(\theta_1, \theta_2)$ 对于 $(\theta_1, \theta_2)$ 的每个实现值必定是非负的。特别地，我们必定有 $t_0(\overline{\theta}, \overline{\theta}) \geqslant 0$，因此可行性条件 $t_0(\overline{\theta}, \overline{\theta}) + t_1(\overline{\theta}, \overline{\theta}) + t_2(\overline{\theta}, \overline{\theta}) \leqslant -c$ 无法得到满足。

一般来说，对于任何既定情形，参与约束可能发生在三个阶段。首先，与例 1 一样，一个参与人 $i$ 能在**事后阶段（ex post stage）**退出，即在参与人已经报告了他们的类型以及 $X$ 中的一个结果已被选择之后退出。正式地说，假设当参与人 $i$ 的类型为 $\theta$ 时，他能从退出得到的效用为 $\overline{u}_i(\theta)$。于是，为了保证参与人 $i$ 的参与，我们必须满足**事后参与约束（ex post participation constraints）**或**事后个人理性约束**：

$$ u_i(f(\theta_i, \theta_{-i}), \theta_i) \geqslant \overline{u}_i(\theta_i),\ \forall (\theta_i, \theta_{-i}) \tag{7} \label{eq7} $$

在其他环境下，参与人可能只能在**事中阶段（interim stage）**退出，即在每个参与人都已经知道自己的类型但还没在机制中选择行动时退出。令 $U_i(f \mid \theta_i) = E_{\theta_{-i}}[u_i(f(\theta_i, \theta_{-i}), \theta_i) \mid \theta_i]$ 表示当参与人 $i$ 的类型为 $\theta_i$ 时他从执行社会选择函数 $f(\cdot)$ 的机制中得到的**事中期望效用**，那么当参与人 $i$ 的类型为 $\theta_i$ 时他将参与能执行社会选择函数 $f(\cdot)$ 的机制当且仅当 $U_i(f \mid \theta_i) \geqslant \overline{u}_i(\theta)$。因此，参与人 $i$ 的**事中参与约束（interim participation constraints）**或**事中个人理性约束**要求

$$ U_i(f \mid \theta_i) = E_{\theta_{-i}}[u_i(f(\theta_i, \theta_{-i}), \theta_i) \mid \theta_i] \geqslant \overline{u}_i(\theta_i),\ \forall \theta_i \tag{8} \label{eq8} $$

比较事中和事后，我们发现事后还要求 $\eqref{eq7}$ 对于任意的 $\theta_{-i}$ 成立，这是因为事后 $\theta_{-i}$ 的值确定了，而事中还是一个需要求期望的参数。在最后一种情形下，参与人 $i$ 可能只能在**事前阶段（ex ante stage）**拒绝参与，即在参与人知道他们的类型之前拒绝参与。令 $U_i(f) = E_{\theta_i}[U_i(f \mid \theta_i)] = E[u_i(f(\theta_i,\theta_{-i}), \theta_i)]$ 表示参与人 $i$ 从执行社会选择函数 $f(\cdot)$ 的机制中得到的**事前期望效用**，那么参与人 $i$ 的**事前参与约束（ex ante participation constraint）**或**事前个人理性约束**为

$$ U_i(f) \geqslant E_{\theta_i}[\overline{u}_i(\theta_i)] \tag{9} \label{eq9} $$


参与人在知道自己的类型之前同意参与机制，这种约束是事前参与约束类型。相反，当参与人在参与机制之前已经知道了自己的类型，这种约束是事中参与约束类型。最后，如果无法要求参与人接受机制指定的但违背他意愿的结果，这时我们面对的是事后参与约束（例如，如果机制能够导致一个参与人破产，那么破产法条款对事后效用提供了一个有效下界，此时参与人可以据此决定是否事后决定破产（退出机制））。当然，在考虑问题时我们很多时候都考虑事中参与约束，因为这是最自然且常见的情形。

注意到如果 $f(\cdot)$ 满足 $\eqref{eq7}$，那么它满足 $\eqref{eq8}$；如果它满足 $\eqref{eq8}$，那么它满足 $\eqref{eq9}$。但在另外一个方向上，这种关系未必成立，即如果 $f(\cdot)$ 满足 $\eqref{eq9}$，那么它未必满足 $\eqref{eq8}$ 从而未必满足 $\eqref{eq7}$。因此，对于上述三种参与约束类型来说，事后参与约束施加的约束最严厉，事前参与约束最不严厉。

总之，当参与人的类型是私人信息时，能被成功执行的社会选择函数集必须不仅满足激励相容、预算平衡，还必须满足具体环境要求的任何参与约束。在本节余下的内容中，我们通过研究重要的**迈尔森-萨特斯韦特定理**（归功于 Myerson 和 Satterthwaite（1983）），说明参与约束对可执行社会选择函数集施加的进一步限制。

### 迈尔森-萨特斯韦特定理

考虑之前提到过的双边交易的例子。参与人 1 是某个不可分割物品的卖者，他对该物品的评价位于区间 $\Theta_1 = [\underline{\theta}_1, \overline{\theta}_1] \subset \mathbb{R}$；参与人 2 是买者，他对该物品的评价位于 $\Theta_2 = [\underline{\theta}_2, \overline{\theta}_2] \subset \mathbb{R}$。这两个人对物品的评价在统计上是独立的，$\theta_i$ 的分布函数为 $\Phi_i(\cdot)$，相应的密度函数为 $\phi_i(\cdot)$，其中 $\phi_i(\theta_i) > 0$ 对于所有 $\theta_i \in [\underline{\theta}_i, \overline{\theta}_i]$。我们令 $y_i(\theta)$ 表示当参与人类型为 $\theta = (\theta_1, \theta_2)$ 时参与人 $i$ 得到物品的概率，因此，给定 $\theta$，他的期望效用为 $\theta_i y_i(\theta) + t_i(\theta)$（对于所有 $i$ 我们标准化 $\overline{m}_i = 0$）。

AGV 机制表明，在这个环境中我们可以贝叶斯执行一个事后有效率的社会选择函数（在该双边交易环境下，我们可以将这个函数称为“交易规则”）。然而，当交易是自愿的时，AGV 机制遇到了问题。在这种情形下，对于参与人 $i$ 来说，如果想要他参加，那么他在任何类型下从交易得到的期望收益必定是非负的。特别地，如果类型 $\theta_i$ 的卖者想要参与能执行的社会选择函数 $f(\cdot)$ 的一个机制，也就是说，如果参与这个机制对于类型 $\theta_i$ 的卖者来说是**个人理性的**，那么必定有 $U_1(f \mid \theta_1) \geqslant \theta_1$，这是因为这个卖者如果不参与机制而是自己消费该物品，他能得到期望效用 $\theta_1$。类似地，类型 $\theta_2$ 的买者如果拒绝参与机制，那么他得到的效用为零，因此 $U_2(f \mid \theta_2) \geqslant 0$。遗憾的是，在AGV 机制中，我们可以验证这些事中参与约束得不到满足。

**迈尔森-萨特斯韦特定理（Myerson-Satterthwaite theorem）**告诉我们一个坏消息：当交易收益有可能发生但未必发生时（后面会形式化这一条件），不存在既满足贝叶斯激励相容约束又满足这些事中参与约束的事后有效率的社会选择函数。因此，在定理给定的条件下，私人信息和自愿参与意味着不可能实现事后效率。

!!! note "迈尔森-萨特斯韦特定理"
    在某个双边交易中，买者和卖者都是风险中性的，他们对商品的评价 $\theta_1$ 和 $\theta_2$ 分别从区间 $[\underline{\theta}_1, \overline{\theta}_1] \subset \mathbb{R}$ 和 $[\underline{\theta}_2, \overline{\theta}_2] \subset \mathbb{R}$ 以严格正的概率密度独立抽取出，而且 $(\underline{\theta}_1, \overline{\theta}_1) \cap (\underline{\theta}_2, \overline{\theta}_2) \neq \emptyset$。那么不存在贝叶斯激励相容的社会选择函数使得该函数既是事后有效率的，又能给予每个买者类型和每个卖者类型非负期望交易收益。

!!! note "迈尔森-萨特斯韦特定理的证明思路"
    证明分为两步，我们写出两步的思路，具体的可以参考 MWG《微观经济理论》命题 23.E.1：

    第 1 步：对于任何贝叶斯激励相容和事中个人理性社会选择函数 $f(\cdot) = [y_1(\cdot), y_2(\cdot), t_1(\cdot), t_2(\cdot)]$，其中 $y_1(\theta_1, \theta_2) + y_2(\theta_1, \theta_2) = 1$ 而且 $t_1(\theta_1, \theta_2) + t_2(\theta_1, \theta_2) = 0$，我们需要证明

    $$ \int_{\underline{\theta}_1}^{\overline{\theta}_1} \int_{\underline{\theta}_2}^{\overline{\theta}_2} y_2(\theta_1, \theta_2) \left[\left(\theta_2 - \dfrac{1-\Phi_2(\theta_2)}{\phi_2(\theta_2)}\right) - \left(\theta_1 + \dfrac{\Phi_1(\theta_1)}{\phi_1(\theta_1)}\right)\right] \phi_1(\theta_1) \phi_2(\theta_2) \, \mathrm{d}\theta_2 \, \mathrm{d}\theta_1 \geqslant 0 \tag{10} \label{eq10} $$

    第 2 步：证明当 $\theta_2 > \theta_1$ 时若 $y_2(\theta_1, \theta_2) = 1$，或当 $\theta_2 < \theta_1$ 时若 $y_2(\theta_1, \theta_2) = 0$（即事后有效率的），则 $\eqref{eq10}$ 不成立。

我们现在来总结一下此前学习的机制以及不可能定理。直到目前，我们考虑的社会选择函数需要满足的性质有如下四点：

1. 激励相容
2. 帕累托最优（事后有效率）
3. 预算平衡
4. 个人理性

吉巴德-萨特斯韦特定理告诉我们，在备选方案大于等于 3 个时，且偏好关系可以取遍 $\mathcal{P}$（回忆 $\mathcal{P}$ 的定义）以及 $f(\Theta) = X$ 时，在占优策略下满足 1 的社会选择函数只能是独裁的。于是接下来我们把目光转向了偏好限制在拟线性场景下的情况，我们讨论了 VCG 机制，它是满足 1、2、4 的机制（个人理性我们只需要采纳主角机制即可，在 VCG 拍卖中也会提到），但不一定满足 3，并且 Green 和 Laffont（1979）证明了在占优策略情形下，当参与人估值函数任意可取时，不存在一个机制能够同时满足 1、2、3。

于是接下来我们考虑了更弱的贝叶斯执行的情形，得到了 AGV 机制可以同时满足 1、2、3 但不一定满足 4，并且迈尔森-萨特斯韦特定理告诉我们，在双边交易的一个情形下，不存在一个机制能够同时满足 1、2、3、4。因此现在还有一个很直接的问题留待我们探讨：什么情况下可以找到同时满足 1、2、3、4 的机制呢？我们将在拍卖理论中站在拍卖的视角给出一个充要条件。

## 附录：完全信息情形下的执行问题

在本附录，我们简要讨论完全信息环境下的执行问题。在完全信息情形下，我们假设每个参与人不仅能观知他自己的偏好参数 $θ_i$，还能观知所有其他参与人的偏好参数 $θ_{-i}$。然而，尽管参与人能观知 $θ$，我们仍然假设局外人不能。因此，尽管参与人能观知 $θ$，仍然存在着执行问题：由于局外人（比如法院）不能观知 $θ$，参与人不能签订有约束力的事前协议：约定当参与人的偏好为 $θ$ 时他们将选择结果 $f(θ)$。相反，他们只愿同意参与某个机制：如果 $θ$ 得以实现，均衡结果为 $f(θ)$。

注意到，我们可以将完全信息环境视为本章一直考察的一般环境的一种特殊情形，在这种情形下，上的概率密度 $\phi(\cdot)$ 具有下列（退化的）性质：每个参与人在观测自己的类型时完全知道其他参与人的类型。

现在开始分析。注意到可在占优策略中执行的社会选择函数集不受存在完全信息的影响，这是因为参与人关于其他参与人类型的信念不会影响他的占优策略集，这是由占优的等价定义可以看出的，因为等价定义完全不依赖对其他参与人的类型的信念。然而，上述结论对于基于贝叶斯纳什均衡的执行不成立。我们已经知道，在完全信息环境中，贝叶斯纳什均衡概念就是标准的纳什均衡概念。这样我们就得到了如下定义：

!!! note "定义 3：纳什执行"
    机制 $\Gamma = (S_1, \cdots, S_I, g(\cdot))$ 可在纳什均衡中**执行**社会选择函数 $f(\cdot)$，如果对于参与人偏好参数的每个组合 $θ = (\theta_1, \ldots, \theta_I) \in \Theta$，由 $F$ 产生的博弈存在着一个纳什均衡 $s^*(θ) = (s_1^*(θ), \ldots, s_I^*(θ))$，使得 $g(s^*(0)) = f(θ)$。机制 $\Gamma = (S_1, \ldots, S_1, g(\cdot))$ 可在纳什均衡中**强执行**（strongly implement）社会选择函数 $f(\cdot)$，如果对于参与人偏好参数的每个组合 $θ = (\theta_1, \ldots, \theta_I) \in \Theta$，由 $\Gamma$ 产生的博弈的每个纳什均衡均导致结果 $f(θ)$ 发生。

关于纳什均衡中的执行，我们首先指出，如果本章前面中使用的弱执行概念（即上面的“执行”概念，即可能存在多个均衡，但我只要求其中一个执行 $f(\cdot)$ 即可）得以满足，那么只要 $I \geqslant 3$，任何社会选择函数都可以在纳什均衡中执行。为了看清这一点，考虑下列机制：每个参与人 $i$ 同时报告关于 $I$ 个参与人的一个类型组合。如果至少 $I-1$ 个人报告的类型组合相同，比如说为 $\hat{\theta}$，那么我们选择结果 $f(\hat{\theta})$。否则，我们选择结果 $x_0 \in X$（$x_0$ 为任意的）。在这个机制下，对于每个类型组合 $\theta$，存在着一个纳什均衡使得每个参与人报告 $\theta$，而且由此导致的结果为 $f(\theta)$，这是因为任何参与人的单方面偏离都不会影响结果。所以对于任何函数 $f(\cdot)$，我们都可以这样设计机制来执行。

尽管这个机制能在纳什均衡中执行 $f(\cdot)$，显然它不是个合意的机制（即，它对 $f(\cdot)$ 的执行不是很有说服力），这是因为当偏好组合为 $\theta$ 时，存在无法产生结果 $f(\theta)$ 的很多其他均衡。事实上，在这个机制下，给定偏好参数组合 $θ$，对于每个 $x \in f(\Theta) = \{x \in X \mid \exists \theta \in \Theta \text{ 使得 } f(\theta) = x\}$，存在一个能产生 $x$ 的纳什均衡。于是，我们看到对于伴有 $I \geqslant 3$ 的纳什执行，如何令人满意地执行给定的社会选择函数的核心就是如何处理多个均衡的问题（见 MWG《微观经济理论》23 章附录 A）。

那么我们能在纳什均衡中强执行什么样的社会选择函数呢？下面的命题（源于 Maskin（1977））的简单但有力的结果说明了这一点：

!!! note "Maskin（1977）"
    如果社会选择函数 $f(\cdot)$ 可在纳什均衡中强执行，那么 $f(\cdot)$ 是单调的。

!!! note "证明"
    假设 $\Gamma = (S_1, \ldots, S_I, g(\cdot))$ 可强执行 $f(\cdot)$。于是当偏好参数组合为 $\theta$ 时，存在一个能产生结果 $f(\theta)$ 的纳什均衡；根据纳什均衡以及纳什执行的定义，这也就是说，存在一个具有下列性质的策略组合 $s^* = (s_1, \ldots, s_I)$：$g(s^*) = f(\theta)$ 以及 $g(s_i', s^*_{-i}) \in L_i(f(\theta), \theta_i)$ 对于所有 $s_i' \in S_i$ 和所有 $i$ 成立。
    
    现在假设 $f(\cdot)$ 不是单调的。于是存在另外一个偏好参数组合 $\theta'$ 使得 $L_i(f(\theta), \theta_i) \subset L_i(f(\theta), \theta_i')$ 对于所有 $i$ 成立，但是 $f(\theta) \neq f(\theta')$。然而 $s^*$ 也是偏好参数组合 $\theta'$ 下的一个纳什均衡，这是因为 $g(s_i', s^*_{-i}) \in L_i(f(\theta), \theta_i')$ 对于所有 $s_i' \in S_i$ 和所有 $i$ 成立。因此出现了矛盾（$g(s^*)$ 出现了两个可能值），故 $\Gamma$ 不能强执行 $f(\cdot)$。

下面的命题是上面的定理以及吉巴德-萨特斯韦特定理的一个直接推论：

!!! note "独裁"
    假设 $X$ 是有限的，而且包含至少三个元素，对于所有的 $i$ 有 $\mathcal{R}_i = \mathcal{P}$，且 $f(\Theta) = X$，那么社会选择函数 $f(\cdot)$ 在纳什均衡中可强执行当且仅当它是独裁的。

因此我们可以看到，在处理多个均衡问题时，可执行社会选择函数集施加了非常大的限制。事实上，Maskin（1977）也证明了，当 $I > 2$ 时，单调性几乎是强执行的充分条件（证明略去）。马斯金增加的条件，称为**无否决权（no veto power）**条件，要求如果 $I-1$ 个参与人都认为某个备选方案 $x$ 是最优的，那么 $x=f(\theta)$（显然这一要求是非常弱的）。

!!! note "Maskin（1977）"
    如果 $I \geqslant 3$，$f(\cdot)$ 是单调的且满足无否决权条件，那么 $f(\cdot)$ 可在纳什均衡中强执行。

事实上，我们还可以有更进一步的结论：对于一个多值社会选择对应（correspondence）$f(·)$，如果当 $x \in f(\theta)$ 和 $L_i(x, \theta_i) \subset L_i(x, \theta_i')$ 对于所有 $i$ 成立时 $x \in f(\theta_i')$，我们说 $f(·)$ 是单调的，那么之前的命题中纳什执行必要和充分条件对于多值情形也成立。

到目前我们已经看到，“淘汰”不合意的均衡这个要求（以强执行概念形式化）对可执行社会选择函数集施加了很大的限制。这意味着如果我们转而使用纳什均衡精炼概念，我们也许能够更成功。事实上，这样的精炼的确非常有力量。感兴趣的读者可以参考 MWG《微观经济理论》附录 B。