---
title: git 上传node_modules
author: Born to the sun
top: false
cover: false
toc: false
mathjax: true
date: 2020-06-29 18:50:40
keywords:
# summary: git 上传node_modules
tags: [git]
categories: git
---
首先，在项目目录下打开git Bash Here，输入命令：touch .gitignore

完成后项目中会出现一个后缀名“.gitignore”为的文件

打开该文件，生成文件的时候已经自动配置好了，接下来提交代码的时候就可以放心提交了，不会再将node_modules文件夹提交上去
```
node_modules/   表示过滤这个文件夹
*.zip   过滤zip后缀文件
demo.html   过滤该文件
```
node_modules一般过大，不适合提交git，建议后期还是<font color=blue> install </font>比较好