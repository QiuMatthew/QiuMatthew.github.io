---
title: Cpp-Primer-Plus-Ch1-Preliminaries
auther: yuran
date: 2021-11-19 21:30:02
categories:
    - 技术
    - C++
    - C++ Primer Plus
tags:
    - 技术
    - C++
    - C++ Primer Plus
---

## 1.4.2 编译和链接
### 2 Linux编译和链接
Linux最常用的编译器：g++
下面的命令将生成可执行文件`a.out`
```
g++ spiffy.cpp
```
要编译多个源文件，只需将他们全部放到命令行中即可：
```
g++ my.cxx precious.cxx
```
这将生成一个名为`a.out`的可执行文件和两个目标代码文件`my.o`和`precious.o`
如果接下来修改了某个源代码文件，如`my.cxx`，则可使用`my.cxx`和`precious.o`来重新编译:
```
g++ my.cxx precious.o
```
