---
layout: post
title: "在 Ubuntu 上用 apt-get 安装 opencv"
date: 2016-07-06 23:39:46 +0800
comments: true
categories: Linux
---

#### 1. 搜索与OPENCV相关的软件包：

``` sh
$ apt-cache search opencv
```
<!--more-->

#### 2. 安装这些软件包（用默认安装）

``` sh
$ sudo apt-get install XXX XXX XXX
```

####3. 查看安装好的（与OPENCV相关的库）

``` sh
$ pkg-config --cflags --libs opencv
```

#### 4. 写一个小例子

```cpp
#include <cv.h>
#include <highgui.h>
int main()
{ //请确定程序目录下有一张测试用的图片temp.png

    const char *fileName = "temp.png";

    const char *title = "Image" ;

    IplImage *image = cvLoadImage(fileName, CV_LOAD_IMAGE_COLOR);

    cvNamedWindow(title, CV_WINDOW_AUTOSIZE); cvShowImage(title, image);

    cvWaitKey(0);

    cvReleaseImage(&image);

    cvDestroyWindow(title); return 0;
}
```

#### 5. 编译与运行

``` sh
$ gcc test.c -o test `pkg-config --cflags --libs opencv`
$ ./test
```

一切搞定
