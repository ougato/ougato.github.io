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

## **Set**

### 基本用法

```typescript
let s: Set = new Set()
```

### 特性描述

1. 自身是一个`构造函数`，用于`生成数据结构`。
2. 类似于`数组`，它内部成员的值都是`唯一`的，没有重复值。

### 常用属性

* `size` : 获取 `Set` 内的成员数量。

### 常用方法

* `add(value)` : 添加一个值，返回 `Set` 结构本身。
* `delete(value)` : 删除某个值，返回一个布尔值，表示删除是否成功。
* `has(value)` : 返回一个布尔值，表示该值是否为 `Set` 的成员。
* `clear()` : 清除所有成员，没有返回值。
* `keys()` : 返回键名的遍历器。
* `values()` : 返回键值的遍历器。
* `entries()` : 返回键值对的遍历器。
* `forEach()` : 使用回调函数遍历每个成员。

---

## **WeakSet**

### 基本用法

```typescript
let ws: WeakSet = new WeakSet()
```

### 特性描述

1. 自身是一个`构造函数`，用于`生成数据结构`。
2. 类似于`数组`，它内部成员的值都是`唯一`的，没有重复值，但它成员`只能是对象类型`。
3. 成员对象都是`弱引用`，不计入垃圾回收机制中，放入的成员对象引用计数不 +1。
4. 用于`临时存放一组对象`，外部某个对象的引用计数一旦为 0 时，在 WeakSet 内的某个对象会一同消失。
5. 由于垃圾回收机制运行不可预测，它内部的成员会随时消失，所以`没有提供遍历`的方法。

### 常用方法

* `add(value)` : 添加一个值，返回 `WeakSet` 结构本身。
* `delete(value)` : 删除某个值，返回一个布尔值，表示删除是否成功。
* `has(value)` : 返回一个布尔值，表示该值是否为 `WeakSet` 的成员。

---

## **Map**

### 基本用法

```typescript
let map: Map = new Map()
```

### 特性描述

1. 本质上是键值对的集合，各种类型的值（包括对象）都可以当作键。


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