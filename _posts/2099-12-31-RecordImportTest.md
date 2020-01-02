---
title: "测试需要的Markdown工具"
excerpt: "这次测试MathJax的功能实现"
classes: wide
categories:
- Markdown
tags:
- MathJax
last_modified_at: 2019-04-01
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

使用MathJax引擎

* 安装Ruby
* gem install jekyll bundler
* jekyll new my-awesome-site
* cd my-awesome-site
* bundle install
  * 目录下必须有默认的GEM文件，用于安装网站需要的相关模块
* bundle exec jekyll serve --incremental
* 下载MathJax，
* "No GitHub API authentication" error 问题的解决
  * 去GitHub的Setting→Developer Setting→Personal Access Toke下Generate New Token；
  * 给Token真个名字，选择public_repo；
  * 把生成的"TOKEN码"拷贝下来，将之用github:"TOKEN码"的方式放在_config.yml文件中，就可以不再出现启动时报错的问题。


参考地址：

使用介绍：http://blog.csdn.net/xiahouzuoxin/article/details/26478179

公式详情：http://blog.csdn.net/zdk930519/article/details/54137476

公式详情：http://oiltang.com/2014/05/04/markdown-and-mathjax/