---
layout: post
title:  "VSCode debug配置环境变量"
category: dev
---

VSCode在Launch文件中配置调试参数，在`configurations`中新增一个字段`env`，在这里写上NODE_ENV以及其他自定义环境变量，参见[链接](https://segmentfault.com/a/1190000020236324)

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "node debug",
            "program": "${workspaceFolder}/bin/www",
            "env":{
                "NODE_ENV":"development",
                "PORT":8080,
                "CUSTOM_PARAMS":"foo"
            }
        }
    ]
}
```