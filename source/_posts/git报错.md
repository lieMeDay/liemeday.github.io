---
title: 提示Your branch is up-to-date with 'origin/master' 该怎么办
author: Born to the sun
top: false
cover: false
toc: false
mathjax: true
date: 2020-06-28 18:50:40
keywords:
summary: 提交提示Your branch is up-to-date with 'origin/master' 该怎么办
tags: [git]
categories: git
---
创建并切换到新分支
```
git checkout -b newbranch
```
然后将你的改动提交到新分支上
```
git add . 
git commit -m "new"
```
然后切换到主分支
```
git checkout master 
```
然后将新分支提交的改动合并到主分支上
```
git merge newbranch 
```
然后就可以push代码了
```
 git push -u origin master
```
最后还可以删除这个分支
```
git branch -D newbranch
```