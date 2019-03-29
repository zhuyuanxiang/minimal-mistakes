---
title: "《模式识别与机器学习》的读书笔记"
excerpt: "PRML的经典教材，这次下定决心读完。"
classes: wide
categories:
- Algorithm
tags:
- Machine Learning
- Statistics Learning
- Data Science
- Pattern Recognition
- Bayesina Methods
create_at: 2019-03-29
last_modified_at: 2019-04-15
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

# 全书总评

* 书本印刷质量：4 星。PDF打印，印刷清楚，排版有点紧凑，错误较少并且不影响阅读。
* 著作编写质量：4 星。机器学习的进阶。
  * 全书内容自洽，数学方面不算太深，具备大学工科数学功底（微积分、线性代数、概率统计）就可以阅读，如果想深入理解还需要补充随机过程、泛函分析、最优化、信息论等，如果还想更深一层还可以补充决策论、测度论、流形几何等理论；再深俺就完全不知道了。
  * 作者以讲清楚Bayesian方法的来龙去脉为根本目的，所以全书紧紧围绕在Bayesian同志的周围，尽可能以Bayesian思想来分析各种模式识别与机器学习中的常用算法，对于已经零散地学习了许多种算法的同学大有裨益。
  * 全局的结构是点到面的风格，以一个二项式拟合的例子一点点铺开，节奏稍慢但是前后连贯，知识容易迁移理解；
* 笔记目的：记录重点，方便回忆。

# C01. 绪论

# 1.1. 基本知识点

* 训练与训练集(training set)、通过目标向量(target vector)学习，利用测试集(test set)测试学习的结果，泛化(generalization)表示新样本的预测的能力
* 原始输入向量需要被预处理(pre-processed)，变换到新的变量空间，也称为特征抽取(feature extraction)
* 有监督学习(supervised learning)
  * 离散学习称为分类(classification)问题
  * 连续学习称为回归(regression)问题
