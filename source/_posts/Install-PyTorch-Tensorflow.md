---
title: Install-PyTorch-Tensorflow
auther: yuran
date: 2021-10-06 20:06:27
categories:
    - 技术
    - DeepLearning
tags:
    - 技术
    - PyTorch
    - Tensorflow
---

## Install PyTorch
到PyTorch官网，GetStarted页面，选择自己的需求，会自动生成需要执行的命令，我这里是

|标签|选项|
|----|----|
|版本|Stable|
|系统|Linux|
|包管理工具|Conda|
|语言|Python|
|计算平台|CUDA10.2|

自动生成的命令如下
```
>>> conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch
```

<!--more-->

## Install Tensorflow
使用 Python 的 pip 软件包管理器安装 TensorFlow
需要最新版本的 pip
```
>>> pip install --upgrade pip
```