---
title: python函数式编程
date: 2019-07-24 16:59:21
categories:
- Python3
tags:
- 函数式编程
- 闭包
---
## 闭包  

    闭包是由函数及其相关的引用环境组合而成的实体(即：闭包=函数+引用环境)  
    
```python

# def curve_pre():
#     a = 25
#     b = 20
#     c = 10
#     def curve(x):
#         print('this is curve')
#         return a*x*b
#
#     def fun():
#         return c*2
#
#     return curve
#
# f = curve_pre()
# print(f.__closure__[0].cell_contents)
# print(f.__name__)
# print(f(2))

def foo():
    m = 9
    n = 8
    def foo1():
#        m = 1
        print(n)
    print(m)
    foo1()
    print(m)
    return foo1

#    return foo1()

f = foo()
print(f.__closure__)  

```  

## 闭包测试  
    
```python

###每次走step，求从0开始的当前位置
origin = 0

def walk(pos = origin):
    def striagh(step):
        global origin
        pos = step + origin
        origin = pos
        return origin
    return striagh

stra = walk()
print(stra(10))
print(stra(1))  

```  

## python中的三元表达式  

```python

#x > y ? x : y
#python版本三元表达式的代码
#条件为真时候的d返回 if 条件判断 else 条件为假的时候的返回
x = 2
y = 1
r = x if x > y else y
print(r)  

```  
    
## 匿名函数(lambda表达式)  

```python

def add(x ,y):
    return x+y;

print(add(2,3))

f = lambda x,y : x + y
print(f(2,3))  

```  

## python函数map的使用  

    map() 会根据提供的函数对指定序列做映射。  
    第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函数返回值的新列表。  

```python
# map函数语法:
# function -- 函数
# iterable -- 一个或多个序列
map(function, iterable, ...)

# map函数使用示例1
list_x = [1,2,3,4]
def square(x):
    return x*x
    
r = map(square, list_x)
print(r)
print(list(r))

# map使用示例2 
list_x = [1,2,3,4]
list_y = [1,2,3,4]
#list_y = [1,2,3]
    
r = map(lambda x,y : x*x + y, list_x, list_y)

print(list(r))
```  

## python中的reduce函数  

```python
from functools import reduce
#连续计算，连续调用lambda
list_x = [1,2,3,4]
r = reduce(lambda x,y:x+y, list_x)
#r = reduce(lambda x,y:x+y, list_x, 10)#10是初始值
print(r)
```  

## python装饰器  

```python
import time                                                                     

def f1():
    print('a function')

def f2():
    print('b function')


def print_current_time(func):
    print(time.time())
    func()

print_current_time(f1)
print_current_time(f2)
```  

```python
import time                                                                                                                                                                                                  

def f1():
    print('a function')


def decorator(func):
    def wrapper():
        print(time.time())
        func()
    return wrapper

f = decorator(f1)
f()
```  

## 装饰器+语法糖

```python
import time                                                                                                                                                                                                 
def decorator(func):
    def wrapper():
        print(time.time())
        func()
    return wrapper
@decorator
def f1():
    print('a function')
#f = decorator(f1)
#f()    
f1()
```  

```python
import time                                                                                                                                                                                                  
def decorator1(func):
    def wrapper(*args):
        print(time.time())
        func(*args)
    return wrapper

@decorator1
def f1(func_name):
    print('a function:' + func_name)

@decorator1
def f2(func_name, func_name1):
    print('a function:' + func_name)
    print('a function:' + func_name1)
    
def f3(func_name, func_name1, **kw):
    print('a function:' + func_name)
    print('a function:' + func_name1)
    print(kw)

#f = decorator(f1)
#f()    
f1('123')
f2('123','2')
f3('123','2', a=1, b=2, c='321'
```  

```python
import time                                                                                                                                                                                                  
def decorator1(func):
    def wrapper(*args, **kw):
        print(time.time())
        func(*args, **kw)
    return wrapper
@decorator1
def f2(func_name, func_name1):
    print('a function:' + func_name)
    print('a function:' + func_name1)
@decorator1
def f3(func_name, func_name1, **kw):
    print('a function:' + func_name)
    print('a function:' + func_name1)
    print(kw)
f3('123','2', a=1, b=2, c='321')
```  





    

