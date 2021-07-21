---
layout: post
title: "HTTP数据报结构"
date: 2020-02-02 01:05:31 +0800
categories: Learn
tags: Lisp
author: ougato
mathjax: true
---

* content
{:toc}




# HTTP 请求/响应 数据报结构

## 请求报文

![请求报文结构](https://raw.githubusercontent.com/ougato/ougato.github.io/master/_image/http/http-request-datagram.png)

### 请求行

#### 方法

参考资料
* [W3C](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)（英文）

##### GET
* 作用
    * 仅用于向服务器**索要数据**，对服务器的数据资源不会进行修改，不会产生副作用，对服务器来说是`安全`的，也是`幂等`的。
* 安全
    * 这里安全是指不会对服务器产生数据的影响，就像查询数据库一样，不会增加、删除或修改数据库内的数据。
* 幂等
    * 是数学或计算机学概念，常见于抽象代数中，指无论 GET 一次或多次，返回的数据都应该是一样的，和求绝对值（abs）的方法一样；但是在实际生活中，比如，请求一个新闻的数据，虽然每次都返回的是不同的新闻数据列表，该操作也可认为是幂等的，因为它总返回的是新闻数据列表。

##### POST
* 作用
    * 用于向服务器**提交数据**，包括**上传资源**，并获取数据返回，可能对服务器上的资源数据造成修改影响。

##### HEAD
* 作用
    * 类似于 GET 方法，但是它仅只能向服务器索要**响应头**的数据，返回中并没有具体的响应体数据。

##### PUT
* 作用
    * 用于**完整的资源更新**到服务器，仅是对已有的资源进行更新，是`幂等的`。

##### DELETE
* 作用
    * 告诉服务器**删除文件**，通过 Request-URI 所标识的资源进行删除。

##### CONNECT
* 作用
    * 仅用于代理的请求中，HTTP/1.1 协议中预留给，能够将连接改为通道方式的代理服务器。
* 参考资料
    * [joji.me](https://www.joji.me/zh-cn/blog/the-http-connect-tunnel)

##### OPTIONS
* 作用
    * 用于**获取服务器所支持的请求方法**，成功后，则它会在 HTTP 请求头中包含一个字段名为 Allow，值是所有支持的请求方法。

##### TRACE
* 作用
    * 请求服务器回显服务器收到的请求信息，该方法主要用于HTTP请求的**测试或诊断**。

##### PATCH
* 作用
    * 与 PUT 请求类似，该方法细分了更新资源的功能，用于**资源的部分更新**，当资源不存在时，创建一个新资源。

##### MOVE
* 作用
    * 请求服务器将指定的页面移到另一个网络地址。

##### COPY
* 作用
    * 请求服务器将指定的页面拷贝到另一个网络地址。

##### LINK
* 作用
    * 请求服务器建立链接关系。

##### UNLINK
* 作用
    * 断开链接关系。

##### WRAPPED
* 作用
    * 允许客户端发送经过封装的请求。

##### Extension-mothed	
* 作用
    * 在不改动协议的前提下，可增加另外的方法。


#### URL
* 全称
    * Uniform Resource Locator
    * 统一资源定位器
* 组成
    * scheme : Internet 服务的类型，常见（http / https / web / ftp）。
    * host : 主机前缀，默认是 **www**。
    * domain : 域名，是注册于Internet上用于绑定IP的别名，便于记住。
    * port : 服务器端对外开放的端口，默认 HTTP 请求端口是 80，该端口可以被忽略。
    * path : 路径，远程服务器上的文件资源目录，默认是网站的根目录，该路径可以被忽略。
    * filename : 远程服务器上的文件资源名称，省略此文件，通常被定位到index.html页面文件。
* 例子
    * `https://www.google.com/`
    * `https://stackoverflow.com/`

#### 协议

#### 版本

### 请求头
* 媒体类型 MIME（Multipurpose Internet Mail Extensions），

#### 字段名:值

### 空行

### 请求体

## 响应报文

### 响应行

#### 协议

#### 版本

#### 状态码

#### 状态描述

### 响应头

#### 字段名:值

### 空行

### 响应体

