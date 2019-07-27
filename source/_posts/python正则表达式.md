---
title: python正则表达式
date: 2019-07-24 17:44:07
categories:
- Python3
tags:
- 正则表达式
---
## 概括字符集  

```
#\d（[0-9]） \D（[^0-9]）
#\w（[A-Za-z_0-9]） \W ([^A-Za-z_0-9])
#.表示除了换行符的所有字符
#以python为例
import re

a = 'python 11\t11java&1223\nh\rp'

r = re.findall('\w', a)

print(r)
```  

## 数量词  

```python
#以python为例
import re 

a = 'python 11\t11java&1223\nh\rp'

#默认贪婪模式
r = re.findall('[a-z]{3,6}', a)
#非贪婪模式
r1 = re.findall('[a-z]{3,6}?', a)

# *匹配0次或者无限多次
a = 'pytho0npython1pythonn2'
r2 = re.findall('python*', a)

# +匹配1次或者无限多次
a = 'pytho0npython1pythonn2'
r2 = re.findall('python+', a)

# ?匹配0次或者1次
a = 'pytho0npython1pythonn2'
r2 = re.findall('python?', a)
print(r)
```  

## 边界匹配  

```python
import re

qq = '10000000001'

r = re.findall('^\d{4,8}$', qq)

r = re.findall('000$', qq)#显示为空
print(r)

```  

## 中文范围  

1. UTF-8 (Unicode)  
    \u4e00-\u9fa5 (中文)  
    \x3130-\x318F (韩文)  
    \xAC00-\xD7A3 (韩文)   
    \u0800-\u4e00 (日文)  