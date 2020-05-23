---
title: 搭建hexo博客
date: 2020-05-23 14:26:49
tags:
---

# 1. 开始

## hexo

官网： https://hexo.io/

```javascript

// 1.安装hexo-cli
npm install hexo-cli -g

// 2.初始化blog目录
hexo init myblog

// 3.安装依赖包
cd myblog
npm install

// 4.启动

hexo server

// 5.本地预览
http://localhost:4000/

```


初始化的博客采用的是默认主题，我们可以更换一个自己喜欢的主题

# 2. 设置主题

### 2.1 选择主题next

选择一个自己喜欢的主题，这里选择我选了next：

github地址： https://github.com/theme-next/hexo-theme-next

### 2.2 主题设置

#### 2.2.1 主题下载

```javascript
cd myblog
git clone https://github.com/theme-next/hexo-theme-next themes/next
```

下载完成之后会在`themes`目录下看到`next`


#### 2.2.2 主题设置

修改根目录下的_config.yml

```javascript
theme: next
```

### 2.3 预览新的主题


```javascript
hexo generate
```
重启本地服务之后访问http://localhost:4000/， 也可以采用新的端口：


```javascript
hexo server -p 5000
```

`server`详细的用法见官网：
https://hexo.io/docs/server.html

# 3. 设置博客地址

下面内容的前提条件：已经有一个github账号，SSH key已经配置好

### 3.1 创建仓库

名称形式： `你的github用户名.github.io`， 则博客的访问地址就是：https://smileying.github.io/

注意点：
- 必须是用户名，其他名称不可以

### 3.2 发布

官网文档：https://hexo.io/docs/one-command-deployment#content-inner


- 安装`hexo-deployer-git`:

```javascript
npm install hexo-deployer-git --save

```

- 修改根目录`_config.yml`:

```javascript
deploy:
  type: git
  repo: github仓库地址
  branch: master
  message: update blog
```

### 注册域名

如果有需要，可以注册域名，然后绑定，这里不做详细介绍

# 创建一篇博客