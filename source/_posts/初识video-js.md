---
title: 初识video.js
date: 2020-09-04 17:30:07
categories:
tags:
---
随着视频和直播业务的流行，在Web页面中播放视频已经成为很常见的业务场景。

虽然html5原生支持了video元素，但是由于浏览器的支持情况不同，存在很多兼容性。

可以通过 `can i use video ?`查看目前的浏览器支持情况：

https://caniuse.com/#search=video



那么如何选择一个适合的播放器呢？在不自己造轮子的情况下，可以选择一些开源的播放器，然后定制化开发。目前比较流行的一个Web端Video播放器是`Video.js`。


## Video.js 简介

官网：https://videojs.com/

github地址：https://github.com/videojs/video.js


`Video.js`是一个web video播放器，支持 `HTML5 video`和 `Flash` ，主要有以下优点：

- 支持格式多：

  除了支持MP4、WebM，也支持`adaptive streaming formats`比如HLS 、DASH

- 丰富的插件支持

- 支持UI自定义

- 浏览器兼容性：

  支持Modern Browser, 支持桌面端及移动端

## video.js  VS  `<video>`

When to use `Video.js` over the `<video>`element?

`Video.js`可以支持跨浏览器的样式一致性，支持动态码率格式，支持 Youtube, Youtube等平台，有丰富的插件

| Feature  | Video.js     | HTML5  |
| ---------| ------------ | ------ |
| **Cross-browser "Skins"** | Looks good everywhere with CSS-based Skins | Looks different in every browser                           |
| **Adaptive Streaming (adjusting to the viewer’s bandwidth)** | HLS supported everywhere.<br /> DASH supported everywhere but iOS Safari. | HLS and DASH not playable in Chrome or Firefox by default. |
| **Social Video Platforms** | Play Youtube, Vimeo, and more with added plugins.  | Not supported  |
| **Community-built Plugins**  | Hundreds!   | Probably?   |
| **Browser API Inconsistencies**  | Makes them disappear  | Many    |

## 文档

Plugins: https://videojs.com/plugins/
文档: https://docs.videojs.com/