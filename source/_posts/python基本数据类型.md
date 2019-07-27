---
title: python基本数据类型
date: 2019-07-24 16:25:15
categories:
- Python3
tags:
- 数据类型
- 二维数组
---
## python基本数据类型  
Python3 中有六个标准的数据类型：  
1. Number（数字）
2. String（字符串）
3. List（列表）
4. Tuple（元组）
5. Set（集合）
6. Dictionary（字典）  

不可变数据:  Number（数字）、String（字符串）、Tuple（元组）；  
可变数据: List（列表）、Dictionary（字典）、Set（集合）.  

## python中二维数组赋值浅拷贝问题  
```python
# 这会造成浅拷贝的问题
d = [[]]
d[0].append(2)
# 赋值改为下面这种方式避免浅拷贝
lists = [[] for i in range(3)]

```