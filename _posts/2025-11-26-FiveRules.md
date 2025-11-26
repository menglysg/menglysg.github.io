---
title: "促进合作演化的五种机制"
date: 2025-11-26 19:43:00 +0800
categories: [Blog]
tags: [five rules]
math: true
---

**Martin Nowak 提出自然选择无法独立促成合作，还需要其他辅助因素，包括 kin selection, direct reciprocity, indirect reciprocity, network reciprocity 以及 group selection。**

### 1. 亲缘选择 (Kin Selection)

* **核心机制：** 合作行为的收益直接受到亲缘系数 $r$ 的影响。
* **亲缘系数 $r$：** 表示博弈双方的亲密度，取值范围为 $[0, 1]$。

$$
\begin{array}{c|cc}
& C & D \\
\hline
C & (b-c)(1+r) & br-c \\
D & b-rc & 0 \\
\end{array}
$$

### 2. 直接互惠 (Direct Reciprocity)

* **核心机制：** 个体基于过去的互动记录，决定是否与同一对手合作。
* **下一轮概率 $w$：** 博弈双方以概率 $w$ 进行下一轮博弈。
* **期望轮数：** 在此情况下，合作个体的期望博弈轮数为 $E[N] = 1/(1-w)$。

$$
\begin{array}{c|cc}
& C & D \\
\hline
C & (b-c)/(1-w) & -c \\
D & b & 0 \\
\end{array}
$$

### 3. 间接互惠 (Indirect Reciprocity)

* **核心机制：** 个体基于对手的**声誉值**（或社会评分）决定是否合作。
* **声誉概率 $p$：** Cooperator 有概率 $p$ 得知对方的声誉值。

$$
\begin{array}{c|cc}
& C & D \\
\hline
C & (b-c) & -c(1-q) \\
D & b(1-q) & 0 \\
\end{array}
$$

### 4. 网络互惠 (Network reciprocity)
* **核心机制：** 合作的演化依赖于一个去中心化的拓扑结构，个体只与邻居互动。H是一个修正项，将网络对博弈的影响融入到收益矩阵中。

$$
\begin{array}{c|cc}
& C & D \\
\hline
C & (b-c) & H-c \\
D & b-H & 0 \\
\end{array}
$$

$$ H= \frac{bk-c(k+2)}{(k+1)(k-2)} $$

### 5. 群体选择 (Group selection)
* **核心机制**：博弈不仅仅只在群体内进行，群间也会博弈。
* **分裂概率 $p$：** 当群体内个体达到最大数量时，以概率$p$进行分裂

$$
\begin{array}{c|cc}
& C & D \\
\hline
C & (b-c)(n+m) & bm-c(m+n) \\
D & bn & 0 \\
\end{array}
$$

<mark> Hello! LPL！</mark>


### 参考文献
[1]Nowak M A. Five rules for the evolution of cooperation[J]. science, 2006, 314(5805): 1560-1563.