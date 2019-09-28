---
layout: post
title: "使用 github 免费 建 自己的 博客"
subtitle: '使用 github.io 免费 建 自己的 博客'
author: "panmg"
header-style: text
tags:
  - github
---

### 使用 github 免费 建 自己的 博客

github.io 是 github 机构提供的 免费服务, 可以通过建一个仓库上传 MD 文件自动 模板化

有什么优势:
* 稳定
* 不会删数据
* 免费的午餐

### 网络上的 一些 常用的搭建文章

常见的两种, 可以自行百度
* 使用github教程推荐的 方式
* 使用 hexo方式搭建

### 最简单的方式 
### 1. 直接 clone 一个仓库

打开 github 网站, 全网所都 github.io

返回结果, 哇, 很多, 自己选, start 几千上的

	DataScienceSpecialization/DataScienceSpecialization.github.io
	http://DataScienceSpecialization.github.io
	1.4k	 CSS	Updated on 30 Jun
	
	academicpages/academicpages.github.io
	Github Pages template for academic personal websites, forked from mmistakes/minimal-mistakes
	1.9k	 JavaScript	MIT license	Updated yesterday
	
	Huxpro/huxpro.github.io
	My Blog / Jekyll Themes / PWA
	4.6k	 CSS	Apache-2.0 license 	Updated 6 days ago	5 issues need help
		
	qiubaiying/qiubaiying.github.io
	BY Blog ->	blog  jekyll-theme  github-pages
	1.7k	 HTML 	MIT license	Updated 23 hours ago

选一个进去看看是否是 标准的 gitio 版本, 文章 都在_posts 下面, 直接clone, 或者下载zip, 

### 2. 改仓库名称

找到settings rename

修改仓库名称为 XXX.github.io, 改成自己用户名, 可以参考下面的 

	qiubaiying/qiubaiying.github.io
	Huxpro/huxpro.github.io
	academicpages/academicpages.github.io

找到 GitHub Pages , 查看一下是否绑定的 自定义域名, 有的话删除

### 3. 有域名修改域名, 没有就直接完成了

此时你直接打开 xxx.github.io, 发现 别人的博客已经到你的 `用户名.github.io` 上面了

找到 GitHub Pages 
* 如果自己有域名, 把自己的域名配置上面
* 到自己的域名管理商, 添加一个 CNAME 记录, 将域名地址 指向 value [`用户名.github.io`]
* 使用自己的域名访问, 看看有没有出现, 如果出现了, 恭喜

### 4. 使用自定义域名 实现 https访问

现在github 也提供 https 的免费证书, 使用自己的域名解析后 会出现, 一般 等待证书生成成功后 就可以使用, 我们不采取这种方式, github国内访问太慢
我们用 cloudflare cdn 加速, 不仅可以加速, 还可以提供免费的 https

参考 这篇文章  https://www.jianshu.com/p/653b5682e2bd

由于使用cloudflare 配置cdn 需要修改 dns 解析, 会影响原有的 域名提供商的 dns

提供另一种方式
* 通过 这个地址 : https://dns.mzr.me/ 可以登录cloudflare控制面板
* 可以查看他的开源地址及文档 https://github.com/ZE3kr/Cloudflare-CNAME-Setup
* 使用这个面板 可以 不修改 原域名厂商的 dns解析
* 登录后直接在 这个面板内 解析域名, 添加一条cname 解析

	记录类型		主机名	内容		
	CNAME	cocook.cn	panmingguang.github.io

* 面板下方会出现 很多课选择的 在域名上修改的 解析方式 ip4 ip6 cname ns等
* 到自己的域名上 修改原来的 解析 cocook -> 到面板上提供的 地址
* 此时 跳转地址,  自己域名商 cocook -> cloudflare( 映射域名 cname或IP ) -> 跳到 panmingguang.github.io
* 此时访问  cocook 已经可以访问自己的博客, 但是发现并部署https, 自己输入https 的话可以正常访问
* 到cloudflare 自己的域名管理控制台, 找到 SSL|TLS -> Edge Certificates -> Always Use HTTPS 开启

### 大功告成, 花了点时间, 快来写自己的第一遍博客吧, 写完发布提交后 稍等片刻 才能在 网址上看到新博客

我一般是用md 格式写博客, 可移植














