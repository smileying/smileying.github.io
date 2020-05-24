---
title: hexo博客配置优化
date: 2020-05-23 16:40:26
categories:
- 博客写作
tags:
- Hexo
---

# 整体配置优化

## 侧边栏设置

侧边栏跟人信息展示区，主要包括头像，社交信息、文章目录，站点概览等


### 作者信息展示

### 文章目录

`next`主题配置：

```yml
post_navigation: left
```

## 实时预览

## 博客底部布局

## 博客摘要显示

# 增加搜索

- 安装
  ```javascript
  npm install hexo-generator-searchdb --save
  ```

- 修改根目录下的`_config.yml`， 增加`search`配置:
  ```yml
  search:
    path: search.html
    fiels: post # post page all
    content: true
    format: html
  ```


- 修改`next`主题配置`_config.yml`:
  
  ```yml
  local_search:
    enable: true
  ```


# 标签&分类&归档

## 配置

`next`主题下`_config.yml`中：

```yml
# Menu Settings
menu:
  home: / || fa fa-home
  about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  schedule: /schedule/ || fa fa-calendar

menu_settings:
  icons: true  # 是否显示各个页面的图标
  badges: true # 是否显示分类/标签/归档页的内容量

```

## 生成tags page

```javascript
hexo new page tags
```

`source`目录下生成一个文件夹：`tags`:

```javascript
---
title: tags
date: 2020-05-23 20:53:37
---
```

添加`type: "tags"`到内容中, 修改title为中文【标签】：

```javascript
---
title: tags
date: 2020-05-23 20:53:37
type: "tags"
---
```

文章中增加`tags`后，回自动关联，例如

```javascript
---
title: 从0到1搭建hexo博客（1）
date: 2020-05-23 14:26:49
tags:
- Hexo
---
```

至此，已经成功给文章添加分类，点击【标签】可以看到已经有的具体标签，点击具体的标签可以看到该标签下的所有文章。只有添加了`tags: xxx`的文章才会被收录到标签中。


## 生成categories page

步骤类似tags, 对应得更换为categories 

```javascript
hexo new page categories
```

```javascript
---
title: categories
date: 2020-05-23 20:59:07
---
```

```javascript
---
title: 分类
date: 2020-05-23 20:59:07
type: categories
---
```








# 文章写作相关

## 文章缩略描述

## 增加文章版权信息

## 增加文章结束标志

## 增加阅读次数、时长和访客数

- 安装插件
  ```javascript
  npm install hexo-symbols-count-time --save
  // https://www.npmjs.com/package/hexo-symbols-count-time
  ```
- 修改站点配置文件，增加：
  ```yml
  symbols_count_time:
    symbols: true # 是否统计字数
    time: true # 是否统计阅读时长
    total_symbols: true # 是否统计总字数
    total_time: true # 是否统计总阅读时长
    exclude_codeblock: false
    awl: 2 # Average Word Length (chars count in word). Default: 4
    wpm: 300 # Words Per Minute. Default: 275
    suffix: "mins."
  ```
  
- `next`主题中可修改的相关配置
  
  ```yml
  symbols_count_time:
    separated_meta: true # 分隔符|
    item_text_post: true # 是否统计站点总字数
    item_text_total: true # 是否统计文章总字数
    awl: 2  # 适合汉字，平均每个字符长度
    wpm: 300 # 适合汉字 words per minute

  busuanzi_count:
    enable: false # 是否开启不蒜子统计功能
    total_visitors: true # 是否统计总访客数
    total_visitors_icon: fa fa-user
    total_views: true # 是否统计总访问数
    total_views_icon: fa fa-eye
    post_views: true # 是否统计文章访问数
    post_views_icon: fa fa-eye

  ```



## 设置代码块样式

### 修改`next`自带的代码块配置
   
  ```yml
  # https://github.com/chriskempson/tomorrow-theme
  codeblock:
    highlight_theme: night
    copy_button:
      enable: true # 设置可复制
      # Show text copy result.
      show_result: false
      # Available values: default | flat | mac
      style:
  ```
### 自定义代码块展示
   想要一种mac风格的代码展示


## 添加打赏

## 文章引入图片

# 优化回到顶部按钮

# 自定义样式