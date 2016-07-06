---
layout: post
title: "Mac 下安装 Python-OpenCV"
date: 2016-07-06 23:33:13 +0800
comments: true
categories: Mac
---

首先确保已经安装了Python

<!--more-->

- Mac 下可以直接使用 brew 来安装OpenCV，具体步骤如下：

``` sh
# add opencv
brew tap homebrew/science

# install opencv
brew install opencv
```

- 安装必要的python库

``` sh
pip install numpy
pip install matplotlib
```

- 测试是否安装成功

``` sh
import cv2
import numpy  np
matplotlib import pyplot  plt

img = cv2.imread('road.png', )
plt.imshow(img, cmap='gray', interpolation='bicubic')
plt.xticks([]), plt.yticks([]) # to hide tick values on X and Y axis
plt.show()
```

可参考这篇文章中的方法安装：[Install OpenCV On Mac](http://www.pyimagesearch.com/2015/06/15/install-opencv-3-0-and-python-2-7-on-osx/)