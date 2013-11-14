---
title: package.json
date: 2013-11-11
category: clientout
layout: page
modifiedOn: 2013-11-14
---

## package.json

**Q**：该文件不就是个 json 文件么？很重要么？都放啥呀？  
**A**：此文件标识了项目的元数据信息，npm 会从此文件中存取需要安装的依赖，grunt 也从此文件中读取相关依赖。如果在安装 npm 模块时提供了 `--save` 或 `--save-dev` 参数，则会将对应模块作为依赖写入此文件的对应位置。关于 package.json 的各项设定，可以参考 npm 文档 [package.json(5)](https://npmjs.org/doc/files/package.json.html) 部分。