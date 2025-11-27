---
title: "网络互惠如何通过结构效应影响演化过程？"
date: 2025-11-26 22:27:00 +0800
categories: [Blog]
tags: [network reciprocity]
math: true
---

**上一篇文章中提到的几种机制中，前三种机制都是通过直接影响博弈双方的收益来影响合作演化的。而我们知道网络互惠(network reciprocity)其实并不直接影响博弈双方的收益，而是通过结构效应对演化过程产生影响，而这个影响可以通过引入一个修正项H来表示。文本主要探讨网络互惠是如何通过结构效应实现对演化过程的影响**

### 1. 促进合作演化的几种机制的特点是什么？
* 亲缘选择、直接互惠、间接互惠都是在**无结构**的群体中研究的 (因为在无结构的群体中，如果不外加机制，群体演化会偏好于defector)
* 在网络互惠这样一个更加贴近现实的场景中，个体处于一个**结构化**的网络中 （who-meets-whom is determined by spatial relationships or social networks）
* 微观层面上：
    * 亲缘选择、间接互惠的系数直接作用在每一次博弈上。
    * 直接互惠和网络互惠每一次博弈都是原始PD，直接互惠的影响体现在长期交互的累积（通过概率w来进行反复博弈），而网络互惠则通过结构化效应改变了个体之间的相遇模式，从而影响了博弈的长期收益。

### 2.网络互惠的结构效应如何影响演化过程？
对于亲缘选择、直接互惠、间接互惠的促进合作演化的条件，都可以通过先将**机制的影响折算成一个新的PD矩阵**，然后再通过复制子方程来直接推导。而对于网络互惠来说，由于结构并不是well-mixed population，因此无法直接通过复制子方程来推导促进合作演化的条件
### 参考文献

[1]Nowak M A. Five rules for the evolution of cooperation[J]. science, 2006, 314(5805): 1560-1563.

[2]Ohtsuki H, Hauert C, Lieberman E, et al. A simple rule for the evolution of cooperation on graphs and social networks[J]. Nature, 2006, 441(7092): 502-505.