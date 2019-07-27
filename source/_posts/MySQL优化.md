---
title: MySQL优化
date: 2019-07-24 15:59:20
categories:
- MySQL
tags:
- MySQL优化
---
## 优化Count  
1. 问题产生  
    使用Springboot JPA的分页查询的时候,会带上一个count(\*)语句,在count的数量在1400万左右的时候,耗时大概在20秒以上  
2. count性能对比  
    性能 : count(1) > count(id) > count(*)  

## like优化  
在做查询的时候,难免存在需要字符串模糊查询,数据量稍微大一点的话效率就很低的下,此时可以用前缀索引替代.  
