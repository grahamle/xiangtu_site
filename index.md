---
layout: homepage
title: 项目代码说明文档（alpha）
date: 2013-11-11
modifiedOn: 2013-11-14
---
	
<h2 id="organization">目录组织</h2>

- [/client](organization/client.html)
- [/server](organization/server.html)

<h2 id="clientout">外围文件</h2>

- [Gruntfile.js](clientout/gruntfile.js.html)
- [package.json](clientout/package.json.html)

<h2 id="stateview">状态切换</h2>

<h2 id="controllers">控制器</h2>

<h2 id="directives">指令集</h2>

<h2 id="filters">过滤器</h2>

<h2 id="services">依赖服务</h2>

<h2 id="reader">第二界面视图</h2>

<h2 id="shelf">书架界面视图</h2>

<h2 id="Documents">教材仓库</h2>

{% comment %}

{% if site.posts.size != 0 %}

## 最新文章

{% for post in site.posts %}
* {{ post.date | date_to_string }} [{{ post.title }}]({{ post.url }})
{% endfor %}

{% endif %}

{% if site.pages.size != 0 %}

## 最新页面

{% for page in site.pages limit:5 %}
{% if page.url !='/index.html' %}
* [{{ page.title }}]( {{ page.url }})（{{ page.date }}）
{% endif %}
{% endfor %}

{% endif %}

{% endcomment %}
