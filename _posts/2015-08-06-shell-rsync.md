---
layout: post
category: "shell"
title: "Shell拷贝文件"
tags: ["shell"]
---

解决方法如下：

```shell
rsync --exclude=.svn $SRC_DIR/ $DST_DIR/ -r
```

> -r, --recursive 对子目录以递归模式处理。    
> -v, --verbose 详细模式输出。