---
layout: post
title: Git使用下出现的问题
description: "Git使用下出现的问题"
modified: 2018-09-12
---

<img src="http://i.imgur.com/nQFuJBO.jpg">

<b>1. 莫名奇妙出现没有权限的问题</b> <br><br>
```
Unable to negotiate with xxx.xxx.xxx.xxx port 19428: no matching key exchange method found. Their offer: diffie-hellman-group1-sha1
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
 1. 根据提示是不同的group sha1，所以直接输入以下命令
    ```
    $export GIT_SSH_COMMAND='ssh -o KexAlgorithms=+diffie-hellman-group1-sha1'
    ```
    但这样不是根本解决问题的方法
 2. 修改ssh config文件
    ```
    sudo gedit /etc/ssh/ssh_config 
    # 在host下加入 
    KexAlgorithms=+diffie-hellman-group1-sha1
    ```
 3. 还是修改config，但是在用户目录下的.ssh文件夹新建要给config文件，在其中输入
    ```
    Host *
        KexAlgorithms +diffie-hellman-group1-sha1
    ```


<br>

<div class="fb-comments" data-href="https://www.facebook.com/photo.php?fbid=426800044160287" data-width="650" data-numposts="3" data-colorscheme="light"></div>
