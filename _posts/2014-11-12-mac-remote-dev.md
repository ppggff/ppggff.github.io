---
layout: post
title: Mac下远程Linux C开发
comments: True
---

# 目标

目标是Macbook取代公司的老旧Dell，第一步便是搭建可用的开发环境。
之前公司开发环境为：

 * Windows + Source Insight + Visual Studio
 * Linux + GCC + GDB

因为暂时不支持Mac下编译，同时也不能轻松使用Source Insight，
所以替换后的目标是：

 * Mac + emacs
 * Linux + GCC + GDB

# 问题

暂时有如下问题需要解决：

 1. Mac不支持编译
 1. 如何使用emacs替代Source Insight
 1. 本地Linux的开发环境
 1. 如何同步Mac和Linux下的代码
 1. emacs下调试
 1. 如何profile

# 解决

暂时主要关注开发环境和代码同步问题。

## 本地Linux的开发环境

采用虚拟机方案，目前采用VirtualBox，以后考虑其他。
为了减少依赖及更强的定制性，目前为手工安装Debian，而非使用vagrant。
记录如下要点：

 1. VBoxHeadless启动无头虚拟机，注意要关闭3D加速，否则会有段错误
 1. 在Mac上执行如下命令启用VirtualBox的共享文件夹的Symlink

~~~
VBoxManage setextradata 虚拟机名字 VBoxInternal2/SharedFoldersEnableSymlinksCreate/共享文件夹名字 1
~~~

貌似硬连接还有问题，不过似乎还没用到。


## 如何同步Mac和Linux下的代码

暂时考虑到两种方法：

 1. 虚拟机的共享文件夹
 1. rsync，可以参考[此文](http://peter.bourgon.org/blog/2011/04/27/remote-development-from-mac-to-linux.html)
