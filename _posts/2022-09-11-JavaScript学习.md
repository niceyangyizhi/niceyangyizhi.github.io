---
layout: post
title:  "Loadsh库"
category: dev
---

## NodeJS代码小技巧

使用一个属性前先判断这个值是否存在，避免抛出错误。判断一个对象是否是空对象，可以使用`Object.keys(obj).length === 0`
```
if (externalFileMap['attachmentPng'] && Object.keys(externalFileMap['attachmentPng']).length === 0) {
        externalFileMap['attachmentPng'] = externalFileMap['png'];
}
```
## Array.prototype.slice.apply(arguments)

JS中每个函数都会有一个隐藏参数`arguments`表示传递给该函数的所有实参，`arguments`是一个类数组对象，可以使用`Array.prototype.slice.apply(arguments)`将对象转化成数组。

除了上述方法外，还可以使用以下方法，参见[Arguments 对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments)
```
var args = Array.prototype.slice.call(arguments);
var args = [].slice.call(arguments);

// ES2015
const args = Array.from(arguments);
const args = [...arguments];

```

>Tips：箭头函数中不能使用`arguments`局部变量。