---
layout: post
title: "Install Dense Trajectory Under MacOS 10.10"
date: 2016-07-06 23:43:20 +0800
comments: true
categories: Mac
---

#### 1. software:

```sh
download ffmpeg-0.11.1, OpenCV-2.4.2 and dense_trajectory_release_v1.2
```
<!--more-->

#### 2. Install ffmpeg:
```sh
cd ffmpeg-0.11.1
./configure
make install
```

#### 3. Install OpenCV-2.4.2:
```sh
cd OpenCV-2.4.2
cmake
make install
```

#### 4. Install Dense Trajectory:
```sh
change the source code by adding a line code
make
```

Done