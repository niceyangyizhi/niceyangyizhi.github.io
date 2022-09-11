---
layout: post
title:  "Loadsh库"
category: dev
---

NodeJS代码小技巧
使用一个属性前先判断这个值是否存在，避免抛出错误。判断一个对象是否是空对象，可以使用`Object.keys(obj).length === 0`
```
if (externalFileMap['attachmentPng'] && Object.keys(externalFileMap['attachmentPng']).length === 0) {
        externalFileMap['attachmentPng'] = externalFileMap['png'];
}
```


