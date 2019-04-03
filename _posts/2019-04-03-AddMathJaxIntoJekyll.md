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
---

1. 去 [MathJax](http://www.mathjax.org) 下载最新的软件包，一个是 [MathJax Docs](http://docs.mathjax.org/en/latest/installation.html)，还有一个是 [GitHub MathJax](https://github.com/mathjax/MathJax/releases)。
2. 有了最新的软件包，解压缩并修改原目录名为MathJax，然后把MathJax放到你 fork 的 minimal-mistakes-jekyll 项目中的 assets/js/ 目录下。
3. 在 minimal-mistakes-jekyll 项目中打开 _layouts 目录下的 default.html 文件。
4. 在 default.html 文件中找到 \<head> ，然后再后面加入以下代码

    ```html
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({tex2jax: {inlineMath: [['$$','$$'], ['\\(','\\)']]}});
    </script>
    <script type="text/javascript"
        src="/assets/js/MathJax/MathJax.js?config=TeX-AMS_HTML-full">
    </script>
    ```

5. 接下来就可以在Markdown中使用MathJax了。
   1. 使用 "$$公式$$" 表示行间公式

        $$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$

   2. 使用\\(公式\\)表示行内公式

        假设\\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)，则\\(\cdots\\)

   3. 居中格式:

        $$xxx$$

        $$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$

   4. 靠左格式:

        \\(xxx\\)

        \\(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}\\)

   5. 测试

        $$\frac{7x+5}{1+y^2}$$

        \\(l(x_i) = - \log_2 P(x_i)\\)
   6. The Lorenz Equations
        $$
        \begin{align}
        \dot{x} & = \sigma(y-x) \\
        \dot{y} & = \rho x - y - xz \\
        \dot{z} & = -\beta z + xy
        \end{align}
        $$
