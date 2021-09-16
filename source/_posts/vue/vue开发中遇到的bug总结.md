---
title: vue开发中遇到的bug总结
date: 2021-08-26 16:00:13
tags: vue
---

1. 问题:1. vue-router 使用 addRoutes 动态添加路由跳转后页面刷新空白问题

```
问题描述：
在做菜单权限的时候，使用了 router.addRoutes() 方法把不同权限获取到的路由表动态的添加到路由里面去。菜单正常展示，在点击菜单跳转之后，浏览器刷新一下，页面没有跳转到 404 页面，而是变成了空白。

问题原因：
addRoutes 和 vuex 一样，在浏览器刷新后数据会丢失，因为刷新页面 Vue 会重新实例化，路由也会恢复到初始路由。

解决方案：
在页面刷新之后重新获取到通过权限修改后的路由表，然后再次使用 router.addRoutes() 方法将新路由表动态添加到路由里面去就可以了。

方法一：在 App.vue 文件的 created 生命周期里面执行 router.addRoutes() 这一操作。
方法二：利用 vuex 页面刷新数据丢失特性，在路由守卫里判断 vuex 存储的路由表数组长度是否为 0 ，为 0 则表明当前有刷新页面操作。这个时候从 localStorage 里重新获取一下有权限的路由表，然后执行 router.addRoutes() 操作。（这个方法是同事提供）


```

2. 项目开发中遇到监听页面隐藏的需求,结果出现了问题

    1.描述:当很多页面都使用了监听页面隐藏的事件时候,一个页面隐藏,会触发所有加载过得页面

    解决方案

    ```
        mounted() {  
            document.addEventListener('visibilitychange', this.handleVisiable)  
        },  
        destroyed() {  
            document.removeEventListener('visibilitychange', this.handleVisiable)  
        },  
        methods: {  
            handleVisiable(e) {  
            if (e.target.visibilityState === 'visible') {  
                // 要执行的方法
            }  
        }

    ```