---
title: "为 minimal-mistakes-jekyll 加入 MathJax 的支持"
excerpt: "因为 GitHub 的 Markdown 不支持数学公式，只好借助于 MathJax 来实现。"
classes: wide
categories:
- Markdown
tags:
- MathJax
last_modified_at: 2019-04-03
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
mathjax: true
---



# 环境搭建

1. 去 [MathJax](http://www.mathjax.org) 下载最新的软件包，一个是 [MathJax Docs](http://docs.mathjax.org/en/latest/installation.html)，还有一个是 [GitHub MathJax](https://github.com/mathjax/MathJax/releases)。
2. 有了最新的软件包，解压缩并修改原目录名为MathJax，然后把MathJax放到你 fork 的 minimal-mistakes-jekyll 项目中的 assets/js/ 目录下。
3. 在 minimal-mistakes-jekyll 项目中打开 _layouts 目录下的 single.html 文件。
4. 在 single.html 文件中找到 \<article class="page" ... \>，然后再后面加入以下代码

```javascript
{% if page.mathjax %} 
  <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
      extensions: ["tex2jax.js"],
      jax: ["input/TeX", "output/HTML-CSS"],
      tex2jax: {
        inlineMath: [ ['$','$']],
        displayMath: [ ['$$','$$']],
        processEscapes: true
      },
      "HTML-CSS": { fonts: ["TeX"] }
    });
  </script>
  <script type="text/javascript" 
    src="/assets/js/MathJax/MathJax.js?config=TeX-AMS_HTML-full">
  </script>
{% endif %}
```

接下来就可以在Markdown中使用MathJax了。(注意：需要在文件头加入 mathjax: true)

# 使用方式

## 行间公式

- 使用` $$公式$$ `表示行间公式，公式自动居中

```tex
$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
```

$$
x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}
$$

## 行内公式

   - 使用` $公式$ `表示行内公式，公式自动靠左

```tex
  假设 $(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a})$，则 $\cdots$
```

假设 $(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a})$，则 $\cdots$
       
# 公式举例



## 公式对齐

### 不同的公式编号

```tex
\begin{align}
  \dot{x} & = \sigma(y-x) \\
  \dot{y} & = \rho x - y - xz \\
  \dot{z} & = -\beta z + xy
\end{align}
```


$$
   \begin{align}
       \dot{x} & = \sigma(y-x) \\
       \dot{y} & = \rho x - y - xz \\
       \dot{z} & = -\beta z + xy
     \end{align}
$$

### 相同的公式编号

```tex
\begin{equation}
\begin{split}
  (a+b)^4 
    &= (a+b)^2 (a+b)^2  \\
    &= (a^2+2ab+b^2)(a^2+2ab+b^2) \\
    &= a^4+4a^3b+6a^2b^2+4ab^3+b^4  \\
\end{split}
\end{equation}
```

   

$$
   \begin{equation}
   	\begin{split}
       (a+b)^4 
       &= (a+b)^2 (a+b)^2  \\
       &= (a^2+2ab+b^2)(a^2+2ab+b^2) \\
       &= a^4+4a^3b+6a^2b^2+4ab^3+b^4  \\
    	\end{split}
   \end{equation}
$$

### The Cauchy-Schwarz Inequality

```tex
  \left( \sum_{k=1}^n a_k b_k \right)^{\!\!2} \leq
    \left( \sum_{k=1}^n a_k^2 \right) 
    \left( \sum_{k=1}^n b_k^2 \right)
```


$$
   \left( \sum_{k=1}^n a_k b_k \right)^{\!\!2} \leq
     \left( \sum_{k=1}^n a_k^2 \right) 
     \left( \sum_{k=1}^n b_k^2 \right)
$$

### A Cross Product Formula

```tex
 \mathbf{V}_1 \times \mathbf{V}_2 =
  \begin{vmatrix}
    \mathbf{i} & \mathbf{j} & \mathbf{k} \\
    \frac{\partial X}{\partial u} 
    	& \frac{\partial Y}{\partial u} & 0 \\
    \frac{\partial X}{\partial v} 
    	& \frac{\partial Y}{\partial v} & 0 \\
  \end{vmatrix}
```

$$
   \mathbf{V}_1 \times \mathbf{V}_2 =
       \begin{vmatrix}
         \mathbf{i} & \mathbf{j} & \mathbf{k} \\
         \frac{\partial X}{\partial u} 
         	& \frac{\partial Y}{\partial u} & 0 \\
         \frac{\partial X}{\partial v} 
         	& \frac{\partial Y}{\partial v} & 0 \\
       \end{vmatrix}
$$

### The probability of getting $k$ heads when flipping $n$ coins is:

```tex
P(E) = {n \choose k} p^k (1-p)^{ n-k}
```

$$
P(E) = {n \choose k} p^k (1-p)^{ n-k}
$$



### An Identity of Ramanujan

```tex
\frac{1}{(\sqrt{\phi \sqrt{5}}-\phi) e^{\frac25 \pi}} =
1+\frac{e^{-2\pi}} 
  {1+\frac{e^{-4\pi}} 
    {1+\frac{e^{-6\pi}}
      {1+\frac{e^{-8\pi}} 
        {1+\ldots} 
      } 
    } 
  }
```


$$
   \frac{1}{(\sqrt{\phi \sqrt{5}}-\phi) e^{\frac25 \pi}} =
   1+\frac{e^{-2\pi}} 
     {1+\frac{e^{-4\pi}} 
       {1+\frac{e^{-6\pi}}
         {1+\frac{e^{-8\pi}} 
           {1+\ldots} 
         } 
       } 
     }
$$

### A Rogers-Ramanujan Identity

```tex
1 +  \frac{q^2}{(1-q)} + \frac{q^6}{(1-q)(1-q^2)} + \cdots =
   \prod_{j=0}^{\infty} \frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
   \quad\quad \text{for $|q|<1$}.
```
$$
1 +  \frac{q^2}{(1-q)} + \frac{q^6}{(1-q)(1-q^2)} + \cdots =
   \prod_{j=0}^{\infty} \frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
   \quad\quad \text{for $|q|<1$}.
$$

### Maxwell's Equations: 

```tex
\begin{align}
  \nabla \times \vec{\mathbf{B}} 
	  -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} 
  	& = \frac{4\pi}{c}\vec{\mathbf{j}} \\
  \nabla \cdot \vec{\mathbf{E}} 
  	& = 4 \pi \rho \\
  \nabla \times \vec{\mathbf{E}}\, 
  	+\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} 
  	& = \vec{\mathbf{0}} \\
  \nabla \cdot \vec{\mathbf{B}} 
  	& = 0
\end{align}
```



$$
\begin{align}
  \nabla \times \vec{\mathbf{B}} 
	  -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} 
  	& = \frac{4\pi}{c}\vec{\mathbf{j}} \\
  \nabla \cdot \vec{\mathbf{E}} 
  	& = 4 \pi \rho \\
  \nabla \times \vec{\mathbf{E}}\, 
  	+\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} 
  	& = \vec{\mathbf{0}} \\
  \nabla \cdot \vec{\mathbf{B}} 
  	& = 0
\end{align}
$$