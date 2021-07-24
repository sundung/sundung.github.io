---
title: 常用css写法
date: 2021-07-23 19:56:23
tags: css
---

## 常用css用法总结:

1. 单行文本溢出,省略号(...)代替

```
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;

```
2.多行文本溢出

```
overflow:hidden;
text-overflow:ellipsis;
display:-webkit-box;
-webkit-box-orient:vertical; /*设置对齐模式*/
-webkit-line-clamp:2; /*设置多行的行数*/

```