---
layout: post
title: "Chrome浏览器跨域"
date: 2019-04-09 01:21:26 +0800
categories: Chrome
tags: CrossOrigin
author: ougato
mathjax: true
---

* content
{:toc}




# Cross-Origin

## 参数说明

| 序号 | 参数 | 说明 | 
| :---: | :---: | :---: | 
| 1 | --allow-outdated-plugins | 不停用过期的插件。 | 
| 2 | --allow-running-insecure-content | 默认情况下，https 页面不允许从 http 链接引用 javascript/css/plug-ins。添加这一参数会放行这些内容。 | 
| 3 | --allow-scripting-gallery | 允许拓展脚本在官方应用中心生效。默认情况下，出于安全因素考虑这些脚本都会被阻止。 | 
| 4 | --disable-accelerated-2d-canvas | 停用 GPU 加速二维画布。 | 
| 5 | --disable-accelerated-video | 停用 GPU 加速视频。 | 
| 6 | --disable-dart | 停用 Dart。 | 
| 7 | --disable-desktop-notifications | 禁用桌面通知，在 Windows 中桌面通知默认是启用的。 | 
| 8 | --disable-extensions | 禁用拓展。 | 
| 9 | --disable-file-system | 停用 FileSystem API。（注意一些拓展如 Adblock Plus for Google Chrome™ 依赖此 API 运行） | 
| 10 | --disable-java | 停用 Java。 | 
| 11 | --disable-local-storage | 禁用 LocalStorage。 | 
| 12 | --disable-preconnect | 停用 TCP/IP 预连接。 | 
| 13 | --disable-remote-fonts | 关闭远程字体支持。SVG 中字体不受此参数影响。 | 
| 14 | --disable-speech-input | 停用语音输入。 | 
| 15 | --disable-sync | 停用同步功能。 | 
| 16 | --disable-ssl3 | 停用 SSL v3。 | 
| 17 | --disable-web-security | 不强制遵守同源策略，供网站开发人员测试站点使用。 | 
| 18 | --disk-cache-dir | 将缓存设置在给定的路径。 | 
| 19 | --disk-cache-size | 设置缓存大小上限，以字节为单位。 | 
| 20 | --dns-prefetch-disable | 停用DNS预读。 | 
| 21 | --enable-print-preview | 启用打印预览。 | 
| 22 | --extensions-update-frequency | 设定拓展自动更新频率，以秒为单位。 | 
| 23 | --incognito | 让浏览器直接以隐身模式启动。 | 
| 24 | --keep-alive-for-test | 最后一个标签关闭后仍保持浏览器进程。（某种意义上可以提高热启动速度，不过你最好得有充足的内存） | 
| 25 | --kiosk | 启用kiosk模式。（一种类似于全屏的浏览模式） | 
| 26 | --lang | 使用指定的语言。 | 
| 27 | --no-displaying-insecure-content | 默认情况下，https 页面允许从 http 链接引用图片/字体/框架。添加这一参数会阻止这些内容。 | 
| 28 | --no-first-run | 跳过 Chromium 首次运行检查。 | 
| 29 | --no-referrers | 不发送 Http-Referer 头。 | 
| 30 | --no-sandbox | 彻底停用沙箱。 | 
| 31 | --no-startup-window | 启动时不建立窗口。 | 
| 32 | --proxy-pac-url | 使用给定 URL 的 pac 代理脚本。（也可以使用本地文件，如 --proxy-pac-url="file:\\c:\proxy.pac"） | 
| 33 | --proxy-server | 使用给定的代理服务器，这个参数只对 http 和 https 有效。（例如 --proxy-server=127.0.0.1:8087 ） | 
| 34 | --show-component-extension-options | 让自带的拓展组件显示在 chrome://settings/extensions 里。（目前有一个 "Bookmark Manager 0.1"） | 
| 35 | --single-process | 以单进程模式运行 Chromium。（启动时浏览器会给出不安全警告） | 
| 36 | --skip-gpu-data-loading | 跳过启动时的 GPU 信息收集、黑名单读取与黑名单自动更新，这样一来，所有的 GPU 功能都可供使用，并且 about:gpu 页面会显示空白。此参数仅供测试使用。 | 
| 37 | --start-maximized | 启动时最大化。 | 
| 38 | --touch-optimized-ui | 使用对触屏更友好的用户界面。（目前来看似乎只是把一些字体放大了） | 
| 39 | --user-agent | 使用给定的 User-Agent 字符串。 | 

## Mac

### 1.创建存储跨域数据文件夹

```
// 打开控制台 命令创建文件夹
mkdir -p $HOME/Data/Chrome/CORS/
```

![for-mac-1](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2019-04-09-ChromeCrossOrigin/for-mac-1.png)

### 2.命令打开Chrome浏览器

```
open -n /Applications/Google\ Chrome.app/ --args --disable-web-security --user-data-dir=$HOME/Data/Chrome/CORS/
```

![for-mac-2](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2019-04-09-ChromeCrossOrigin/for-mac-2.png)

### 3.选择是否 默认浏览器 / 反馈

![for-mac-3](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2019-04-09-ChromeCrossOrigin/for-mac-3.png)

### 4.完成跨域

![for-mac-4](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2019-04-09-ChromeCrossOrigin/for-mac-4.png)

---

## Windows


### 1.创建存储跨域数据文件夹

```
// 打开控制台 命令创建文件夹
mkdir %USERPROFILE%\Data\Chrome\CORS\
```

![for-windows-1](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2019-04-09-ChromeCrossOrigin/for-windows-1.png)

### 2.命令打开Chrome浏览器

```
"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" --disable-web-security --user-data-dir=%USERPROFILE%\Data\Chrome\CORS\
```

![for-windows-2](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2019-04-09-ChromeCrossOrigin/for-windows-2.png)

### 3.完成跨域

![for-windows-3](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2019-04-09-ChromeCrossOrigin/for-windows-3.png)
