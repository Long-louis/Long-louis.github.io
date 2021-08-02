---
title: hexo&git使用教程
date: 2021-08-02 19:41:49
---

## hexo同步方法

```
hexo new [layout] title
```

> > 新建页面
>
> > [layout]为页面布局，在_config.yml中规定默认布局，不填写[layout]即使用默认布局

```
hexo g #生成静态文件 -d文件生成后立即布署网站
hexo d #布署网站
```

```
hexo publish [layout] <filename>
# 发表草稿
```

```
hexo sever #启动本地服务器 默认为http://localhost:4000/
```

```
hexo clean #清除缓存文件（当对站点的更改不生效时可尝试clean）
```

## git 同步方法

### git上传

```
git add .
git commit -m "xxxxx" #引号中为同步评语
git push
```

### git下载

```
git pull
```

