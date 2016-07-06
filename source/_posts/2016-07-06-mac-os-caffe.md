---
layout: post
title: "Mac OS X 10.10 安装 Caffe 教程"
date: 2016-07-06 23:29:02 +0800
comments: true
categories: Mac
---

详细安装步骤:

- Homebrew
1. 根据http://brew.sh/上面的说明安装Homebrew包管理器

<!--more-->

- Anaconda Python
1. 从https://store.continuum.io/cshop/anaconda/下载和安装Anaconda Python包（其中包括Caffe框架用到的hdf5）
2. export PATH=~/anaconda/bin:$PATH（将Anaconda的bin路径添加到PATH环境变量中）


- CUDA
1. 从https://developer.nvidia.com/cuda-downloads下载并安装CUDA 7.0（Caffe使用CUDA进行GPU加速计算）
2. 从http://www.nvidia.com/object/mac-driver-archive.html下载并安装最新的CUDA 独立驱动（CUDA安装包自带的驱动版本低）
3. export PATH=/Developer/NVIDIA/CUDA-7.0/bin:$PATH（将CUDA的bin路径添加到PATH环境变量中）
4. export DYLD_LIBRARY_PATH=/Developer/NVIDIA/CUDA-7.0/lib:$DYLD_LIBRARY_PATH（将CUDA库的路径添加到系统动态链接库搜索路径中）


- BLAS – Intel MKL
1. 由于Mac OS X操作系统自带的线性代数BLAS库存在一些不稳定的问题，因此我选择安装Intel MKL库。如果你是在校大学生，可以使用学校邮箱从https://software.intel.com/en-us/qualify-for-free-software/student页面申请Intel Parallel XE 2015安装包（后面不要忘记在Makefile.config中设置BLAS:=MKL）
2. 确保在安装Intel Parallel XE时选择每一个组件（因为缺省情况下不会安装MKL组件）
3. cd /opt/intel/mkl/lib/
4. sudo ln -s . /opt/intel/mkl/lib/intel64（因为在编译Caffe时Caffe会从MKL的intel64目录中去搜索MKL的库，但是在安装MKL后，MKL的lib目录下并没有intel64这个目录，所以需要建立一个intel64目录到lib目录的软链接）

- cuDNN
1. 从https://developer.nvidia.com/cudnn页面下载并安装cuDNN库（别忘了在Makefile.config中取消USE_CUDNN := 1的注释）
2. tar -xzvf cudnn-6.5-osx-v2.tgz
3. cd cudnn-6.5-osx-v2
4. sudo cp lib* /usr/local/cuda/lib（拷贝cuDNN的链接库文件）
5. sudo cp cudnn.h /usr/local/cuda/include/（拷贝cuDNN的头文件）

- 通过Homebrew安装依赖项
1. brew edit opencv
2.将下面两行（替换的原因是在编译Caffe的Python接口时让Caffe链接到Anaconda的Python库，而不是链接到系统的Python库）
args << “-DPYTHON#{py_ver}_LIBRARY=#{py_lib}/libpython2.7.#{dylib}”
args << “-DPYTHON#{py_ver}_INCLUDE_DIR=#{py_prefix}/include/python2.7”
替换为
args << “-DPYTHON_LIBRARY=#{py_prefix}/lib/libpython2.7.dylib”
args << “-DPYTHON_INCLUDE_DIR=#{py_prefix}/include/python2.7”
3. brew install –fresh -vd snappy leveldb gflags glog szip lmdb homebrew/science/opencv
4. brew install –build-from-source –with-python –fresh -vd protobuf（protobuf需要从源代码进行编译）
5. brew install –build-from-source –fresh -vd boost boost-python（boost需要从源代码进行编译）

- 从Github上面克隆Caffe的代码
1. git clone https://github.com/BVLC/caffe.git
2. cd caffe
3. cp Makefile.config.example Makefile.config

- 配置Makefile.config
1. 设置BLAS := mkl
2. 取消USE_CUDNN := 1注释
3. 检查并设置Python路径

- 设置环境变量
1. export DYLD_FALLBACK_LIBRARY_PATH=/usr/local/cuda/lib:$HOME/anaconda/lib:/usr/local/lib:/usr/lib:/opt/intel/composer_xe_2015.2.132/compiler/lib:/opt/intel/composer_xe_2015.2.132/mkl/lib

- 编译Caffe
1. make clean
2. make all
3. make test
4. make runtest
5. make pycaffe
6. make distribute

英文原文地址：[How to install Caffe on Mac OS X 10.10 for dummies](http://hoondy.com/2015/04/03/how-to-install-caffe-on-mac-os-x-10-10-for-dummies-like-me/)