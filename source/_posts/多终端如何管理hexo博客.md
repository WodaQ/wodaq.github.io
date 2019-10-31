---
title: 多终端如何管理hexo博客
date: 2019-10-31 11:00:25
tags:
---

---
title: 多终端如何管理hexo博客
date: 2019-10-31 11:00:25
tags:
---


>问题来了，如何在多个终端同时管理更新这个博客呢，一般都有公司PC，家里的PC，自己的linux服务器，自己的macbook。都应该可以统一管理这个blog才对。哇这个我整了很久，看了很多文章，最后好不容易琢磨出来了,在这里再次记录一下。

先说一下大概思想，gitpage展示的页面是mster分支，master分支是我们通过g，d命令生成的public文件夹下的静态文件，那么我们另外开一个分支叫backend，用来存放所有的代码，如果需要在不同的终端下更新或者管理博客，只需要在此终端pull一下backend的最新代码，然后在本地修改完成后，重新g，d发布到master分支就可以了。

这个操作的重点就在于，你需要在每个终端都配同样的环境，node，hexo，git之类的。

原理就是利用d命令每次都是发布到我们指定的master分支，然后我们找个新分支来存生成静态文件的源代码

去git另开一个分支backend

然后在另一台终端，pc也好linux机器也好，我是一开始在linux上弄，然后再到本地pc上弄的。

首先新建一个空的文件夹blog,然后cd进去
```
hexo init
hexo install
```
把要装都都装好，然后
```
git init
//绑定到git
git remote add origin git@github.com:WodaQ/wodaq.github.io.git
```
再拉取所有代码，然后丢弃本地，强制拉取远端分支。
```
git fetch --all
git reset --hard origin/master
git checkout -b backend origin/backend
git reset --hard origin/backend
git pull //可以省略

hexo new "PC test"
git add .
git commit -m "PC test"
git pull
```
全部推送到git的backend上

然后重新g,d生成新的静态文件发布到master分支上。
通过git命令把linux和PC的代码同步一下，最后再去访问博客页面应该是可以看到pc test，也可以看到之前在其他终端上发布的内容


### 遇到的错误和坑
```
Error: EPERM: operation not permitted, mkdir 'E:\study\myself\webServer\blog\.deploy_git\css'
```

这个一般就是权限问题，用管理员方式打开cmd在推送
但是我用管理员方式打开依旧有问题，但是我用管理员方式打开powershell运行发现多了一个提示如下，我就去安装posh-git了，安装了之后还没用
```
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
Error: EPERM: operation not permitted, mkdir 'E:\study\myself\webServer\blog\.deploy_git\archives'
E:\study\myself\webServer\blog警告: Missing git support, install posh-git with 'Install-Module posh-git' and restart cmder.
```

始终搞不定，莫名奇妙出现的，明明之前还是好好的

后面我实在没得办法选择重启一下电脑，然而在重启的时候突然弹了个错误框，还说正在配置我的电脑，之后我的win10就自动升级了，心里只有一万句mmp要讲。

遇事不决重启电脑就完事