---
title: 使用 termux搭建hugo并部署到github
date: 2024-09-17
type: blog
authors:
  - name: Ljg
    link: https://github.com/adallei
    image: https://github.com/adallei.png
excludeSearch: true
---

{{< callout >}}
这篇文章是使用termux搭建hugo并部署到github的一些基础教程,进阶教程会在后续写出。
{{< /callout >}}
<!--more-->
## 前言
Hugo是由go语言编写的静态网站生成引擎，以其速度著称，号称是“The world’s fastest framework for building websites”。<br>
Termux是在Android系统上的一款终端模拟器。功能非常强大，可以运行一些linux应用。所以可以用termux当作终端来搭建hugo。<br>
{{< callout type="info" >}}
此文章将分成搭建和部署两部分介绍。
{{< /callout >}}
## 搭建

#### 准备工作
> 在正式开始之前需要先下载termux并安装相关软件包才能开始正式搭建。

* ##### 下载termux
* 在[GitHub](https://github.com/termux/termux-app/releases)或者[F-droid](https://f-droid.org/packages/com.termux/)上下载并安装打开termux<br>
 * 获取存储权限<br>
 `termux-setup-storage`
 * 更新包<br>
 `pkg upgrade -y`
 * 安装相关工具(git和vim)<br>
 `pkg install git vim -y`
 
#### 安装&使用
* ##### 安装hugo
 * 安装<br>
 `pkg install hugo -y`
* ##### 创建网页
 * 建立新的站点<br>
 `hugo new site (你的站点名)`
 * 下载&安装主题<br>
 `cd (你的站点名)`<br>
 `cd themes`<br>
 `git clone (主题下载地址)`
 > hugo默认是没有主题的，所以你需要先安装一个主题才能使用hugo。<br>
在网上找到一个hugo主题然后把(主题下载地址)替换成你找到的主题。<br>
或者直接下载主题的源码解压到themes目录。<br>
主题的安装方式可能会略有不同，你需要找到主题官方发布的安装教程按照教程安装。
 * 启动服务<br>
 `hugo server`
 > 注意要在站点的根目录执行，也就是(你的站点名)这个目录。<br>
启动成功后可以在浏览器输入localhost:1313浏览站点<br>
输入这个指令默认的配置文件是toml格式的，如果你习惯使用yaml格式就输入<br>
`hugo convert toYAML [flags] [args]`<br>
将内容目录中的所有前置内容转换为使用yaml格式的前置内容。

* ##### 写文章
 * 新建文章<br>
 `hugo new content/(文章目录)…/文章名.md`
 > 文章的front matter结构是:<br>
title: 文章的标题<br>
date: 文章的发布日期（通常为 YYYY-MM-DD 格式）<br>
author: 作者的名字<br>
draft: 是否为草稿（true 或 false）<br>
tags: 标签列表，用于组织文章<br>
categories: 分类列表，用于归类文章<br>
slug: URL 中的自定义短路径<br>
summary: 文章的摘要，通常用于列表页面<br>
keywords: 页面关键词，用于 SEO<br>
description: 页面描述，用于 SEO。<br>
aliases: 旧网址的重定向列表<br>
type: 内容类型，决定该内容使用的模板<br>
layout: 指定使用的模板布局<br>
文章采用Markdown标记语言，使用方法可以去[Markdown官方教程](https://markdown.com.cn/)查看。

* ##### 小结
 以上就是网页的基础搭建，如果想要定制你的hugo 或遇到了什么错误请参阅[**hugo官方文档**](https://gohugo.io/)或[**hugo中文文档**](https://hugo.opendocs.io/getting-started/)。
## 部署

#### github上的准备 
* ##### 账户&仓库
 * 注册[**github**](github.com)账户<br>
 * 建立远程仓库
 > 在github创建new repository，注意仓库名一定要是你的 github用户名.github.io<br>
其他的可填可不填。
 * 设置仓库<br>
  进入仓库设置/Pages<br>
  把Build and depolyment下面的source选项改成Deploy from a branch。
  
#### git的使用
* ##### 配置
 * 进入站点中的public目录<br>
 `cd /…/(你的站点路径)/public`
 > 如果public下没有文件就需要在(你的站点路径)下输入<br>
`hugo -D`
<br>生成静态文件。
 * 配置用户信息<br>
  `git config --global user.name "(你的用户名)"`<br>
  `git config --global user.email "(你的电子邮件)"`<br>
  >注意:(你的用户名)和(你的电子邮箱)不一定要和GitHub上的相同。
  * 初始该目录为git仓库<br>
  `git init`
  > 如果输入一次没有成功就输入两次。
  * 添加远程仓库<br>
  `git remote add (别名，一般为origin) "(仓库的SSH链接)"`
  > 使用git remote add添加SSH链接首先要先知道github仓库的SSH链接。<br>
  在仓库首页点击code再点击SSH就能看到仓库的SSH链接了。
  * 查看仓库信息<br>
  `git remote -vv`
  * SSH密钥生成密钥对<br>
  `ssh-keygen -t rsa -C “(备注)”`
  > 其中(备注)可不写。<br>
获取生成的公钥一般在Termux的home目录下的.ssh文件,可以在安桌原生文件中打开，也可授权给别的应用打开。<br>
找到.ssh目录下的id.rea.pub文件以文本形式打开复制里面所有内容,将复制的内容粘贴到GitHub。<br>
在GitHub网站点击自己的头像，再点击Settings，找到SSH and GPG Keys
点击New SSH Kays把刚刚复制的内容粘贴到key的下面随便取一个Title点击Add SSH Key添加密钥，如果需要输入密码就输入GitHub的密码。
 * 提交public下所有文件到数据暂存区<br>
  `git add `
 * 提交文件更改<br>
 `git commit -m "(推送信息)"`
 * 推送<br>
 `git push -u origin main`
 > origin是上面提到的别名。<br>
main代表主分支，如果推送到main分支失败<br>
可以使用命令:<br>
`git pull -f origin main`<br>
强制推送，使用此代码会强制用本地代码覆盖远程仓库代码。<br>
如果以上办法不行，就输入:<br>
`git push -u origin master`<br>
master是默认分支名。<br>
推送之后需要到GitHub仓库中的设置中的Pages把Branch改成master。
* ##### 小结
以上就是hugo在GitHub上的部署。<br>
还有另一种利用GitHubActions部署的方法请查阅[**Hugo官网**](https://gohugo.io/hosting-and-deployment/hosting-on-github/)。<br>
最后，感谢你的观看，希望这些对你有帮助！
 