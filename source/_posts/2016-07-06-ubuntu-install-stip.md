---
layout: post
title: "Install STIP Under Ubuntu 14.04"
date: 2016-07-06 23:49:27 +0800
comments: true
categories: Linux
---

#### 1. Install opencv using apt-get

```sh
sudo apt-get install libopencv-dev
```

<!--more-->

#### 2. Install ffmpeg using apt-get

```sh
sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next
sudo apt-get update
sudo apt-get install ffmpeg
```

#### 3. In step 1. opencv has been installed in /usr/lib/x86_64-linux-gnu/

```sh
cd /usr/lib/x86_64-linux-gnu/
ln -s  libopencv_core.so  libcxcore.so.2
ln -s  libopencv_imgproc.so  libcv.so.2
ln -s  libopencv_highgui.so libhighgui.so.2
ln -s  libopencv_ml.so libml.so.2
ln -s libopencv_video.so libcvaux.so.2
```

#### 4. Add library path

```sh
export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu
OR
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu' >> ~/.bashrc
```

#### 5. Test

```sh
cd <path/to/stip>
chmod +x ./bin/stip*
./bin/stipdet --help
```

All Done