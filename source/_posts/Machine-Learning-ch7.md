---
title: 机器学习（周志华）-贝叶斯分类器
sticky: 1
mathjax: true
date: 2019-02-07 19:01:36
tags:
  - Bayes
categories:
  - Machine Learning
  - 机器学习-周志华
photos:
  - /images/Local-Gallery/Machine-Learning-ZhouZhihua.jpg
---
{%cq%}
机器学习（周志华）第七章：贝叶斯分类器的总结，主要包含**本章脉络整理**以及**章末代码展示**
{%endcq%}

<!-- more -->

# 脉络整理

## 贝叶斯决策论

假设有$N$种可能的标记，即$\mathcal{Y}={c_1,c_2,...,c_N}$，$\lambda_{ij}$是将一个真实标记为$c_j$的样本误分类为$c_i$所产生的损失，基于后验概率$P(c_i|\boldsymbol{x})$可获得将样本$\boldsymbol{x}$分类为$c_i$所产生的期望损失（expected loss），即在样本$\boldsymbol{x}$上的“条件风险”（conditional risk）

$$R(c_i|\boldsymbol{x})=\sum_{j=1}^N \lambda_{ij}P(c_j|\boldsymbol{x})$$

我们的任务是寻找一个判定准则$h:\mathcal{X}\mapsto\mathcal{Y}$以最小化总体风险

$$R(h)=\mathbb{E}_{\boldsymbol{x}}[R(h(\boldsymbol{x})|\boldsymbol{x})]$$

显然，对于每个样本$\boldsymbol{x}$，若$h$能最小化条件风险$R(h(\boldsymbol{x})|\boldsymbol{x})$，则总体风险$R(h)$也将被最小化。这就产生了贝叶斯判定准则（Bayes decision rule）：为最小化总体风险，只需在每个样本上选择那个能使条件风险$R(c|\boldsymbol{x})$最小化的类别标记，即

$$h^*(\boldsymbol{x})=\mathop{\arg\min}_{c\in \mathcal{Y}} R(c|\boldsymbol{x})$$

此时，$h^\*$称为贝叶斯最优分类器（Bayes optimal classifier），与之对应的总体风险$R(h^\*)$称为贝叶斯风险(Bayes risk)，$1-R(h^*)$反映了分类器所能达到的最好性能，即通过机器学习所能产生的模型精度的理论上限。

而若目标是最小化分类错误,也即$\lambda_{ij}$定义为
$$\lambda_{ij}=
\left\{
\begin{array}{rcl}
0, & & {if\ i==j}\\
1, & & {otherwise}
\end{array}
\right.$$


# 章末练习