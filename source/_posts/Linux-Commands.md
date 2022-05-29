---
title: Linux-Commands
auther: yuran
date: 2021-11-11 16:38:17
categories:
	- 技术
	- Linux
tags:
	- 技术
	- Linux
---

## Find command

### Find files with modified time
```Shell
>>> find ./Unclassified/ -newermt '2015-3-1' ! -newermt '2015-4-1' -exec mv {} ./2015-3/ \;
```

## Variable

### Cut strings
```Shell
>>> var=20210515.png
>>> echo $var
20210515.png
>>> echo ${var#*.}
png
>>> echo ${var##*1}
5.png
>>> echo ${var%.*}
20210515
>>> echo ${var%%1*}
202
```
