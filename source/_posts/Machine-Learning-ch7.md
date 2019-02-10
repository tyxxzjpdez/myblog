---
title: 机器学习（周志华）-贝叶斯分类器
sticky: 1
mathjax: true
date: 2019-02-07 19:01:36
tags:
  - Bayes
  - Machine Learning
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

那么此时的贝叶斯最优分类器为

$$h^*(\boldsymbol{x})=\mathop{\arg\max}_{c\in \mathcal{Y}}P(c|\boldsymbol{x})$$

即对每个样本$\boldsymbol{x}$，选择能使后验概率$P(c|\boldsymbol{x})$最大的类别标记。那么，显然地，接下来的重点问题就是如何获得后验概率。然而，在现实任务中这通常难以直接获得。从这个角度讲，机器学习所要实现的是基于有限的训练样本尽可能准确地估计出后验概率$P(c|\boldsymbol{x})$。大体来说，主要有两种策略[^1]：

- 给定$\boldsymbol{x}$，可通过直接建模$P(c|\boldsymbol{x})$来预测$c$，这样得到的是“判别式模型”（discriminative models）
- 也可先对联合概率分布$P(c|\boldsymbol{x})$建模，然后由此获得$P(c|\boldsymbol{x})$，这样得到的是“生成式模型”（generative models）

在贝叶斯方法中，我们使用生成式模型，而对于生成式模型，必然考虑

$$P(c|\boldsymbol{x})=\frac{P(\boldsymbol{x},c)}{P(\boldsymbol{x})}$$

再基于贝叶斯定理，$P(c|\boldsymbol{x})$可以表示为

$$P(c|\boldsymbol{x})=\frac{P(c)\ P(\boldsymbol{x}|c)}{P(\boldsymbol{x})}$$

对于右边的三个量，

- $P(c)$是类先验概率，其表达了样本空间各类样本所占的比例，而由大数定理，当有充足的独立同分布样本时，其可通过各类样本出现的频率来进行估计。
- $P(\boldsymbol{x})$是用于规一化的“证据”（evidence）因子，显然地，对于给定样本$\boldsymbol{x}$，其不随$c$变化而变，是个定值。
- $P(\boldsymbol{x}|c)$是相对于类标记c的类条件概率，对其的计算不能简单地根据样本出现的频率来计算（原因见原书P148-149）。

## 极大似然估计

那么，类条件概率究竟应该如何得到呢？估计类条件概率的一种常见策略是先假定其具有某种确定的概率分布形式，再基于训练样本对概率分布的参数进行估计。就上面的例子来说，假设$P(\boldsymbol{x}|c)$具有确定的形式并且被参数向量$\boldsymbol{\theta}_c$唯一确定，则我们的任务就是利用训练集$D$估计参数$\boldsymbol{\theta}_c$。为明确起见，我们将$P(\boldsymbol{x}|c)$记为$P(\boldsymbol{x}|\boldsymbol{\theta}_c)$。

接下来就是本节要介绍的源自频率主义学派的极大似然估计（Maximum Likelihood Estimation,简称MLE）：
令$D_c$表示训练集$D$中第$c$类样本组成的集合，假设这些样本是独立同分布的，则参数$\boldsymbol{\theta}_c$对于数据集$D_c$的似然是

$$L(\boldsymbol{\theta}_c|D_c)=P(D_c|\boldsymbol{\theta}_c)=\prod_{\boldsymbol{x}\in D_c} P(\boldsymbol{x}|\boldsymbol{\theta}_c)$$

对$\boldsymbol{\theta}_c$进行极大似然估计，就是去寻找能最大化似然$P(D_c|\boldsymbol{\theta}_c)$的参数值$\hat{\boldsymbol{\theta}_c}$。直观上看，极大似然估计就是试图在$\boldsymbol{\theta}_c$所有可能取值中，找到一个能使数据出现的“可能性”最大的值。

考虑到连乘容易下溢，通常使用对数似然（log-likelihood）

$$\begin{aligned}
\begin{aligned} LL(\boldsymbol{\theta}_c)&=\log P(D_c|\boldsymbol{\theta}_c)\\
&=\sum_{\boldsymbol{x}\in D_c}\log P(\boldsymbol{x}|\boldsymbol{\theta}_c) \end{aligned}
\end{aligned}$$

