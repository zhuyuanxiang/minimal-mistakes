---
title: "数学解的分类"
excerpt: "封闭解、解析解、数值解的区别。"
categories:
-   Mathematics
tags:
-   Mathematics
-   Solution
create_at: 2020-05-09
last_modified_at: 2020-05-09
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

# Solutions

## Closed-form Solution

封闭解 ( [Closed-form solution](https://en.wikipedia.org/wiki/Closed-form_expression) ) 就是等式至少有一个解可以使用封闭形式的表达式来表达。

封闭形式的表达式就是包含了有限个标准运算，即常量、变量、运算 ( 加、减、乘、除 ) 和初等函数 ( N 次根、指数、对数、三角函数、双曲函数 )。因为初等函数的运算具有闭包形式，所以这种形式的解称为封闭解，也叫闭式解。

## Analytic Solution

解析解 ( [Analytical solution](https://en.wikipedia.org/wiki/Closed-form_expression#Analytic_expression) ) 就是等式至少有一个解可以使用解析形式的表达式来表达。

解析形式的表达式就是包含了封闭形式的表达式的内容外，还容许包括特别函数 ( [Bessel 函数](https://en.wikipedia.org/wiki/Bessel_functions)、[Gamma 函数](https://en.wikipedia.org/wiki/Gamma_function)、[无限级数](https://en.wikipedia.org/wiki/Series_mathematics)、[连续分数](https://en.wikipedia.org/wiki/Continued_fraction) )，不过极限和积分不容许包括在内。

解析解的性质：根据严格的公式推导，给出任意的自变量就可以求出其因变量，也就是问题的解，然后可以利用这些公式计算相应的问题。

用来求得解析解的方法称为解析法 ( Analytical techniques )，解析法即是常见的微积分技巧，例如分离变量法等。

封闭形式的表达式属于解析表达式的子类，因此封闭解也是解析解的子类。

## Numerical Solution

数值解 ( Numerical solution ) 是采用某种计算方法，如有限元法，数值逼近法，插值法等得到的解。计算结果可以被使用，但是不能根据像解析解那样根据自变量就得出计算值

数值解多发生在无法求得解析解时而采用数值分析的办法求解。

数值分析：是指在「数学分析」( 区别于「离散数学」) 的问题中，对使用「数值近似」( 区别于「符号运算」) 的算法的研究。

在数值分析的过程中，首先会将原方程加以简化，以利于后来的数值分析。例如，会先将微分符号改为差分 ( 微分的离散形式 ) 符号等，然后再用传统的代数方法将原方程改写成另一种方便求解的形式。这时的求解步骤就是将一自变量带入，求得因变量的近似解，因此利用此方法所求得的因变量为一个个离散的数值，不像解析解为一连续的分布，而且因为经过上述简化的操作，其正确性也不如解析法可靠。

## Summary

简而言之，解析解就是给出解的具体函数形式，从解的表达式中就可以算出任何对应值；数值解就是用数值方法求出近似解，给出一系列对应的自变量和解。
