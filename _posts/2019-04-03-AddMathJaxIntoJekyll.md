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
        MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], ['//(','//)']]}});
    </script>
    <script type="text/javascript"
        src="/assets/js/MathJax/MathJax.js?config=TeX-AMS_HTML-full">
    </script>
    ```

5. 接下来就可以在Markdown中使用MathJax了。
   1. 使用 "$\$$$\$$ 公式 $\$$$\$$" 表示行间公式

        ```tex
        $$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
        ```

        $$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$

   2. 使用"//(\$//)公式//(\$//)" 或者 "$//($ 公式 $//\)$"表示行内公式

        假设//(x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}//)，则$\cdots$

   3. 居中格式:

        $$xxx$$

        $$\frac{7x+5}{1+y^2}$$

        $$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$

   4. 靠左格式:
        
        ```tex
        //(xxx//)  
        ```

        //(xxx//)  

        ```tex
        $x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$
        ```

        $x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$

        ```tex
        //(l(x_i) = - \log_2 P(x_i)//)
        ```

        //(l(x_i) = - \log_2 P(x_i)//)

   5. 测试

        When $a \ne 0$, there are two solutions to //(ax^2 + bx + c = 0//) and they are
        $$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

   6. The Lorenz Equations

        $$
        \begin{align}
        \dot{x} & = \sigma(y-x) \\
        \dot{y} & = \rho x - y - xz \\
        \dot{z} & = -\beta z + xy
        \end{align}
        $$

   7. The Cauchy-Schwarz Inequality

        $$
        \left( \sum_{k=1}^n a_k b_k \right)^{\!\!2} \leq
        \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
        $$

   8. A Cross Product Formula

        $$
        \mathbf{V}_1 \times \mathbf{V}_2 =
        \begin{vmatrix}
            \mathbf{i} & \mathbf{j} & \mathbf{k} \\
            \frac{\partial X}{\partial u} & \frac{\partial Y}{\partial u} & 0 \\
            \frac{\partial X}{\partial v} & \frac{\partial Y}{\partial v} & 0 \\
        \end{vmatrix}
        $$

   9. The probability of getting //(k//) heads when flipping //(n//) coins is:

        $$P(E) = {n \choose k} p^k (1-p)^{ n-k} $$

   10. An Identity of Ramanujan

        $$
        \frac{1}{(\sqrt{\phi \sqrt{5}}-\phi) e^{\frac25 \pi}} =
            1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
            {1+\frac{e^{-8\pi}} {1+\ldots} } } }
        $$

   11. A Rogers-Ramanujan Identity

        $$
        1 +  \frac{q^2}{(1-q)}+\frac{q^6}{(1-q)(1-q^2)}+\cdots =
            \prod_{j=0}^{\infty}\frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
            \quad\quad \text{for $|q|<1$}.
        $$

   12. Maxwell's Equations

        $$
        \begin{align}
        \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} & = \frac{4\pi}{c}\vec{\mathbf{j}} \\
        \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\
        \nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\
        \nabla \cdot \vec{\mathbf{B}} & = 0
        \end{align}
        $$

   13. In-line Mathematics

        Finally, while display equations look good for a page of samples, the
        ability to mix math and text in a paragraph is also important.  This
        expression //(\sqrt{3x-1}+(1+x)^2//) is an example of an inline equation.  As
        you see, MathJax equations can be used this way as well, without unduly
        disturbing the spacing between lines.