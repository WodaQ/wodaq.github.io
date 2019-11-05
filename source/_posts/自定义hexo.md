---
title: 自定义hexo
date: 2019-11-05 10:57:05
type: "hexo"
tags:
    - hexo
---

>在配置好主题后，需要加上自己的头像、图标等等等等，在配置过程中也遇到一些问题，在此记录一下。

- 站点配置是指你blog文件夹下的_config.yml
- 主题配置是指你themes/你选择的主题，文件夹下的_config.yml

### 1,配置头像
打开主题配置，找到对应字段
```
avatar: /uploads/Head_portrait.png
```
我在配置头像的时候遇到一些小问题，开始是在sources下新建了个文件夹assert，然后avatar的值设置的是assert/head.jpg。就出现了刚开始配置好后主页的头像显示正常，但是切换到其他页面就显示不出来，一般这个问题就算图片的路径设置的不对

### 2,设置网站标题，作者，语言等

打开站点配置，修改下面对应的值
```
# Site
title: CJ'S BLOG
subtitle: CJ的博客小站
description: 欢迎来到CJ的技术分享站~
author: CJ
language: zh-Hans
timezone:
```
### 3,设置菜单
在主题配置里找到menu字段,加上对应的路径就好了
```
主页: /
  归档:  /archives/index.html
  随笔: /tags/随笔/
```
### 4，设置网页标签页的小图标
在主题配置里找到favicon字段，设置方法和头像一样
```
avatar: /uploads/Head_portrait.png
```

参考文章：
- [HEXO搭配Next主题修改博客](http://blog.codesfile.com/2017/12/16/HEXO%E6%90%AD%E9%85%8DNext%E4%B8%BB%E9%A2%98%E4%BF%AE%E6%94%B9%E5%8D%9A%E5%AE%A2/)
- [Hexo yilia 主题一揽子使用方案](https://cloudy-liu.github.io/2018/04/07/Hexo_yilia_%E4%B8%BB%E9%A2%98%E4%B8%80%E6%8F%BD%E5%AD%90%E4%BC%98%E5%8C%96%E6%96%B9%E6%A1%88/#%E4%BF%AE%E6%94%B9%E4%BB%A3%E7%A0%81%E5%9D%97%E6%A0%B7%E5%BC%8F)
