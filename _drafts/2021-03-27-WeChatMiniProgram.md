---
layout: post
title: "微信小程序"
date: 2019-03-27 02:28:18 +0800
categories: Wechat
tags: MiniProgram
author: ougato
mathjax: true
---

* content
{:toc}




# 微信小程序

## wxss

### 判断是否显示

```css
<view wx:if="{{布尔类型}}">

</view>
```

### 循环

```css
<block wx:for="{{数据列表 数组类型}}" wx:for-item="单项对象" wx:for-index="循环下标 数字类型">
    
</block>
```

### 绑定

#### 不可穿透
catchtap

#### 可穿透
bindtap