此时参数$\boldsymbol{\theta}_c$的极大似然估计$\hat{\boldsymbol{\theta}_c}$为

$$\hat{\boldsymbol{\theta}_c}=\mathop{\arg\max}_{\boldsymbol{\theta}_c} LL(\boldsymbol{\theta}_c)$$

**需要注意的是**，这种参数化的方法虽然能使类条件概率估计变得相对简单，但估计结果的准确性严重依赖于所假设的概率分布形式是否符合潜在的真实数据分布。

## 朴素贝叶斯分类器

那么，除了上节的办法，还有其他求解类条件概率的办法吗？答案是有的，但是需要加一个前提，那就是“属性条件独立性假设”，也即假设每个属性独立德对分类结果发生影响。基于此，使用贝叶斯求解后验概率的公式可以重写为

$$P(c|\boldsymbol{x})=\frac{P(c)\ P(\boldsymbol{x}|c)}{P(\boldsymbol{x})}=\frac{P(c)}{P(\boldsymbol{x})}\prod_{i=1}^{d}P(x_i|c)$$

其中$d$为属性数目，$x_i$为$\boldsymbol{x}$在第$i$个属性上的取值。

由于对所有类别来说$P(\boldsymbol{x})$相同，因此在当前情况下的贝叶斯判定准则有

$$h_{nb}(\boldsymbol{x})=\mathop{\arg\max}_{c\in \mathcal{Y}}P(c)\prod_{i=1}^{d}P(x_i|c)$$

这就是朴素贝叶斯分类器的表达式。
显然，朴素贝叶斯分类器的训练过程就是基于训练集$D$来估计类先验概率$P(c)$，并为每个属性估计条件概率$P(x_i|c)$
**需要注意的细节：**若某个属性在训练集中没有与某个类同时出现过，则通过上式进行计算，在连乘过程中就会出现0，导致那么无论其他项多大，结果都会让该标记的概率降为0，这显然不合理。为了避免其他属性携带的信息被训练集未出现的属性值“抹去”，在估计概率值时通常要进行“平滑（smoothing）”，常用“拉普拉斯修正”[^2]（Laplacian correction）。

## 半朴素贝叶斯分类器

人们考虑到属性条件独立性假设在现实任务中很难成立，于是尝试对属性条件独立性假设进行一定程度的放松，也即，适当考虑一部分属性间的相互依赖信息，从而既不需要进行完全联合概率计算，有不至于彻底忽略了比较强的属性依赖关系。这也就是半朴素贝叶斯分类器的基本思想。它最常用的一种策略是”独依赖估计“（One-Dependent Estimator，简称ODE）。所谓”独依赖“就是假设每个属性在类别之外最多仅依赖于一个其他属性，即

$$P(c|\boldsymbol{x})\propto P(c)\prod_{i=1}^{d}P(x_i|c,pa_i)$$

其中$pa_i$为属性$x_i$所依赖的属性，成为$x_i$的父属性。

若每个属性的父属性都已知，那么问题就转化成类似朴素贝叶斯分类器的做法了。所以关键在于如何确定每个属性的父属性，不同的做法产生不同的独依赖分类器。

- SPODE(super-Parent ODE)方法，假设所有属性都依赖于同一属性——“超父”，然后通过交叉验证等模型选择方法来确定超父属性。
- TAN(Tree Augmented naive Bayes)则是在最大带权生成树算法的基础上，通过一些步骤将属性间依赖关系约简为属性结构。
- AODE(Averaged One-Dependent Estimator)是一种基于集成学习机制、更为强大的独依赖分类器。它尝试将每个属性作为超父来构建SPODE，然后将那些具有足够训练数据支持的SPODE集成起来作为最终结果。

# 章末练习

## 习题 7.1



# 参考

[^1]: 关于两种策略：判别式模型与生成式模型，点击[这里](https://www.cnblogs.com/fanyabo/p/4067295.html)查看更多
[^2]: 拉普拉斯修正实质上假设属性值与类别均匀分布，这是在朴素贝叶斯学习过程中额外引入的关于数据的先验