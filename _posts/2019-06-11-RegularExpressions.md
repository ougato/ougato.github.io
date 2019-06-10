---
layout: post
title: "正则表达式"
date: 2019-06-11 00:15:07 +0800
categories: Learn
tags: RegularExpressions
author: ougato
mathjax: true
---

* content
{:toc}




# 正则表达式

## 1.元字符<Metacharacters>

`[]` : **字符组**
> 包含在字符组内的任意字符都匹配
```
"abcdefghijklmnopqrstuvwxyz"
abc[d123]efghijklmnopqrstuvwxyz
```

`-` : **连字符号**
> 表示一个范围，以ASCII码来连接，如果存在`字符组`的第一个字符时，或存在`字符组`以外时，连字符号功能无效。

```
"abcdefghijklmnopqrstuvwxyz"
[a-z]
```

`^` : **脱字符号**
> 在表达式第一个字符时，匹配一行的开头，以`^`紧跟的内容去匹配。
```
"abcdefghijklmnopqrstuvwxyz"
^ab
```
> 在字符组内时，它是一个取反的含义，即除了123456以外都匹配，这里我们又回顾了一次连字符。
```
"abcdefghijklmnopqrstuvwxyz"
[^1-6]
```

`$` : **美元符号**
> 以`$`之前的字符串结束匹配。
```
"abcdefghijklmnopqrstuvwxyz"
xyz$
```

`.` : **点号**
> 用于匹配任意字符的简便写法，可以匹配到任何字符，除了换行符。
```
"abcdefghijklmnopqrstuvwxyz"
abc.efghijklmnopqrstuvwxyz
```

`|` : **竖线符号**
> 和符号意思相同，可以做为运算`或`，两个表达式之间取其中一个。
```
"abcdefghijklmnopqrstuvwxyz"
123|abcdefghijklmnopqrstuvwxyz
```

`?` : **问号**
> 只作用于问号前一个相邻的字符，让前一个字符可有可无。
```
"abcdefghijklmnopqrstuvwxyz"
abc?e?defghijklmnopqrstuvwxyz
```

`+` : **加号**
> 匹配1-N次，什么意思，就是在`c`字母后面匹配`d`的时候，必须要找到`d`一次，如果没有`d`，那就匹配失败了。
```
"abcdefghijklmnopqrstuvwxyz"
abcd+efghijklmnopqrstuvwxyz
```

`*` : **星号**
> 匹配0-N次，什么意思，就是在`c`字母后面匹配`d`的时候，无需要找到`d`一次，存不存在`d`都可以成功。
```
"abcefghijklmnopqrstuvwxyz"
abcd+efghijklmnopqrstuvwxyz
```