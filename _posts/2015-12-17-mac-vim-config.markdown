---
layout:     post
title:      MacVim配置
subtitle:   spf13-vim
author:     "WZ"
header-img: "img/post-bg-2015.jpg"
tags:
    - 折腾
    - vim
---

在两年前，我就已经开始在用 vim 了，也是在各种帖子上看到其他人把它奉为神器，又说它上手比较难，引起了我的兴趣，那时候是在 windows 系统上，我开始慢慢摸索怎么安装，怎么配置 .vimrc 文件，最后……熟练的掌握了最基本的用法＝。＝!!

那时的我，每次换电脑，都要重新下载、配置一遍 vim，自己其实觉得还是挺麻烦的，虽然我用的插件并不多，终于在上次换公司的时候，跟随新同事一起用起了 sublime。

这次为什么又回到了 vim 呢？因为在现在这家公司都是用 Mac 进行开发。都说Mac是把图形界面和命令行结合得最好的操作系统，像vim这样的编辑方式感觉更酷一些，而且通过homebrew安装软件又是那么方便，在网上又搜了下vim的自动化配置，看到了`spf13/spf13-vim`，心想就折腾一下吧，说不定有惊喜呢？

按照文档上的要求来一步步安装。

为了让[neocomplete](https://github.com/Shougo/neocomplete.vim#requirements)插件能正常工作，我们首先得安装支持lua的vim，我用homebrew安装了MacVim：

```
brew install macvim --with-cscope --with-lua
brew linkapps macvim
```

安装完了之后，可以打开macvim，在normal模式下输入`:echo has("lua")`来测试lua是否已经支持了，如果返回`1`，则表示成功了。

接下来直接输入安装命令：

```
sh <(curl https://j.mp/spf13-vim3 -L)
```

再把它升级到最新版本：

```
curl https://j.mp/spf13-vim3 -L -o - | sh
```

这个过程的时间会有点长，足够喝杯茶慢慢等。整个安装好了之后，打开macvim会看到如下配色的界面：![vim](/img/in-post/2015/12/vim1.png)

现在基本的使用已经没有问题了。

spf13-vim的vimrc配置挺模块化的。

打开之前用sublime编辑的文件，会看到tab键会变成带箭头有底色的色块。![tab](/img/in-post/2015/12/vim2.png)


在 vim 事件中，全局搜索一直是让我感到头疼的问题，这次新装的 `spf13/spf13-vim` 中好像也没有安装搜索相关的插件，又去网上继续找，看到说 `ctrlsf` 这个插件好像不错，遂上去一试，
