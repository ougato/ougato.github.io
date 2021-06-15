---
layout: post
title: "客户端框架设计"
date: 2020-06-16 01:16:51 +0800
categories: Cocos Creator
tags: 
author: ougato
mathjax: true
---

* content
{:toc}




# 客户端框架设计

* 热更新
    * 主包更新
	* 子包更新（AssetBundle）

* 管理器
	* 界面管理器（UIManager）
	* 声音管理器（AudioManager）
		* 音乐播放器（MusicPlayer）
		* 音效播放器（SoundPlayer）
	* 事件管理器（EventManager）
	* 网络管理器（NetworkManager）
		* Http
		* WebSocket
		* Socket
	* 动画管理器（AnimationManager）
		* 帧播放器（FramePlayer）
		* 骨骼播放器（SpinePlayer）
		* 缓动播放器（TweenPlayer）
		* 龙骨播放器（DragonBonePlayer）
	* 更新管理器（UpdateManager）
	* 日志管理器（LogManager）
	* 资源管理器（ResouceManager）
		* 缓存器（Buffer）
		* 加载器（Loader）

* 本地存储
	* 数据库
	* 硬盘库
    
* 多语言

* 工具

* 配置

* 定义

* 接口
