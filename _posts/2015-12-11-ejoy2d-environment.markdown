---
layout:     post
title:      Ejoy2d环境搭建爬坑指南
subtitle:   MacOSX版本
author:     "WZ"
header-img: "img/post-bg-2015.jpg"
tags:
    - 折腾
---

今天在 Github 上整理自己 star 的项目，再次翻到了 ejoy2d 这个项目，它是一款云风发起的开源 2d 游戏引擎，他自己的公司正在用这款引擎进行商业开发，据说这款c写的引擎能更好的和 lua 结合，还没有细看引擎的代码，但是相比 cocos2d-x 引擎，ejoy2d 的代码文件要少得多，给我一种小巧简洁的感觉。肯定要抽时间读一读它的代码，应该能更好的学习游戏引擎开发 :)

为什么要说“又”翻到了这个项目呢？因为第一次接触到这个项目的时候就尝试着想跑一下它的 example 看看效果，但是，当时刚开始用 Mac，没有成功的配置好它的运行环境。这次想再试试，让项目跑起来，也开始研究学习下这个引擎代码。

根据当前版本的 README：

> For Mac OS ,
>
> * Install glfw3
> * Install freetype 2
> * make or make macosx
> * ./ej2d examples/ex01.lua to test

用 [homebrew](http://brew.sh) 安装了 glfw3 和 freetype2 之后，make 一下，提示找不到 GLFW/glfw3.h 头文件（window.c中引用）和 ft2build.h 头文件（winfont.c中引用）。多次确认已经安装了这两个库之后，又去网上查了下 Makefile 文件的写法，发现文件里没有配置相应的路径，修改之后，又报出链接 glfw3 错误，一大堆 `ld: symbols not found for architecture x86_64` 错误，就没有再纠结 Makefile 了，还是直接跑 mac/example/example.xcodeproj，打开项目，已经看到代码里找不到 ft2build.h 文件了，在 Xcode 下配置一下头文件搜索路径，然后查看了下库文件搜索路径，确认都正确了之后，再次 run 一次，报出了同样的链接 glfw3 错误，一开始查了很多 `ld: symbols not found for architecture x86_64` 错误的原因，一直都没有解决问题，直到搜索其他的错误信息，找到了[这篇帖子](http://stackoverflow.com/questions/18391487/compiling-with-glfw3-linker-errors-undefined-reference)，和我的问题一样，我按照这上面的做法，添加了3个系统库依赖之后，模拟器成功的运行起来，终于让我看到了游戏界面。
