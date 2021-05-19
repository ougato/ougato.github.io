---
layout: post
title: "Cocos Creator 热更新"
date: 2020-10-17 00:46:22 +0800
categories: Cocos Creator
tags: HotUpdate
author: ougato
mathjax: true
---

* content
{:toc}




# Cocos Creator 热更新

* Cocos Creator 版本 - **2.4.3**
* Cocos Dashboard 版本 - **1.0.10.2110**
* 脚本语言 - **Typescript**
* 系统环境 - **Windows 10**

# 1. 生成 manifest 的文件

* version.manifest
* project.manifest

```
node .\version_generator.js -v 1.0.0 -u http://192.168.0.107:9000/remote-assets/ -s ..\..\build\jsb-default\ -d ..\..\assets\res\update\
```

> 判断本次是否更新资源的前提是，每次游戏启动都要去网络请求一个版本号，与本地的版本号来做对比，考虑是每次就要保证请求的这个数据量尽量的小。但是随着你的项目越来越大，数据量小的请求文件里面，就无法满足你想要的数据，你每增加一个新资源到工程里，请求的文件里就会增加 1 条 新资源的 MD5 字符串，使得请求文件越来越大。于是就有了一个 version.manifest 来当做第一次请求文件，这里面只包含了相对恒定的 3 个字段数据。

* `remoteManifestUrl` 资源服的 project.manifest 地址
* `remoteVersionUrl` 资源服的 version.manifest 地址
* `version` 资源服的版本号

> 第一次请求远程文件 version.manifest，与本地版本号对比，如果远程版本号大于本地的版本号，就去第二次请求远程文件 project.manifest，这是一个包含详细资源的 MD5 文件，这样就不用每次上来都请求一次大文件。

# 2. 创建热更新脚本文件

``` typescript
// UpdateDefine.ts

enum UpdateType {
    // 不更新
    NOT = 0,
    // 静默更新（小版本更新时，在 WIFI 情况下静默更新）
    QUIET,
    // 提示更新（小版本更新时，在 4G 情况下提示用户需要更新文件大小，让用户决定是否继续更新）
    PROMPT,
    // 商店更新（大版本更新时，用户跳转到商店更新）
    STORE,
}
```

``` typescript
// UpdateInterface.ts

interface CheckResult {
    // 本次更新类型
    type: UpdateDefine.UpdateType,
    // 更新字节数
    downloadBytes?: number,
}
```

``` typescript
// UpdateNative.ts

/**
 * 检测更新
 * @param url {string} version.manifest 更新文件在本地原生中的存储路径
 * @return {Promise<UpdateInterface.CheckResult>} 检测结果
 */
public async check(url: string): Promise<UpdateInterface.CheckResult>;

/**
 * 更新最新资源文件
 * @return {Promise<void>}
 */
public async update(): Promise<void>;

/**
 * 重试更新失败后的资源文件
 * @return {Promise<void>}
 */
public async retry(): Promise<void>;
```

## 相关帮助