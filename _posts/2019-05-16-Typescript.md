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
let s: Set = new Set();
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
let ws: WeakSet = new WeakSet();
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

预留空白处，待补充

---

## **Proxy**

### 基本用法

```typescript
// param 1: 需要代理的目标对象。
// param 2: 配置对象，每一个被代理的方法，都需要提供一个对应的处理函数，该函数将拦截对应的方法。
let proxy: Proxy = new Proxy({}, {
    construct: function(target, args, newTarget) {},
    get: function() {},
    set: function() {},
    apply: function() {},
});
```

### 特性描述

1. 在目标对象之前架设一层 “拦截” ，外界对该对象的访问，都必须先通过这层拦截。

### 常用方法

* `get()`
  * 用于拦截某个属性的`读取`操作；可以接受三个参数，依次为目标对象、属性名、Proxy 实例本身（严格地说，是操作行为所针对的对象），其中最后一个参数可选。
* `set()`
  * 用来拦截某个属性的`赋值`操作；可以接受四个参数，依次为目标对象、属性名、属性值、 Proxy 实例本身，其中最后一个参数可选。
* `apply()`
  * 拦截函数的调用，`call` 和 `apply` 操作；可以接受三个参数，分别是目标对象、目标对象的上下文对象（this）、目标对象的参数数组。
* `has()`
  * 用来拦截 `HasProperty` 操作，即判断对象是否具有某个属性时，这个方法会生效，典型的操作就是 `in` 运算符；可以接受两个参数，分别是目标对象、需查询的属性名。
* `construct()`
  * 用于拦截 `new` 命令。
* `deleteProperty()`
  * 用于拦截 `delete` 操作，如果这个方法抛出错误或者返回 false，当前属性就无法被 delete 命令删除。
* `defineProperty()`
  * 用于拦截 `Object.defineProperty()` 操作。
* `getOwnPropertyDescriptor()`
  * 用于拦截 `Object.getOwnPropertyDescriptor()` ，返回一个属性描述对象或者undefined。
* `getPrototypeOf()`
  * 用于拦截`获取对象原型`。具体来说，拦截下面这些操作。
    - Object.prototype.\_\_proto\_\_
    - Object.prototype.isPrototypeOf()
    - Object.getPrototypeOf()
    - Reflect.getPrototypeOf()
    - instanceof
* `isExtensible()`
  * 用于拦截 `Object.isExtensible()` 操作。
* `ownKeys()`
  * 用于拦截`对象自身属性的读取操作`。具体来说，拦截以下操作。
    - Object.getOwnPropertyNames()
    - Object.getOwnPropertySymbols()
    - Object.keys()
    - for ... in
* `preventExtensions()`
  * 方法拦截 `Object.preventExtensions()`。该方法必须返回一个布尔值，否则会被自动转为布尔值。
  * 这个方法有一个限制，只有目标对象不可扩展时（即 `Object.isExtensible(proxy)` 为 false），proxy.preventExtensions 才能返回 true，否则会报错。
* `setPrototypeOf()`
  * 方法拦截 `Object.setPrototypeOf()` 方法。
* `Proxy.revocable()`
  * 方法返回一个可取消的 Proxy 实例。
  * 方法返回一个对象，该对象的 proxy 属性是 Proxy 实例，revoke属性是一个函数，可以取消 Proxy 实例。上面代码中，当执行 revoke 函数之后，再访问 Proxy 实例，就会抛出一个错误。
  * 目标对象不允许直接访问，必须通过代理访问，一旦访问结束，就收回代理权，不允许再次访问。
* `this 问题`
  * 虽然 Proxy 可以代理针对目标对象的访问，但它不是目标对象的透明代理，即不做任何拦截的情况下，也无法保证与目标对象的行为一致。主要原因就是在 Proxy 代理的情况下，目标对象内部的this关键字会指向 Proxy 代理。

---

### **Reflect**


### 特性描述

1. 将Object对象的一些明显属于语言内部的方法（比如Object.defineProperty），放到Reflect对象上。现阶段，某些方法同时在Object和Reflect对象上部署，未来的新方法将只部署在Reflect对象上。也就是说，从Reflect对象上可以拿到语言内部的方法。




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