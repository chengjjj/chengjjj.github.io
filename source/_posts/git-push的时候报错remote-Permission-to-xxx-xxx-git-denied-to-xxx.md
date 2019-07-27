---
title: 'git push的时候报错remote: Permission to xxx/xxx.git denied to xxx.'
date: 2019-07-27 17:56:44
categories:
- Git
tags:
- 问题
---
## 问题产生  
当push代码的时候出现***Permission***问题  

## 问题原因  
看报错remote: Permission to chengjjj/xxx.github.io.git denied to xxx.  
应该是本地git配置和自己仓库配置不一致导致的。  
但是自己再三核实的git配置，确保配置程池  
然后看是windows系统的控制面板中的凭据管理记录了另一个github账号  
需要在控制面板 -> 所有控制面板中更改原来的github配置  
此处应有图片  

