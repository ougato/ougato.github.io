---
layout: post
title: "Typescript"
date: 2019-05-16 01:09:24 +0800
categories: Learn
tags: Typescript
author: ougato
mathjax: true
---

* content
{:toc}




# [Typescript](https://www.tslang.cn/docs)

## [基础类型](https://www.tslang.cn/docs/handbook/basic-types.html)

### boolean

```
let isBoolean: boolean = false;
```

### number

```
// 二进制
let binary: number = 0b1010;
// 八进制
let octal: number = 0o12
// 十进制
let decimalism: number = 10;
// 十六进制
let hex: number = 0xa;
```

### string

```
// 正常字符串
let name: string = "oucheng";
// 模版字符串
let introduce: string = `I'm ${name}.`;
```

### array

```
// 正常数组
let list: number[] = [1, 2, 3];
// 泛型数组
let list: Array<number> = [1, 2, 3];
```

### tuple

```
// 声明元组
let x: [string, number];
// 正确示范
x = ['hello', 10];
// 错误示范
x = [10, 'hello'];
```

### enum

```
// 枚举默认从0开始元素编号
enum Color {
    Red = 1,
    Green,
    Blue
}
let c: Color = Color.Green;
```

### any

```
// 任意赋值
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false;
```

### void

```
// 表示没有返回任何类型
function foobar(): void {
    console.log("foobar");
}
```

### null

```
let n: null = null;
```

### undefined

```
// 默认未指定值的变量都是undefined
let u: undefined = undefined;
let u;
let u: any;
```

### never

```
// 没有返回值的函数内就是never类型
function error(message: string): never {
    throw new Error(message);
}
// 死循环的返回类型也是never
function infiniteLoop(): never {
    while (true) {
        console.log("never");
    }
}
```

### object

```
// 对象类型声明
declare function create(o: object | null): void;
create({ prop: 0 });
create(null);
```

### as

```
let someValue: any = "this is a string";
// 正常用法
let str: string = someValue as string;
// 尖括号用法 跟C/C++显示转换类似
let str: string = <string>sameValue;
```

### function

```
// 匿名函数
function():void {
    console.log("anonymity");
}
// 类函数
foobar():void {
    console.log("class");
}
// 有名函数
function foobar():void {
    console.log("foobar");
}
```

### var

```
// var的是函数作用域，共用一个i
for(var i = 0; i < 10; ++i) {
    for(var i = 10; i < 20; ++i) {
        console.log(i);
    }
    console.log(i);
}
```

### let

```
// let的是块作用域，各自独立的i
for(let i = 0; i < 10; ++i) {
    for(let i = 10; i < 20; ++i) {
        console.log(i);
    }
    console.log(i);
}
```

### const

```
// const定义常量，能用const的地方，尽量少用let
const DEFINE: number = 10;
```