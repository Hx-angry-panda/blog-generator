---
title: git入门
date: 2019-01-24 16:18:19
tags:
---
每个程序员都要会用git = git很重要 =必须熟练掌握git

先介绍三个git入门的命令

1. git init  ：
初始化 Git 仓库，会生成一个. git 目录，所有 Git 需要的数据和资源都存放在这个目录中。如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪
![init用法](myBlog/img/git init用法.png)

2. git add : 
可将该文件添加到缓存
新项目中，添加所有文件很普遍，我们可以使用 git add . 命令来添加当前项目的所有文件。
![add用法](myBlog/img/git add用法.png)

3. git commit -v
执行 git commit 将缓存区内容添加到仓库中。
git commit -v   提交时显示所有diff信息      diff用来比较两个文本文件的差异
使用 git commit -m "信息" 将你  git add 过的内容「正式提交」到本地仓库（.git就是本地仓库），并添加一些注释信息，方便日后查阅
![commit用法](myBlog/img/git commit用法.png)