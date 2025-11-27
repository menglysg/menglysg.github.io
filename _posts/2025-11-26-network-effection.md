---
title: "网络互惠如何通过结构效应影响演化过程？"
date: 2025-11-26 22:27:00 +0800
categories: [Blog]
tags: [network reciprocity]
math: true
---

**上一篇文章中提到的几种机制中，前三种机制都是通过直接影响博弈双方的收益来影响合作演化的。而我们知道网络互惠(network reciprocity)其实并不直接影响博弈双方的收益，而是通过结构效应对演化过程产生影响，而这个影响可以通过引入一个修正项H来表示。文本主要探讨网络互惠是如何通过结构效应实现对演化过程的影响**

### 1. **促进合作演化的几种机制的特点是什么？**
* 亲缘选择、直接互惠、间接互惠都是在**无结构**的群体中研究的 (因为在无结构的群体中，如果不外加机制，群体演化会偏好于defector)
* 在网络互惠这样一个更加贴近现实的场景中，个体处于一个**结构化**的网络中 （who-meets-whom is determined by spatial relationships or social networks）
* 微观层面上：
    * 亲缘选择、间接互惠的系数直接作用在每一次博弈上。
    * 直接互惠和网络互惠每一次博弈都是原始PD，直接互惠的影响体现在长期交互的累积（通过概率w来进行反复博弈），而网络互惠则通过结构化效应改变了个体之间的相遇模式，从而影响了博弈的长期收益。

### 2. **网络互惠的结构效应如何影响演化过程？**
1. 对于亲缘选择、直接互惠、间接互惠的促进合作演化的条件，都可以通过先将**机制的影响折算成一个新的PD矩阵**，然后再通过复制子方程来直接推导。而对于网络互惠来说，首先，其结构效应很难直接折算到收益矩阵中，其次由于网络结构并不是well-mixed population，因此就算可以折算，也无法直接通过复制子方程来推导促进合作演化的条件。但是可以考虑使用**pair approximation**以及**diffusion approximation**来近似整个演化过程。

2. **演化设置如下：**
    * $N$个个体度数为$K$的网络，其payoff matrix为：
    $$
    \begin{array}{c|cc}
    & C & D \\
    \hline
    C & a & b \\
    D & c & d \\
    \end{array}
    $$
    * 个体都以Death-Birth策略更新，且个体适应度计算公式为：$f=(1-w)+ wP$
