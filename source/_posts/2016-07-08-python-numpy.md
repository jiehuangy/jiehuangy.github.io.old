---
layout: post
title: "Numpy Tutorial"
date: 2016-07-08 16:32:29 +0800
comments: true
categories: Python
---
- list element with functor item
{:toc}

NumPy 提供了两种基本的对象：ndarray 和 ufunc 。 ndarray 是存储单一数据类型的多维数组，而 ufunc 则是对数组进行处理的函数.

<!--more-->

## 1. ndarray 对象

### 1.1 创建数组
- 通过 $array()$ 函数传递 Python 的`序列对象`创建数组

``` python
>>> a = np.array([[1,2,3],[4,5,6]])
array([[1, 2, 3],
       [4, 5, 6]])
```

- 通过函数 $arange(start, end, step)$ 和 $linspace(start, end, nums)$ 创建等差数组

``` python
>>> a = np.arange(0, 1, 0.1)
array([ 0. ,  0.1,  0.2,  0.3,  0.4,  0.5,  0.6,  0.7,  0.8,  0.9])
>>> b = np.linspace(0, 1, 10)
array([ 0.        ,  0.11111111,  0.22222222,  0.33333333,  0.44444444,
        0.55555556,  0.66666667,  0.77777778,  0.88888889,  1.        ])
```
 
- 通过函数 $zeros(), ones(), empty()$ 创建指定形状和类型的数组

``` python
>>> a = np.zeros([2,3], np.float)
array([[ 0.,  0.,  0.],
       [ 0.,  0.,  0.]])
```

### 1.2 存取元素

单个元素：
NumPy 采用元祖 tuple 作为数组的下标。由于元祖的语法只要使用逗号分隔元素即可，所以 a[1,2] 和 a[(1,2)]完全相同

多个元素:

- 通过 **切片获取** 的新数组是原始数组的一个视图，它与原始数组共享同一块数据存储空间
- 与使用切片不同，通过 **整数列表，整数数组，布尔数组** 作为下标得到的数组不和原始数组共享数据

## 2. ufunc 运算
ufunc 是 universal function 的缩写，它能对数组中每个元素进行操作。 Numpy 内置的 ufunc 函数都是 C 语言实现的，计算速度快。包括`四则运算`，`比较运算`和`逻辑运算`。


## 3. 广播
当使用 ufunc 函数对两个数组进行计算时，如果形状不同，会进行如下广播。

1. 向维数最多的数组看齐，shape 属性中不足的部分都通过在前面加 1 补齐。
2. 输出数组的 shape 是输入数组 shape 在各个轴上的最大值。
3. 如果输入数组的某个轴长度为 1 或与输入数组对应轴的长度相同，这个数组就能够用来计算，否则出错。
4. 当输入数组的某个轴长度为 1 时，沿此轴运算时都用此轴上的第一组值。

## 4. 文件存取

### 二进制文件
$load()$, $save()$ 用 Numpy 专用的二进制格式保存数据，它们会自动处理元素类型和形状。可用使用 $savez()$ 将多个数组保存到一个文件中。

``` python
>>> np.save('a.npy', a)
>>> c = np.load('a.npy')
```

$save()$ 和 $savez()$ 输出的二进制文件有特殊的格式，难用其他语言程序读入。
{:.warning} 

### 文本文件
$savetxt()$ 和 $loadtxt()$ 可以读写保存一维和二维数组的文本文件

``` python
>>> np.savetxt('a.txt', a)
>>> c = np.loadtxt('a.txt')
```