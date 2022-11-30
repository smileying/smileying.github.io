---
title: "使用Hugo 搭建blog"
date: 2022-11-30T19:02:02+08:00
draft: true
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


## Stack主题修改

https://stack.jimmycai.com/guide/modify-theme

### 