---
title: "Beyond Compare Evaluate 方法"
excerpt: "Beyond Compare 4 30天试用到期的解决办法"
categories:
-   Tools
tags:
-   Beyond Compare
-   File Compare
-   Directory Compare
create_at: 2020-09-13
last_modified_at: 2020-09-13
toc: false
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

# Evaluate

## Delete DLLs

删除安装目录下的BCUnrar.dll文件

## Modify Register

1.  regedit
2.  HKEY_CURRENT_USER\Software\Scooter Software\Beyond Compare 4
3.  Delete CacheID

## Schedule Delete

1.  定义 BAT 文件，内容：`reg delete "HKEY_CURRENT_USER\Software\Scooter Software\Beyond Compare 4" /v CacheID /f`
2.  我的电脑-->管理-->任务计划程序-->创建任务-->配置定时任务基本信息
3.  将这个BAT文件定义为每4周执行一次