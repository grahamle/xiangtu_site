---
title: Gruntfile.js
date: 2013-11-11
category: clientout
layout: page
modifiedOn: 2013-11-14
---

## Gruntfile.js

Grunt 是一个任务自动化工具（task runner），Gruntfile.js 为 Grunt 的配置文件。关于 Grunt 的用法和配置等，可以参考 [Grunt 主页](http://gruntjs.com/)。

**Q**：代码前面16行都是干嘛的？  
**A**：这里面主要声明一些下面配置的时候要用到的变量和信息。详述下面几个变量：

- lrSnippet ：livereload 脚本片段，因为 livereload 需要通过在 html 中嵌入一段代码来引用入口文件，此文件在最终发布时是不需要的，故通过一个 connect 中间件仅在开发调试中实时嵌入。
- uuid ：通过依赖 node-uuid 模块来生成唯一的随机 id
- mountFolder ：用于方便配置 connect 静态文件中间件的函数，方便的 mount 一个目录供 connect 读取。
- modRewrite ：加载 connect-modrewrite ，一个 connect 中间件，可以给 connect/express 的 server 提供 URL 重写功能。用于适配 Angular 的 HTML5 Mode，将所有请求重定向给 index.html
- swig ：模板引擎，用于预处理一些用模版生成的教材内容，如单词表等。

**Q**：500行的 js 代码，到底都干了些啥？  
**A**：别看代码行数挺多，其实逻辑倍儿清晰。总体就干了四件事：

- 通过 forEach() 加载项目依赖的所有 grunt 插件
- yeoman 配置及异常检测
- grunt.initConfig() 是配置主体，里面是一个 js 对象，定义所有 grunt 插件的配置（共达345行）
- grunt.registerTask() 注册 grunt 任务。

**Q**：命令行中执行的一个 grunt 命令代表什么？  
**A**：grunt 不带参数运行会执行 Gruntfile.js 中的默认任务，目前的默认任务为 `server` 任务。

**Q**：这个 js 文件最后是怎么被用的？  
**A**：整个 js 文件是通过 `module.exports()` 作为 node.js 模块暴露在外的，grunt会在当前目录下通过文件名找到这个文件，据此进行任务执行。

**Q**：那么 `grunt.initConfig()` 里到底有哪些任务呢？  
**A**：`initConfig` 是各个 grunt 插件任务的初始化配置（**注**，带 grunt-contrib- 前缀的，是 Grunt 的官方插件），具体如下：

* `yeoman`：配置自定义变量 yeomanConfig。
* `livereload`：配置 [grunt-contrib-livereload](https://github.com/gruntjs/grunt-contrib-livereload) 插件，用于检测文件变化并自动刷新浏览器。此插件已经被废弃，后面会升级为 [grunt-contrib-watch](https://github.com/gruntjs/grunt-contrib-watch)。
* `watch`：配置 [grunt-regarde](https://github.com/yeoman/grunt-regarde) 插件，用于监视文件变化并执行其他任务，目前做了 alias 为 watch。此插件已经被废弃，后面会升级为 [grunt-contrib-watch](https://github.com/gruntjs/grunt-contrib-watch)。
* `replace`：配置 [grunt-text-replace](https://github.com/yoniholmes/grunt-text-replace) 插件，用来替换文本，包括几个 target 配置，分别替换代码中的不同部分。
* `connect`：配置 [grunt-contrib-connect](https://github.com/gruntjs/grunt-contrib-connect) 插件，用于开启一个 [connect](http://www.senchalabs.org/connect/) web 服务器供开发时使用。
* `open`：配置 [grunt-open](https://github.com/jsoverson/grunt-open) 插件，打开特定文件，这里打开的是 url，故会调用系统默认浏览器。
* `clean`：配置 [grunt-contrib-clean](https://github.com/gruntjs/grunt-contrib-clean) 插件，用于清理临时文件。
* `jshint`：配置 [grunt-contrib-jshint](https://github.com/gruntjs/grunt-contrib-jshint) 插件，用于自动 hint js 文件，**暂未使用**。
* `karma`：配置 [grunt-karma](https://github.com/karma-runner/grunt-karma) 插件，用于自动化测试，目前**暂未使用**。
* `concat`：配置 [grunt-contrib-concat](https://github.com/gruntjs/grunt-contrib-concat) 插件，做文件的合并。
* `usemin`：配置 [grunt-usemin](https://github.com/yeoman/grunt-usemin) 插件，用于将 HTML 中对一系列文件的引用合并为一个引用。
* `useminPrepare`：同上，是 usemin 的一部分。
* `imagemin`：配置[grunt-contrib-imagemin](https://github.com/gruntjs/grunt-contrib-imagemin) 插件，用于优化图片文件，**暂时未用**，项目中尚未用到图片。
* `cssmin`：配置 [grunt-contrib-cssmin](https://github.com/gruntjs/grunt-contrib-cssmin) 插件，用于 css 文件压缩。
* `ngmin`：配置 [grunt-ngmin](https://github.com/btford/grunt-ngmin) 插件，用来压缩 Angular 相关的 js 代码，因 Angular 使用了 [DI](http://docs.angularjs.org/guide/di)，代码较为特殊，ngmin 可解决此问题。
* `uglify`：配置 [grunt-contrib-uglify](https://github.com/gruntjs/grunt-contrib-uglify) 插件，用于代码混淆。
* `rev`：配置 [grunt-rev](https://github.com/cbas/grunt-rev) 插件，用于给静态文件加版本号以解决缓存问题。
* `copy`：配置 [grunt-contrib-copy](https://github.com/gruntjs/grunt-contrib-copy) 插件，用于复制文件到指定目录，目前用于将文件复制到构建目录。目前里面的几个 ios 等 target 暂未用到。
* `stylus`：配置 [grunt-contrib-stylus](https://github.com/gruntjs/grunt-contrib-stylus) 插件，用于预处理 styl 文件为 css 文件。
* `shell`：配置 [grunt-shell](https://github.com/sindresorhus/grunt-shell) 插件，用于执行 shell 命令，目前用到的是通过 git 抓取和更新教材内容。

**Q**：好人，最后告诉我一下这些任务是怎么被执行的吧？要按顺序么？还是乱序随便？  
**A**：grunt 的任务是在 Gruntfile.js 中通过 registerTask 指定，之后在命令行通过参数读入任务名并执行的。具体参考 [Grunt 主页](http://gruntjs.com/)。