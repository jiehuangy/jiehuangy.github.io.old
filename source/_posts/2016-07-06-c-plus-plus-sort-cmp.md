---
layout: post
title: "C++ sort 的比较函数写法"
date: 2016-07-06 19:33:30 +0800
comments: true
categories: c++
---

定义排序函数：

### 方法1：声明外部比较函数

``` c++
bool Less(const Student& s1, const Student& s2)
{
    return s1.name < s2.name; //从小到大排序
}
std::sort(sutVector.begin(), stuVector.end(), Less);
```
<!--more-->

注意：比较函数必须写在类外部（全局区域）或声明为静态函数

当comp作为类的成员函数时，默认拥有一个this指针，这样和sort函数所需要使用的排序函数类型不一样。

否则，会出现错误

### 方法2：重载类的比较运算符

``` c++
bool operator<(const Student& s1, const Student& s2)
{
    return s1.name < s2.name; //从小到大排序
}
std::sort(sutVector.begin(), stuVector.end());
```

### 方法3：声明比较类

```c++
struct Less
{
    bool operator()(const Student& s1, const Student& s2)
    {
        return s1.name < s2.name; //从小到大排序
    }
};

std::sort(sutVector.begin(), stuVector.end(), Less());
```

