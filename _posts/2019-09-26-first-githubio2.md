---
layout: post
title: "My First github blog"
subtitle: 'From Vim to Spacemacs'
author: "panmg"
header-style: text
tags:
  - github.io
  - Emacs
---

### 修改hosts 文件 github clone 加速 访问 github 加速


我们可以通过修改hosts文件来提速,获取github的IP地址

> 1.手动访问：https://www.ipaddress.com/ 网址，然后依次获取以下三个网址的IP

github.com
github.global.ssl.fastly.net
codeload.github.com

这是我获取的IP

192.30.253.113 github.com
151.101.25.194 github.global.ssl.fastly.net
192.30.253.121 codeload.github.com
--------------------------------------------------------------------------------------
修改系统本地的hosts文件，添加内容，Windows系统的hosts文件路径：C:\Windows\System32\drivers\etc\hosts


> 2. 打开cmd 界面

C:\Users\tomsun>ipconfig /flushdns
Windows IP 配置
已成功刷新 DNS 解析缓存。





