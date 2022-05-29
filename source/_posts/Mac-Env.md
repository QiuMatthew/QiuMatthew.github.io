---
title: Mac-Env
auther: yuran
date: 2022-05-11 00:53:57
categories:
tags:
---

# Start with Mac
第一次到实验室，拿到了实验室给准备的Mac  
于是要开始配置Mac了

# Homebrew
本科的时候听说Mac对开发者还挺友好的，而且Mac的terminal和Linux比较相似，那第一件事就是打开terminal  
一番ls/cd等无意义操作后，觉得首要事情是弄个包管理工具，搜索后发现homebrew用的比较多，Jo Ting也如此建议，英文互联网和中文互联网都有推荐，空白也附议  
于是敲定，就它了  
## Installation
进入官网，有自动提示的安装指令
` % /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" `
安装完毕后
` % brew -v `
```
Homebrew 3.4.10
```
说明安装成功  
## Wget
既然包管理安装好了，作为测试，用它来装个wget罢  
` % brew install wget `
安装完毕后  
` % wget -V `
注意是大写哟  
```
GNU Wget 1.21.3 built on darwin21.3.0
blablabla
```
说明安装成功  

# Git
想能在Win和Mac不同设备上共同用hexo编辑自己的博客，那显然要给Mac也整上Git  
直接去Git官网，发现官网也推荐使用homebrew下载安装
` % brew install git `