* 无监督学习(unsupervised learning)
  * 离散学习称为聚类(clustering问题
  * 连续学习称为密度估计(density estimation)
    * 高维空间投影到二维或者三维空间，为了数据可视化(visualization)
* 反馈学习（强化学习）(refinforcement learning)：本书不关注
  
# 1.2. 例子：多项式曲线拟合

* 概率论提供了数学框架，用来描述不确定性；
* 决策论提供了合适的标准，用来进行最优的预测。
* 多项式函数是线性模型，充分讨论在C03和C04。
  * 最小化误差函数(error function)：常用的是平方误差函数，根均方（RMS）误差更方便
  * 多项式的阶数的选择，称为模型对比(model comparison)或者模型选择(model selection)问题。
  * 过于完美的拟合训练集数据可能会出现过拟合(over-fitting)问题。大量的数据可以避免过拟合问题。
  * 训练数据的数量应该是模型可调节参数的数量的5到10倍。
  * 最大似然(maximum likelihood，ML）
    * 寻找模型参数的最小平方法代表了ML的一种特殊情形
    * 过拟合问题是ML的一种通用属性
    * Bayesian方法可以自然地解决过拟合问题
    * 控制过拟合的技术有正则化（regularization）方法，通过给误差函数增加惩罚项
      * 在统计学中叫做收缩（shrinkage）方法
      * 在二次正则项中称为山脊回归(ridge regression)
      * 在神经网络中称为权值衰减(weight decay)
      * 正则项对过拟合的影响可以通过λ系数来认识
    * 控制过拟合的技术有验证集(validation set)，也被称为拿出集(hold-out set)，缺点是不能充分利用数据

# 1.3. 概率论

* （建议跟着公式和例子推导一下）
* 离散随机变量与连续随机变量之间的关系有助于理解概率中的其他概念，例如：期望、方差、熵等等的定义和推导
* **概率论的两个基本规则**（后面会有大量的应用，需要充分理解才能正确的使用）
  * 加和规则(sum rule)
  * 乘积规则(product rule)
* 离散随机变量
  * 概率质量函数(probability mass function)
  * 联合概率(joint probability)
    * 利用加和规则得到边缘概率(marginal probability)
    * 利用乘积规则得到条件概率(conditional probability)
* 连续随机变量
  * 概率密度函数(probability density function)
  * 累积分布函数(cumulative distribution function)
* 期望(expectation)：函数的平均值
  * 有限数量的数据集，可以用 **求和** 的方式估计期望
  * 多变量函数的期望，需要使用下标来表明被平均的是哪个变量
  * 条件分布的条件期望(conditional expectation)
* 方差(variance)：度量了函数在均值附近变化性的大小。
  * 协方差(covariance)：度量两个随机变量之间的关系
* **Bayesian概率**
  * 后验概率∝似然函数×先验概率
  * 似然函数
    * 频率派认为参数的值是固定的，可以通过某种形式的“估计”来确定；
      * 广泛使用最大似然估计(maximum likelihood estimator, MLE)
      * 函数的负对数被叫做误差函数，最大化似然函数等价于最小化误差函数
    * Bayesian派认为参数的不确定性通过概率分布来表达。
      * 取样方法：MCMC（C11）
      * 判别方法：变分贝叶斯（Variational Bayes）和期望传播（Expectation Propagagtion）
* **高斯分布**（Gaussian distribution)，也叫正态分布(normal distribution)。（各种分布的详细情况参考C02）
  * 控制参数：均值μ和方差σ^2，标准差σ，精度(precision)β
  * 期望就是均值μ
  * 分布的最大值叫众数，与均值恰好相等。
  * 多维向量的高斯分布：均值向量和协方差矩阵
  * 独立地从相同的数据点中抽取的数据被称为独立同分布(independent and identically distributed, i.i.d.)
    * 在给定的数据集下最大化概率的参数得到最大似然解：样本均值和样本方差。
    * 最大似然的偏移问题是多项式曲线拟合问题中遇到的过拟合问题的核心。
    * 最大化后验概率等价于最小化正则化的平方和误差函数

# 1.4. 模型选择

* 交叉验证(cross validation)和留一法(leave-one-out)可以解决验证模型时面临的数据不足问题。但是会增加训练成本。
* 模型表现的度量的信息准则
  * 赤池信息准则（Akaike information criterion，AIC）
  * 贝叶斯信息准则(Bayesian information criterion, BIC)
* 维度灾难
* 在高维空间中，一个球体的大部分体积都聚焦在表面附近的薄球壳上。（可以推导公式理解）
* 高维空间中，大部分数据都集中在薄球壳上导致数据无法有效区分，称为维度灾难(curse of dimensionality)
* 解决方案
  * 真实的数据经常被限制在有着较低的有效维度的空间区域中；（通过特征选择降维）
  * 真实数据通常比较光滑（至少局部上比较光滑）（通过局部流形降维）

# 1.5. 决策论
  
* 决策论：保证在不确定性的情况下做出最优的决策。
  * 从训练数据集中确定输入向量x和目标向量t的联合分布是推断(inference)问题
* 分类问题的决策
  * 最小化错误分类率
    * 输入空间根据规则切分成不同的区域，这些区域被称为决策区域。
    * 决策区域间的边界叫做决策边界(decision boundary)或者决策面(decision surface)。
  * 最小化期望损失
    * 损失函数(loss function)也称为代价函数(cost function)
      * 目标是最小化整体的损失。
    * 效用函数(utility function)
      * 目标是最大化整体的效用。
  * 拒绝选项(reject option)：避免做出错误的决策，可以使模型的分类错误率降低。
  * 分类问题的两个阶段
    * 推断(inference)
    * 决策(decision)
    * 同时解决两个阶段的问题，即把输入直接映射为决策的函数称为判别函数(discriminant function)
  * 显式或者隐式地对输入以及输出进行建模的方法称为生成式模型(generative model)
  * 使用后验概率进行决策的理由
    * 最小化风险
    * 拒绝选项
    * 补偿类先验概率
    * 组合模型（参考C14）
* 回归问题的损失函数
  * 解决回归问题的三种方法
    * 先求联合概率密度，再求条件概率密度，最后求条件均值；
    * 先解决条件概率密度的推断问题，再求条件均值；
    * 直接从训练数据中寻找一个回归函数
  * 平方损失函数的一种推广，闵可夫斯基损失函数(Minkowski loss)

# 1.6. 信息论

* 无噪声编码定理(noiseless coding theorem)：熵是传输一个随机变量状态值所需要的比特位的下界。
  * （推导过程值得理解，没有深入讨论的部分可以跳过）
* 离散随机变量的熵(entropy)
  * 最大的熵值产生于均匀分布
* 连续随机变量的熵（微分熵）
  * 具体化一个连续变量需要大量的比特位
  * 最大化微分熵的分布是高斯分布
  * 微分熵可以为负
  * 在给定x的情况下，y的条件熵
* 相对熵(relative entropy)或者KL散度(Kullback-Leibler divergence)
  * （推导过程建议理解）
  * 凸函数和严格凸函数(strictly convex function)，函数的二阶导数处处为正
  * 凹函数和严格凹函数(strictly concave function)
  * KL散度是两个分布之间不相似程度的度量。
  * 最小化KL散度等价于最大化似然函数。
  * 互信息(mutual information)：表示一个新的观测y造成的x的不确定性的减小。
  
# 1.7. 总结

* 本章对于后面需要的重要概念都进行了说明和推导，方便深入理解后面提及的各种算法。
* 如果看完本章后感觉充斥着许多新的概念，那么建议搁置些书，找本更加基础的模式识别与机器学习的书，例如：李航的《统计学习方法》和周志华的《机器学习》。当然，如果你有强大的内心和坚定的信念，你还是可以坚持的。因为本书需要的知识并不是很深，并且全书内容基本自洽，因此通过后面的学习也可以将不懂的其他知识慢慢补全。