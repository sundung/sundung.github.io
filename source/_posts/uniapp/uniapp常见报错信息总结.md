---
title: uniapp常见报错信息总结
date: 2021-08-20 15:33:08
tags: uniapp
---

1. 问题1. App平台 v3 模式暂不支持在 js 文件中引用"static/iconfont/iconfont.css" 请改在 style 内引用

    解决办法:

    把main.js 引入的css 放到app.vue的style里
    /* 导入 iconfont 字体图标 */
    @import  'static/iconfont/iconfont.css';


2. 问题2. App 上 scroll-view 不能横向滚动

    解决办法:

    1. 必须加上 block 
    2. 样式必须加上 white-space: nowrap;  display: inline-block;

    具体见代码:

    ```
    <!-- 内容区域 -->
      <scroll-view class="recommendSongScroll" scroll-x='true'  enable-flex='true'>
       /* 必加*/  <block   v-for="(item,index) in recommendSong" :key="index">
             <view class="scrollItem">
               <image class="image" :src="item.picUrl" mode=""></image>
               <text>{{item.name}}</text>
             </view>
         </block>
       </scroll-view>

    样式

      // 内容区域
      .recommendSongScroll {
        margin-top: 20rpx;
        height: 300rpx;
        display: flex;
        white-space: nowrap;/* 必加*/
        .scrollItem {
          width: 200rpx;
          display: inline-block; /* 必加*/
          margin-right: 20rpx;
          .image {
            width: 200rpx;
            height: 200rpx;
            border-radius: 10rpx;
          }
          text {
            font-size: 26rpx;
            /* 多行文本溢出隐藏 省略号代替*/
              overflow: hidden;
              text-overflow: ellipsis;
              display: -webkit-box;
              -webkit-box-orient: vertical; /*设置对其模式*/
              -webkit-line-clamp: 2; /*设置多行的行数*/
          }
        }
      }
    }


    ```