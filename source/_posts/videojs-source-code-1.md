---
title: videojs源码阅读（一）
date: 2020-09-04 17:30:47
categories:
tags:
---

## 代码组织结构

```shell
|--.github
|--build  打包相关脚本及配置文件
|--docs  文档说明
|--lang  多语言化
|--sandbox  示例
|--src  源代码目录
    |--css
    |--js
|--test 测试
|--...  其他

```

## `src`主要文件分析

- `index.js` & `video.js`

​   `index.js` 入口文件, 导出主要代码逻辑在`video.js`

- `setup.js` 

  根据`video`标签的`data-setup`属性，设置播放器

- `resize-manager.js`

- `poster-image.js` ： 处理播放器封面

- `player.js` ： 核心播放器类

- `plugin.js` 插件

- `modal-dialog.js` ：处理弹层，中断播放

- `media-error.js` ： 定义错误描述

- `loading-spinner.js` ： 播放器加载标识， waiting/loading

- `live-tracker.js`

- `fullscreen-api.js`： 浏览器全屏

- `extend.js`

- `event-target.js` ：原生EventTarget的封装

- `error-display.js` ：处理错误展示

- `component.js` ：所有UI类的基类

- `close-button.js`   ：关闭按钮

- `clickable-component.js` 
  
  可支持点击事件和键盘事件的button, 不是原生HTML button

- `button.js`：  按钮的基类

- `big-play-button.js`： 视频播放前展示的按钮

- `control-bar`：  控制器，比如音轨，进度条，音量控制等

- `menu` ：popup  弹层相关

- `mixin`

- `slider`  slider的基础实现，如进度条

- `tech` 对播放方法的封装，比如HTML5,flash等

- `tracks` 处理音轨等

- `utils` 常用的功能函数

## 启动播放器的流程

### 1.主要文件

`video.js` 、 `player.js`、 `component.js`

```js
// 1. 创建player，调用 Player（player.js）
// 2. Player继承自Component
// 3. beforesetup 
// 4. 获取当前Player Component
// 5. setup
```

###  2.`video.js` 方法

```js
// ....
//  获取播放器实例
let player = videojs.getPlayer(id);

if (player) {
  // 已经初始化，options无效
  if (options) {
    log.warn(`Player "${id}" is already initialised. Options will not be applied.`);
  }
  // 添加播放器ready的回调函数
  if (ready) {
    player.ready(ready);
  }
  return player;
}

// id可以是string形式的id也可以是DOM节点
// normalizeId 如果带#, 去掉#
const el = (typeof id === 'string') ? Dom.$('#' + normalizeId(id)) : id;

// 如果不是Dom元素，抛出错误
if (!Dom.isEl(el)) {
  throw new TypeError('The element or ID supplied is not valid. (videojs)');
}

if (!el.ownerDocument.defaultView || !el.ownerDocument.body.contains(el)) {
  log.warn('The element supplied is not included in the DOM');
}

options = options || {};

// 声明周期hooks--beforesetup
videojs.hooks('beforesetup').forEach((hookFunction) => {
  const opts = hookFunction(el, mergeOptions(options));

  if (!isObject(opts) || Array.isArray(opts)) {
    log.error('please return an object in beforesetup hooks');
    return;
  }

  options = mergeOptions(options, opts);
});

// We get the current "Player" component here in case an integration has
// replaced it with a custom player.
const PlayerComponent = Component.getComponent('Player');

player = new PlayerComponent(el, options, ready);

// 声明周期hooks--beforesetup
videojs.hooks('setup').forEach((hookFunction) => hookFunction(player));

// 返回播放器实例
return player;
```

###  3. `player.js`

```js
constructor(tag, options, ready) {
  // ...

  // Run base component initializing with new options
  // 实例化父类
  super(null, options, ready);
  // ...
}
```

### 4. `component.js`

```js
constructor(player, options, ready) { 

  // code ...
  this.ready(ready);

}

```

### 5.插件

```js
// video.js

```

