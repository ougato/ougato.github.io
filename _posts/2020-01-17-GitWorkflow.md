---
layout: post
title: "Git简单使用流程"
date: 2019-11-21 02:29:34 +0800
categories: Learn
tags: Semver
author: ougato
mathjax: true
---

* content
{:toc}




# Git简单使用流程

|软件|系统|终端|版本|
|:--:|:--:|:--:|:--:|
|Git|macOS Mojava|iTerm|v2.22.0|

## 本地分支

* `feature` : **功能分支** 定义规则（`"feature-功能名"`），有新功能时，先切换到本地 *develop* 分支，再同步远程 *develop* 分支，在此基础上创建一个新的分支，命名为 *feature-xxx* 分支，进行开发，完成后合并回 *develop* 分支，可以选择保留还是删除 *feature-xxx* 分支，*feature* 分支不做远程提交，如果强制需要（两人维护同一个功能的情况）可以上传到远程分支，但功能完成后，记得删除之前提交的 *feature* 远程分支。

## 远程分支

* `develop` : **开发分支** *feature-xxx* 分支完成开发功能后，与 
* `release` : **发布分支** 是项目发布到 **生产环境** 中的最后一个校验分支，规定只允许，*develop* 的分支合并到 *release*，不允许其他的分支合并到 *release* 分支上。
* `hotfix` : **热修复分支** 下一个版本正在研发，线上的版本又出了问题，需要修复并快速更新上去时，找到需要修复的 *tag* 版本，合并到 *hotfix* 修复好并测试完成后，再合并到现在开发的 *develop* 分支和 *master* 分支，保证下个版本这个 bug 能被同步修复，再进行构建发布。
* `master` : **主分支** 用于阅览项目开发与合并的整个过程，规定只允许 *release* 和 *hotfix* 分支单向合并到 *master* 主分支，不允许从 *master* 逆向合并到任意分支上。

## Git 流程图

![git-model](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-01-17-Git/git-model.png)