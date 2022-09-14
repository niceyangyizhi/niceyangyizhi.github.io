---
layout: post
title:  "node config模块"
category: dev
---

config模块用于管理node项目的各种配置文件。

使用方法：
```
const config = require('config');
```
会默认加载当前工作目录下config文件下的配置文件，可以自己设置配置文件加载路径`process.env.NODE_CONFIG_DIR=" __dirname + "/configDir/"`。多个配置目录使用分隔符链接起来`process.env["NODE_CONFIG_DIR"] = __dirname + "/configDir/" + require('path').delimiter + __dirname + "/configDir2/";`


默认加载`default.js`，如果设置了环境变量`process.env.NODE_ENV`(`development`、`production`、`envName`)，则会加载对应的文件`[nevNane].js`。如果`process.env.NODE_ENV`为空，且存在`development.js`则会加载`development.js`。

使用`config.get()`获取配置项，当配置项不存在时，方法会抛出异常。

使用`config.has()`判断一个配置项是否存在。