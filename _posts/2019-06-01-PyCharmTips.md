---
title: "PyCharm 使用心得"
excerpt: ""
classes: wide
categories:
- Python
tags:
- Python
- PyCharm
last_modified_at: 2019-09-01
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

## 如何设置 PyCharm 的 Console 的启动脚本？

File → Settings → Build, Execution, Deployment → Console → Python Console → Starting Script
就可以把自己的启动脚本加入其中了。

## 如何设置 PyCharm 的 Python Script？

File → Settings → File and Code Templates → Python Script

PyCharm 中的文件模版变量：

* ${PROJECT_NAME} - 当前的项目名
* ${PRODUCT_NAME} - IDE 的名称
* ${NAME} - 在文件创建过程中，新文件对话框的命名
* ${USER} - 当前的登录用户
* ${DATE} - 现在的系统日期
* ${TIME} - 现在的系统时间
* ${YEAR} - 当前年份
* ${MONTH} - 当前月份
* ${DAY} - 当前月份中的第几日
* ${HOUR} - 现在的小时
* ${MINUTE} - 现在的分钟
* ${FILE} - 文件的名称
* ${MONTH_NAME_SHORT} - 月份的前三个字母缩写
* ${MONTH_NAME_FULL} - 完整的月份名
