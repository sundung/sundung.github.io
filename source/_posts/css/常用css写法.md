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
2. 多行文本溢出

```
overflow:hidden;
text-overflow:ellipsis;
display:-webkit-box;
-webkit-box-orient:vertical; /*设置对齐模式*/
-webkit-line-clamp:2; /*设置多行的行数*/

```
3. css3 动态计算高宽高

> height:calc(100vh - 12px);

解释: 
    1. calc:可以动态计算css的宽高,运算符左右两侧必须加 空格,否则计算就会失效
    2. 视口单位: vh vw 1vh = 1% 的视口高度 1vw = 1% 的视口宽度

4. 动画

```
    .discAnimation {
        animation: disc(动画名) 4s liner infinite;
        animation-delay:1s;
    }
    @keyframes: 设置动画帧

    1) from to 
    - 适用于简单动画,只有起始帧和结束帧
    - 北京 - 上海 直达
    2) 百分比
    - 多用于复杂的动画,动画不止两帧
    - 0% - 100% 可以任意拆分

    例如:
    @keyframes disc(动画名) {
        from {
            transform:rotate(0deg);
        }
        to {
            transform:rotate(360deg);
        }
    }
```