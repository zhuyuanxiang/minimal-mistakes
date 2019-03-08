---
title: "《Python Cookbook》的读书笔记"
excerpt: "Python 的菜谱, 肯定是很香的, 内容也是很全的。"
categories:
- Coding
tags:
- Python
- Programming
- Data Science
create_at: 2019-03-04
last_modified_at: 2019-03-07
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---
## 全书总评
* 书本印刷质量: 4 星。印刷清楚, 排版合适, 错误很少。最好还能找本电子书, 可以少输入一些数据代码。
* 著作编写质量: 4 星。胆敢称自己的菜谱的书, 要不就是好书; 要不就是差书; 绝对不会不好不差。所以这是本长期使用 Python 人员必备的案头书。
* 代码质量: 4 星。常常学习几个里面的代码, 保证你心情愉悦! 
* 阅读笔记: 记录需要记住的重点, 方便快速回忆。

## C01. 数据结构和算法
### 序列处理
* (01) 序列分解，一对一匹配：x, y, z=(4, 8, 2)
* (02) 序列分解，一对多匹配：first, *middle, last = ('start', 1, 2, 3, 'last')
* (10) 移除序列中出现的重复元素: 生成器(yield)
* (11) 对序列切片命名: slice(start,stop,step)
* (12) 统计序列中元素出现次数: collections.Counter()
### 列表处理
* (03) collections.deque: 限制队列长度, 保留最后几项, 后来的挤掉最前面的; 
* (04) 寻找特定的 N 个元素: 
   * 寻找 N 个最大元素: heapq.nlargest()
   * 寻找 N 个最小元素: heapq.nsmallest()
* (05) 按优先级排序的队列: 
   * 向队列压入数据: heapq.heappush()
   * 从队列弹出数据: heapq.heappop()
* (13) 对字典列表排序： sorted(dict_list, key=itemgetter(keys))， itemgetter()创建一个可调用对象；
* (14) 对对象列表排序： sorted(object_list, key=attrgetter(prop))
* (15) 对字典列表分组：
### 字典处理
* (06) 一键多值字典: collections.defaultdict()
* (07) 有序的字典: collections.OrderedDict(), 保证字典迭代时按元素添加顺序进行
* (08) 字典计算
   * zip(): 将字典转换成元组; 
   * min(): 找出元组列表中的最小值; 
   * max(): 找出元组列表中的最大值; 
* (09) 寻找两个字典中的共同元素: keys() 和 items() 返回的对象都支持集合操作。

