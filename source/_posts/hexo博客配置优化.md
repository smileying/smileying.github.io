---
title: hexo博客配置优化
date: 2020-05-23 16:40:26
categories:
- 博客写作
tags:
- Hexo
---
# 说明
本文配置优化适合`hexo-theme-next`主题，要修改的配置copy至根目录下`_config.yml`中`theme_config`选项

# 实时预览

```javascript
// todo
```

# 侧边栏
## 增加页面-标签&分类&归档

`next`默认只有`home`和`archives`两个，可以添加更多：

```yml
menu:
  home: / || fa fa-home
  about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive

menu_settings:
  icons: true  # 是否显示各个页面的图标
  badges: true # 是否显示分类/标签/归档页的内容量
```

然后依次生成对应的页面

```javascript
hexo new page about

hexo new page tags

hexo new page categories
```

`source`目录下生成对应文件夹，比如`tags`下有一个`index.md`:

```markdown
---
title: tags
date: 2020-05-23 20:53:37
---
```

可以手动修改为：

```markdown
---
title: 标签
date: 2020-05-23 20:53:37
type: "tags"
---
```


## 作者信息展示

- 头像设置
  ```yml
  # Sidebar Avatar
  avatar:
    url: /images/smileying.gif # source目录下新建images文件夹，放置头像
    rounded: false # 是否设置圆形头像
  ```
- 信息展示
  ```yml
  # Site
  description: 'keep learning'
  keywords:
  author: smileying
  ```
- 社交信息展示
  ```yml
  social:
    GitHub: https://github.com/smileying || fab fa-github
  ```

## 文章目录展示位置

`next`主题配置：

```yml
post_navigation: left
```

## 博客底部信息展示

可以设置站点信息，备案信息等，`footer`

```yml
footer:
  since: 2020  # 建站时间
  # Icon between year and copyright info.
  icon:
    # Icon name in Font Awesome. See: https://fontawesome.com/icons
    name: fa fa-heart # 作者图标
    # If you want to animate the icon, set it to true.
    animated: false  # 图标是否闪动
    # Change the color of icon, using Hex Code.
    color: "#ff0000" # 图标颜色
  
  # If not defined, `author` from Hexo `_config.yml` will be used.
  copyright: smileying

  powered: false

  beian: # 网站备案信息
    enable: false
```

# 增加搜索

```javascript
// todo
```


- 安装
  ```javascript
  npm install hexo-generator-searchdb --save
  ```

- 根目录的`_config.yml`， 增加`search`配置:
  ```yml
  search:
    path: search.html
    fiels: post # post page all
    content: true
    format: html
  ```

- 修改`next`主题配置`_config.yml`--`theme_config`:
  
  ```yml
  local_search:
    enable: true
  ```

# 文章写作相关

## 文章增加标签或分类

默认生成的文章格式为：

```markdown
---
title: {{ title }}
date: {{ date }}
tags:
---
```

文章中增加`tags`后，回自动关联，例如

```markdown
---
title: 从0到1搭建hexo博客（1）
date: 2020-05-23 14:26:49
tags:
- Hexo
---
```

给文章添加分类后，点击【标签】可以看到已经有的具体标签，点击具体的标签可以看到该标签下的所有文章。只有添加了`tags: xxx`的文章才会被收录到标签中。

每次都要手动增加有些麻烦，可以修改下文章生成的模板

## 文章模板设置

修改`scaffolds`目录下的post.md,增加`categories`:

```markdown
---
title: {{ title }}
date: {{ date }}
categories:
tags:
---
```

这样设置后，默认新建的`post`会自动添加了`tags`/`categories`, 后面只需要增加实际的标签和分类即可。

## 文章缩略描述

```javascript
// todo
```

## 增加文章版权信息

```javascript
// todo
```

## 增加文章结束标志

```javascript
// todo
```

## 增加阅读次数、时长和访客数

```javascript
// todo
```

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

修改主题配置：

```yml
codeblock:
  # Code Highlight theme
  # Available values: normal | night | night eighties | night blue | night bright | solarized | solarized dark | galactic
  # See: https://github.com/chriskempson/tomorrow-theme
  highlight_theme: night
  # Add copy button on codeblock
  copy_button:
    enable: true
    # Show text copy result.
    show_result: true
    # Available values: default | flat | mac
    style: mac
```

## 添加打赏

```javascript
// todo
```

## 文章引入图片

```javascript
// todo
```

# 优化回到顶部按钮

```javascript
// todo
```

# 参考

https://www.qcmoke.site/blog/hexo_next.html