3. **pair approximation and diffusion approximation**

    pair approximation体现在对于一个中心个体，其邻居个体可以看成独立同分布的个体，所以对于个体x来说，其邻居C个体的数量与D个体的数量为$k_C$与$k_D$的概率分别可以用 $q_{C\|x}^{k_C},q_{D\|x}^{k_D}$来表示

    $$P_C+P_D=1$$

    $$q_{C|X}+q_{D|X}=1$$

    $$P_{XY}=q_{X|Y} \cdot P_Y$$

    $$P_{AB}=P_{BA}$$

    网络中C个体数量的单位时间变化为：

    $$\dot{P}_C=(1/N)P(\Delta_{P_C}=1/N)+(-1/N)P(\Delta_{P_C}=-1/N)$$

    $$P(\Delta_{P_C}=1/N)=P_D \sum_{k_C+k_D=k} \frac{k!}{k_C!k_D!} q_{C|D}^{k_C} q_{D|D}^{k_D} \frac{k_C f_C}{k_C f_C + k_D f_D}$$

    $$P(\Delta_{P_C}=-1/N)=P_C \sum_{k_C+k_D=k} \frac{k!}{k_C!k_D!} q_{D|C}^{k_D} q_{C|C}^{k_C} \frac{k_D f_D}{k_C f_C + k_D f_D}$$

    网络中C-C边数量的单位时间变化为：

    $${\dot{P}_{CC}}=\sum_{k_C=0}^{k}(\frac{2k_C}{kN})P(\Delta_{P_{CC}}=\frac{2k_C}{kN})+\sum_{k_C=0}^{k}(-\frac{2k_C}{kN})P(\Delta_{P_{CC}}=-\frac{2k_C}{kN})$$

    $$P(\frac{2k_C}{kN})=P_D \frac{k!}{k_C!k_D!} q_{C|D}^{k_C} q_{D|D}^{k_D} \frac{k_C f_C}{k_C f_C + k_D f_D}$$

    $$P(-\frac{2k_C}{kN})=P_C \frac{k!}{k_C!k_D!} q_{C|C}^{k_C} q_{D|C}^{k_D} \frac{k_D f_D}{k_C f_C + k_D f_D}$$

    因此 $q_{C\|C}$ 单位时间内变化为：

    $$\dot{q}_{C|C}=\frac{d\frac{P_{CC}}{P_C}}{dt}$$

    其中所有变量都可以用$P_A,q_{A\|A}$来代替

    $$\dot{P}_C = w \cdot F_1(P_A,q_{A|A}) + o(w^2)$$

    $$\dot{q}_{C|C} = F_2(P_A,q_{A|A}) + o(w^2)$$

    在弱选择$w << 1$时，$\dot{P}\_C$ 时间复杂度是O(w), $\dot{q}\_{C\|C}$ 时间复杂度是O(1), 因此在演化过程中 $\dot{q}_{C\|C}$ 很快便会达到平衡态，此时 $F_2=0$ 则有:

    $$q_{C|C} - q_{D|C} = \frac{1}{k-1}$$

    $$q_{C|C} = P_C + \frac{1}{k-1}(1-P_C)$$

    意味着在演化过程中，首先会达成：在$k-1$个邻居中，一个cooperator平均比一个defector要多一个cooperator。说明了，**网络互惠会使得同类更容易聚集在一起。但是这并不意味着cooperator会更容易扩散**，因为具体的策略模仿取决于payoff。

    达到平衡之后，演化后期可以用$P_C$来表示，可以得到在 $\Delta t$ 时间内，

    $$\mathbb{E}[\Delta P_C] \simeq w \cdot \frac{k-2}{k(k-1)N} P_C(1-p_C)(\alpha P_C + \beta)\Delta t \quad \left(\equiv m(P_C)\Delta t\right),$$

    $$\text{Var}[\Delta P_C] \simeq \frac{2}{N^2} \frac{k-2}{k-1} P_C(1-P_C)\Delta t \quad \left(\equiv v(P_C)\Delta t\right).$$

    这里

    $$\alpha = (k+1)(k-2)(a-b-c+d),$$

    $$\beta = (k+1)a + (k^2-k-1)b - c - (k^2-1)d.$$

    固定概率 $\Phi_C(y) $, 即$P_C(t=0)=y$, 满足方程

    $$\phi_C(y) = \mathbb{E}[\phi_C(y + \Delta P_C)]$$

    对右边进行Taylor展开：

    $$\phi_C(y + \Delta p_C) \approx \phi_C(y) + \frac{d\phi_C}{dy}\Delta p_C + \frac{1}{2}\frac{d^2\phi_C}{dy^2}(\Delta p_C)^2 + \cdots$$

    取期望：

    $$\phi_C(y) = \phi_C(y) + \frac{d\phi_C}{dy}\mathbb{E}[\Delta p_C] + \frac{1}{2}\frac{d^2\phi_C}{dy^2}\mathbb{E}[(\Delta p_C)^2] + \cdots$$

    可得：

    $$0 = \frac{d\phi_C}{dy} \cdot m(y)\Delta t + \frac{1}{2}\frac{d^2\phi_C}{dy^2} \cdot v(y)\Delta t$$

    消去 $\Delta t$：

    $$\boxed{0 = m(y)\frac{d\phi_C(y)}{dy} + \frac{v(y)}{2}\frac{d^2\phi_C(y)}{dy^2}}$$

    解该微分方程可得：

    $$\phi_C(y) = y + w \cdot \frac{N}{6k}y(1-y)\left[(\alpha + 3\beta) + \alpha y\right] $$

    因此，$\rho_C=\Phi_C(1/N)$,即有$\rho_A > 1/N$ 当且仅当 $\alpha+3\beta > 0$ 时，即：

    $$(k^2 + 2k + 1)a + (2k^2 - 2k - 1)b > (k^2 - k + 1)c + (2k^2 + k - 1)d.$$

    当博弈类型为PD时，即$a=b-c,b=-c,c=b,d=0$，可得

    $$\frac{b}{c}>k$$

### 参考文献
[1]Nowak M A. Five rules for the evolution of cooperation[J]. science, 2006, 314(5805): 1560-1563.

[2]Ohtsuki H, Hauert C, Lieberman E, et al. A simple rule for the evolution of cooperation on graphs and social networks[J]. Nature, 2006, 441(7092): 502-505.