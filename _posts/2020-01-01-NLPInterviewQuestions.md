---
title: "自然语言处理面试常问问题"
excerpt: ""
categories:
- interview
tags:
- 面试
- 笔试
- 工作
- 知识库
create_at: 2019-12-29
last_modified_at: 2020-04-20
toc: false
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

# HMM模型

## 前向-后向算法
[前向-后向算法](http://www.52nlp.cn/hmm-learn-best-practices-seven-forward-backward-algorithm-4)


# EM算法

[EM算法](http://www.52nlp.cn/hmm-learn-best-practices-seven-forward-backward-algorithm-3)

直观地理解EM算法，它也可被看作为一个逐次逼近算法：事先并不知道模型的参数，可以随机的选择一套参数或者事先粗略地给定某个初始参数λ0 ，确定出对应于这组参数的最可能的状态，计算每个训练样本的可能结果的概率，在当前的状态下再由样本对参数修正，重新估计参数λ ，并在新的参数下重新确定模型的状态，这样，通过多次的迭代，循环直至某个收敛条件满足为止，就可以使得模型的参数逐渐逼近真实参数。
