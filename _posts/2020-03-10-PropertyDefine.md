---
layout: post
title: "property完整属性定义详解"
date: 2020-03-10 15:42:51 +0800
categories: Learn
tags: Cocos-Creator
author: ougato
mathjax: true
---

* content
{:toc}




# Typescript 中 property 完整属性定义详解

## **`displayName`**
> * 功能：表示重定义变量在编辑器面板的名字 
> * 类型：**`string`**

```typescript
@property({
    displayName: "爪哇",
    type: cc.Label
})
public java: cc.Label = null;
```

![图-01](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-01.png)

脚本中定义了变量为 **java** 的变量名，使用 `displayName` 改变了在编辑器面板上的名字，相当于给 **java** 起了个别名叫 **爪哇**，但不会实际改变 **java** 的使用变量名。

## **`tooltip`**
> * 鼠标停留在编辑器面板变量上的提示 
> * 类型：**`string`**

```typescript
@property({
    tooltip: "用于沟通表示友好的开场白",
    type: cc.Label
})
public hello: cc.Label = null;
```

![图-02](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-02.gif)

在装饰器中定义了 `tooltip` 属性，用于给 **hello** 变量在编辑器上的描述显示，使用鼠标移动到 **hello** 的位置，就会提示出这段描述 **"用于沟通表示友好的开场白"**。

## **`multiline`**
> * 属性类型是字符串的时候，是否允许多行输入
> * 类型：**`boolean`**

```typescript
@property({
    multiline: true,
    type: cc.String
})
public hello: string = "";
```

![图-03](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-03.png)

![图-04](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-04.png)

当属性 **type** 为字符串类型时，**multiline** 为 false，编辑输入框是（图1）仅支持单行输入，若 **multiline** 为 true 时，编辑输入框是（图2）允许多行输入字符串，默认 **multiline** 属性 为 false。

## **`readonly`**
> * 任意属性上，只允许存在初始默认值，锁定开发者不允许修改属性值
> * 类型：**`boolean`**

```typescript
@property({
    readonly: true,
})
public hello: string = "hello";
```

![图-05](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-05.gif)

如果 **readonly** 存在属性内，当它的值为 true 时，开发者只能使用和观看其值，不允许开发者在编辑器属性上去修改它，如果为 false 时，就会解开锁定，允许任意修改其值，默认为 false。

## **`min`**
> * 类型为数值的前提下，在面板编辑框内限定输入最小数值
> * 类型：**`number`**

```typescript
@property({
    min: 0,
})
public hello: number = 100;
```

![图-06](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-06.gif)

必须为数值 **number** 类型，**min** 属性才生效，由上图所示，在输入框内输入 -1，由于输入小于 0 的数值，编辑框自动设置为 **min** 的数值 0，可以与 **max** 配合使用。

## **`max`**
> * 类型为数值的前提下，在面板编辑框内限定输入最大数值
> * 类型：**`number`**

```typescript
@property({
    max: 500,
})
public hello: number = 0;
```

![图-07](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-07.gif)

必须为数值 **number** 类型，**max** 属性才生效，由上图所示，在输入框内的数值不能超过 500，如果超过了，编辑框自动设置数值为 **max** 的值 500，可以与 **min** 配合使用。

## **`step`**
> * 鼠标拖动，单步拖动的单位
> * 类型：**`number`**

```typescript
@property({
    min: 0,
    max: 500,
    step: 50
})
public hello: number = 0;
```

![图-08](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-08.gif)

如上代码，最小是 0，最大是 500，每次单步拖动为 50，所以鼠标往右移动 10次就走到头了，不能再往右拖动增加数值了。

## **`range`**
> * 包含了 **min\|max\|step**，可以直接在 **range** 中快速设置这三个值。
> * 类型：**`number[]`**

```typescript
@property({
    range: [0, 500, 50]
})
public hello: number = 0;
```

![图-09](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-09.gif)

如果需要三个属性 **min\|max\|step** 同时存在的时候，允许在 number 数组中，传入三个数值，下标 1 代表 min，下标 2 代表 max，下标 3 代表 step，快速设置。

## **`slide`**
> * 编辑器面板显示横向滑动条，鼠标拖动来改变数值大小
> * 类型：**`boolean`**

```typescript
@property({
    slide: true,
    range: [0, 500, 50],
})
public hello: number = 0;
```

![图-10](https://raw.githubusercontent.com/ougato/ougato.github.res/master/2020-03-10-PropertyDefine/property-define-10.gif)

当类型是 **number** 的时候如果 **slider** 为 true，则会在编辑器面板显示一个横向滑动条，鼠标拖动来改变数值大小，默认值为 false，代表不以滑动条显示。


## **`serializable`**
> * 指定了 default 默认值的属性默认情况下都会被序列化，序列化后就会将编辑器中设置好的值保存到场景等资源文件中，并且在加载场景时自动还原之前设置好的值。如果不想序列化，可以设置 serializable: false
> * 类型：**`boolean`**

## **`formerlySerializedAs`**
> * 指定之前序列化所用的字段名
> * 类型：**`string`**

## **`editorOnly`**
> * 在导出项目前剔除该属性，默认值为 false
> * 类型：**`boolean`**

## **`override`**
> * 所有属性都将被子类继承，如果子类要覆盖父类同名属性，需要显式设置 override 参数，否则会有重名警告，默认为 false
> * 类型：**`boolean`**

## **`animatable`**
> * 该属性标识是否能被动画修改，默认为 true 可以被动画修改
> * 类型：**`boolean`**