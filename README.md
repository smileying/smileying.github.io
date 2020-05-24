# 说明

# 准备工作
- 安装hexo
  
  ```javascript
  npm install hexo-cli -g
  ```

- `git clone xxx`

- 切换到分支`hexo-new`
  
  ```javascript
  npm install
  ```

- 下载主题
  
``` javascript
cd 根目录
git clone https://github.com/theme-next/hexo-theme-next themes/next
```

- 主题配置文件所在位置

为了更新主题时不冲突，将`next`主题配置文件copy至`source`下: `source/_data/next.yml`

# 开始写作

## 新建文章

```
hexo new "my post"
```

## 新建页面

```
hexo new page xxx
```

## 预览

```javascript
hexo generate

hexo server 
// 本地预览
http://localhost:4000/

// 设定端口方式
hexo server -p 5000 
```

## 发布

```javascript
hexo deploy
```