---
title: 开始搭建hexo博客
date: 2020-05-23 14:26:49
categories:
- 博客写作
tags:
- Hexo
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
```

### 博客源码存储

deploy后悔发现github仓库并没有本地的所有代码，为方便存储可以新建一个分支存储源码, 这样可以像管理代码一样来管理博客的原始文件及配置等

```javascript
git init
git  checkout -b hexo
git remote set-url --push origin  仓库
git push --set-upstream origin hexo // hexo分支用来存储源码
```

注意：
安装的主题next可能会提示已经是一个仓库

```
hint: If you meant to add a submodule, use:
hint: 
hint:   git submodule add <url> themes/next
hint: 
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint: 
hint:   git rm --cached themes/next
```

### 注册域名

如果有需要，可以注册域名，然后绑定，这里不做详细介绍

# 4. 创建一篇博客&常用命令

```javascript
hexo new 'my first blog' // 会在source文件目录下生成飞鹰的.md文件

hexo generate

hexo deploy
```


常用命令：

```javascript
hexo new  "postname" // 新建文章
hexo new page "pagename" // 新建页面
hexo generate // 生成静态文件值public文件夹
hexo server // 本地预览端口，默认4000
hexo deploy // 部署到github
```

缩写：
```javascript
hexo n -> hexo new
hexo g -> hexo generate
hexo s -> hexo server
hexo d -> hexo deploy
```


# 5 基础博客配置优化

###  5.1 基础配置

详细配置见根目录下`_config.yml`， 可以修改博客的基本信息，作者名称，展示等

- `scheme`: 选择主题
- `#Site `: 基本信息
- `# URL`: 网站域名信息
- `# Directory`: 关于文件目录的一些配置
- `# Writing`: 关于博客写作的一些配置
- 增加`archive_generator`: 归档页的分页设置
- 增加`tag_generator`: 标签页的分页设置


# 5.2 `next` 主题美化

## 不改变next的主题配置文件的设置方法
https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/DATA-FILES.md

#### 5.2.1 主题选择

`next`支持的默认主题有四种，可以在`themes/next`目录下`_config.yml`文件中看到，可以切换不同的主题，选择一种


```yml
# Schemes
# scheme: Muse
# scheme: Mist
# scheme: Pisces
scheme: Gemini
```

#### 5.2.2 `next`主题的其他设置

- `custom_file_path`: 个性化配置
- `favicon`: 可以更换网站图标
- `footer`: 页面底部信息  `copyright` 、备案信息等
- `menu`: 设置博客各个页面的相对路径
- `# Sidebar Avatar`: 设置导航，个人头像，展示位置等
- `# Social Links`: 可以配置gihub等社交网站信息


#### 5.2.3 个性化配置


# 参考
https://www.cnblogs.com/tengj/p/5352572.html

https://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html


https://www.jianshu.com/p/8e9000cc1015

https://blog.csdn.net/nightmare_dimple/article/details/86661502

https://blog.csdn.net/weixin_44815733/article/details/88817220

http://shenzekun.cn/hexo%E7%9A%84next%E4%B8%BB%E9%A2%98%E4%B8%AA%E6%80%A7%E5%8C%96%E9%85%8D%E7%BD%AE%E6%95%99%E7%A8%8B.html