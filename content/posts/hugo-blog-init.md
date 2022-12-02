---
title: "使用Hugo 搭建blog"
date: 2022-11-30T19:02:02+08:00
draft: false
# image: 
categories:
    - Hugo 
    - React
    - Vue
tags:
    - tag1
---


## 常用目录说明


| 子目录名称  | 功能                                                                        |
| ----------- | ------------------------------------------------------------------------  |
| archetypes  | 新文章默认模板                                                              |
| config.toml | 配置文档                                                                   |
| content     | 存放所有`Markdown`格式的文章, 可以自定义子文件目录                              |
| layouts     | 存放自定义的`view`，可为空                                                   |
| static      | 存放静态资源                                                                |
| themes      | 存放下载的主题                                                              |


## 生成新文章

`hugo new posts/my-first-post.md`

在content目录中会自动以`archetypes/default.md`为模板在`content/posts`目录下生成一篇名为`my-first-post.md`的文章草稿：

## 本地服务启动

`hugo server`

浏览器中输入网址http://localhost:1313/ 可预览

## 生成网页

`hugo`

生成的内容会在 `public`文件下


## Stack主题修改

https://stack.jimmycai.com/guide/modify-theme

文档里可能不全, 可以看下项目的issues: [hugo-theme-stack](https://github.com/CaiJimmy/hugo-theme-stack)

### favicon

1. 新建目录`static/img`, `favicon.ico`放置在此目录下
2. 配置文件修改

```toml
[params]
    favicon = 'img/favicon.ico'
```

### 主页不显示内容？

1. 修改 **mainSections**, `posts`为文件所在目录：`content/posts`

```toml
[params]
    mainSections = ['posts']
```

2. 非草稿状态的文件才会显示 **draft**

### 设置widget

```toml
[params.widgets]
[[params.widgets.homepage]]
    type = 'search'
[[params.widgets.homepage]]
    type = 'archives'
    [params.widgets.homepage.params]
        limit = 5
[[params.widgets.homepage]]
    type = 'categories'
    [params.widgets.homepage.params]
        limit = 10
[[params.widgets.homepage]]
    type = 'tag-cloud'
    [params.widgets.homepage.params]
        limit = 10
```