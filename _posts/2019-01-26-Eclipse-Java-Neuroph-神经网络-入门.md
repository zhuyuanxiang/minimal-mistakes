---
title: "Neuroph开发过程"
excerpt: "使用Eclipse JavaEE和Neuroph学习神经网络，编写基于Java的神经网络模型"
categories:
- Coding
tags:
- Eclipse
- Neuroph
- Java
- Program
- 神经网络
- Neural Network 
create_at: 2019-01-25
last_modified_at: 2019-01-26
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

## 安装与配置
* JDK的安装：建议JRE 1.8以上；
* Neuroph安装：建议2.94的版本。[下载地址](http://neuroph.sourceforge.net/)
  * neuroph-core-2.94：开发的核心包
  * neuroph-samples-2.94：使用这个框架的例子
* Eclipse的安装：建议是java 2018-09以上的版本
  * 配置“Windows→Preferences→Java→Build Path→User Libraries→New”一个“neuroph-2.94”，再“Add External Jars”就可以把相关的包全部定义在这个变量下面。
  * 也可以使用Maven配置。

## 开发小结
### 建立项目
* 在Eclipse中创建一个Java项目。

### 配置项目
* 选中项目，“右键→Properties→Java Build Path→Libraries→Add Library→User Library→neuroph-2.94”即可把相关类包纳入到项目中。
### 理解感知机的代码
* 单层感知机：neuroph-samples-2.94.jar中org.neuroph.samples.PerceptronSample.class
```java
    public SinglePerceptronAND() {
        // create training set (logical AND function)：创建训练集（符合逻辑与函数）
        DataSet trainingSet = new DataSet(2, 1);trainingSet.addRow(...);
        // create perceptron neural network：创建感知机(两个入，一个出，就是最简单的单层一个神经元的神经网络)
        NeuralNetwork myPerceptron = new Perceptron(2, 1);
        // learn the training set：学习这个训练集，就是为了得到神经网络的参数
        myPerceptron.learn(trainingSet);
        // test perceptron：测试这个感知机，检验它训练的参数是否正确
        myPerceptron.setInput(trainingSet.get(0).getInput());
        myPerceptron.calculate();
        System.out.print("Input: " + Arrays.toString(trainingElement.getInput()));
        System.out.println(" Output: " + Arrays.toString(networkOutput));
    }


    
