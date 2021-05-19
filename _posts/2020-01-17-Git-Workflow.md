---
layout: post
title: "Git 简单使用流程"
date: 2020-01-17 12:24:05 +0800
categories: Git
tags: 
author: ougato
mathjax: true
---

* content
{:toc}




# Git 简单使用流程

## 本地分支

* `master` : **主分支** 保持与远程 *master* 分支同步，合并稳定的本地 *release* 分支，进行[版本控制](https://ougato.github.io/2019/11/20/Semver/) tag 封订，为了今后线上版本出现问题时，方便查找稳定的版本号，进行热修复。
* `release` : **发布分支** 用于本地 *develop* 分支把本期功能完成后，合并到该分支内，进行测试封版，并提交到远程 *release* 分支的过渡做用。
* `develop` : **开发分支** 与远程 *develop* 分支同步，保持该分支一直都是最新状态，因为远程 *develop* 分支在团队协作时，提交比较频繁；拉取的时候尽量使用 `git pull --rebase` 来拉取最新的资源，避免拉取冲突后产生多余的提交节点和分支线性异常；该分支用于 *feature* 分支做新功能开发时使用。
* `feature` : **功能分支** 由 *develop* 分支分叉出来的一组分支，用于开发新功能，完成后合并回本地 *develop* 分支，在合并时尽量使用 `git merge --no-ff` 模式，这样合并回去的所有提交内容才会被显示在线性图表内；该分支命名规则 `"feature-功能名"`。
* `hotfix` : **热修复分支** 由 *master* 分支中的 tag 分叉出来的一组分支，用于线上功能出现严重 bug 时，在该分支修复后，合并回 *master* 分支，并同步合并到 *develop* 分支，保证下个版本正常发布时，也同步修复了该 bug。


## 远程分支

* `master` : **主分支** 用于在发布到线上资源，Jenkins 拉取并构建的独立分支。
* `release` : **发布分支** 是项目发布到生产环境中的最后一个校验分支，规定只允许，*develop* 的分支合并到 *release*，不允许其他的分支合并到 *release* 分支上，也属于 Jenkins 拉取并构建的独立分支。
* `develop` : **开发分支** 用于 bug 修复与功能开发使用，Jenkins 拉取并构建的独立分支。
* `hotfix` : **热修复分支** 该分支在正常流程中不会存在于远程分支内，我在此保留该远程分支是为了 *master* 分支的严重 bug 被修复后，在 Jenkins 上构建时，没有独立远程分支，供测试人员做回归测试。


## Git 流程图

![git-model](https://raw.githubusercontent.com/ougato/ougato.github.io/master/_image/git/git-model.png)