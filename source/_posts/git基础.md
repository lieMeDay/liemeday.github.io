---
title: git基础使用
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-06-28 16:50:40
keywords:
summary: git基础命令
tags: [git]
categories: git
---
### 提交
``` git
git status  // 查看与上次提交的区别
git add xxx // 要提交的文件名 或 git add . 当前目录下所有内容
git commit -m "提交说明"
git push origin﻿ master  //提交到主分支
  注* 首次提交 git push -u origin master
```
### 分支
```git
git branch xxx //创建分支
git checkout xxx // 切换分支
git checkout -b xxx //创建并切换分支
 注* 分支提交时需先切换到分支
```
## 多人开发
先将自己的内容提交到分支上
### 合并时先切换到主分支
```git
git checkout master
```
### 合并分支
```git
git merge xxx
```
### 提交合并
```git
git push  ==>失败时
git pull 拉取在本地编辑器查看合并修改冲突
```
### 重新执行提交
```git
git branch -b xxx 删除分支
```

### 本地Git 与远程关系的绑定
```git
git remote -v 查看本地git 信息
git remote rm origin 删除本地仓库当前关联的远程仓库
git remote add origin 地址 =》重新添加绑定
注: 重新绑定后push提交时 git push -u origin master
```