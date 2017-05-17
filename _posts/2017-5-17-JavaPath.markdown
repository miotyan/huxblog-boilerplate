---
layout:     post
title:      "Java 路径与跳转"
subtitle:   "JavaWeb 各种跳转和绝对相对路径的总结"
date:       2015-09-22
author:     "Mio"
header-img: ""
tags:
    - Java EE
    - Web
    - 总结
---
### 各种相对路径的含义
- `/` 根据跳转方式不同而代表`服务器端的地址`或`客户端的地址`
- `./` 代表当前目录，效果等同于什么也不加
- `../` 代表当前文件所在目录的上级目录
- `../../` 代表当前文件所在目录的上级目录的上级目录
- 按上述两条依次类推

### 服务器端的地址
服务器端的地址指的是包含 web 应用名称的地址，即 `http://主机名：8080/app-name/`
### 客户端的地址
客户端地址指的是不包含 web 应用名称的地址，即 `http://主机名：8080/`,
所以在使用`/`时需要手动加上 web 应用名称，即 `http://主机名：8080/app-name/`

### 各种跳转的区别
- `<a>`标签
> 普通html超链接。客户端跳转
- form 表单提交
> html表单提交，客户端浏览器将表单内容交付给服务器。客户端跳转
- request.getRequestDispatcher(url).forward(request,response)
> 请求转发到指定URL,跳转页面的时候带着原来页面的request和response跳转，request对象始终存在，不会重新创建。是服务器端跳转。地址栏的地址保持不变
- response.sendRedirect(url)
> 重定向到指定URL，跳转到指定的URL地址后，上个页面（跳转之前的原来页面）中的请求全部结束，原request对象将会消亡，数据将会消失。紧接着，当前新页面会新建request对象，即产生新的request对象。是客户端跳转。地址栏的地址会改变
