---
title: "概率图模型学习总结"
excerpt: "概率图模型是一类用图来表达变量相关关系的概率模型。本文以 Murphy 的介绍性论文为基础的学习笔记。"
classes: wide
categories:
- Models
tags:
- Machine Learning
- Statistics Learning
- Data Science
- Probability Graphical Models
- Bayes Network
- Markov Random Field
- Condition Random Field
create_at: 2019-03-28
last_modified_at: 2019-03-31
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

## 修改历史

* 2019-03-28. 以论文为基础建立基本框架，与《概率图模型》那本书基本相同。

## C01. 简介

* 概率图模型（Probability Graphical Models，PGM）
  * 是概率论和图论的结合。
    * 概率论很方便地把系统中各个部分结合在一起，使整个系统被作为一个整体来处理，为模型与数据的沟通提供了接口。
    * 图论则方便模型的不同变量集合进行高度地交互，并且一种数据结构可以很自然地被设计成一个有效的、通用的算法。
      * 结点表示随机变量；
      * 边表示条件独立性假设。
  * 为处理不确定性和复杂性提供了很好的工具。
  * 对设计和分析机器学习算法起着越来越重要的作用。
    * PGM 为联合概率分布提供了很好的“表示”。
    * PGM 可以大幅地减少参数的数量。

## C02. 表示

* 链式图（Chain Graph）：既包括有向边，也包括无向边的概率图。

### 2.1. 有向图（必须无环）

* Bayesian 网络（BNs）
* 置信网络（Belief Networks）
* 生成模型（Generative Models）
* 因果模型（Causal Models）

#### 2.1.1. PCA，ICA，等等

* 用于表达连续随机变量
* 因子分析本质就是将高维观测向量解释为低维特征的线性混合。

#### 2.1.2. HMM，Kalman Filters，等等

* BN 对 隐Markov模型（Hidden Markov Models，HMM） 的解释。

#### 2.1.3. 总结

* Figure 6 是对不同的统计模型之间的关系的总结

### 2.2. 无向图

* Markov 随机场（Markov Random Field，MRF）

## C03. 推理

* 基于过程的推理分类
  * 诊断，自底向上的推理；
  * 预测，自顶向下的推理。
* 基于方法的推理分类
  * 精确推理
    * 变量消除
    * 团树
  * 近似推理
    * 抽样
    * 变分（平均场逼近）
    * 循环置信传播

### 3.1. 精确推理：变量消除

* 许多优化算法的基础：Viterbi 解码，快速 Fourier 变换（Fast Fourier Transform，FFT），贪婪算法。

### 3.2. 作为优化的推理：动态规划

* 类似于 HMM 的前向——后向算法，非周期 BN 使用的局部消息传递。
* 解决最大后验概率推理问题。

### 3.3. 基于粒子的推理：近似逼近

* 第一类包括在非树结构上使用团树消息传递模式的方法。
  * 这类方法可以理解为对能量泛函近似版本的优化，包括著名的环状置信传播 (loopybelief propagation）算法。
* 第二类包括用近似消息在团树上消息传播的方法。
  * 这类方法，通常称为期望传播（expectation propagation）算法。
  * 虽然最大化了精确的能量泛函， 但是松弛了表示 Q 的一致性约束。
* 第三类方法是推广了源于统计物理学的平均场（mean field) 的方法。
  * 这类方法使用精确的能量泛函，但是将注意力局限于具有特别简单的因子分解的分布 Q 构成的类上。
  * 为了确保可以用 Q 执行推理，选择的因子分解必须足够简单。

## C04. 学习

* 学习的目的
  * 确定模型的结构（拓扑）
  * 确定模型的参数
  * 确定模型的结构与参数。
* 学习的分类
  * 已知结构，观测充分：封闭形式的解；
  * 已知结构，观测缺失：EM 算法
  * 未知结构，观测充分：局部搜索
  * 未知结构，观测缺失：结构化的 EM 算法
* 学习的评价
  * 单个“最好”的模型，即参数集合（点估计）
  * 模型的后验分布，即参数（Bayesian 估计）

### 4.1. 已知结构，观测充分

* 有向图模型常用算法
  * 最大似然估计（Maximum Likelihood Estimator，MLE）
  * 最大后验估计（Maximum a Posterior Estimator，MAP）
* 无向图模型
  * 团势
  * MLE可以基于迭代比例拟合（Iterative Proportional Fitting，IPF）

### 4.2. 已知结构，观测缺失

* 期望最大化算法（Expectation Maximum，EM）
* Baum-Welch算法是EM算法在HMM中的应用。

### 4.3. 未知结构，观测充分

* 最大似然结构是完全图，需要加入先验信息防止过拟合。即“Ockham剃刀”。

#### 4.3.1. 搜索算法

* 定义评价函数，使用局部搜索算法（贪婪爬山法）

#### 4.3.2. Bayesian方法

* 利用MCMC（Markov　Chain　Monte Carlo）搜索方法计算后验概率。
  
### 4.4. 未知结构，观测缺失（最难）

* 贝叶斯信息准则（Bayesian Information Criterion，BIC）等价于最小描述长度（Minimum Description Length，MDL）
* 利用结构化EM算法，可以收敛到BIC评价函数的局部最大值。
  
#### 4.4.1. 虚构新的隐藏结点

* 使模型更加紧凑

## C05. 决策

* 决策论=概率论+效用论

## 参考文献

* [^Bishop,2007] Bishop, C. M. (2007). Pattern Recognition and Machine Learning.
* [^Koller,2009] Koller, D., & Friedman, N. (2009). Probabilistic Graphical Models: Principles and Techniques.
* [^Murphy,2001] Murphy, Kevin. "An introduction to graphical models." Rap. tech (2001): 1-19.
* [^肖秦琨,2007] 肖秦琨，高嵩，高晓光。动态贝叶斯网络推理学习理论及应用, 国防工业出版社, 2007.
* [^周志华,2018] 周志华 机器学习, 清华大学出版社, 2018.
* [^宗成庆,2018] 宗成庆著，统计自然语言处理（第二版）, 清华大学出版社, 2018.

## 符号说明

* P_xx，代表第 xx 页
* Ch_xx，代表第 xx 章
* Sec_xx，代表第 xx 节
* Eq_xx，代表第 xx 公式
