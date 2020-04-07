---
layout: post
title: "Fiddler抓包工具手机添加代理后连不上网"
subtitle: 'Fiddler抓包工具手机添加代理后连不上网'
author: "panmg"
header-style: text
catalog:    true
tags:
  - Fiddler IOS连不上代理
  - Fiddler IOS

---

## Fiddler抓包工具总结

序章
Fiddler是一个蛮好用的抓包工具，可以将网络传输发送与接受的数据包进行截获、重发、编辑、转存等操作。也可以用来检测网络安全。反正好处多多，举之不尽呀！当年学习的时候也蛮费劲，一些蛮实用隐藏的小功能用了之后就忘记了，每次去网站上找也很麻烦，所以搜集各大网络的资料，总结了一些常用的功能。

参考地址:  https://www.cnblogs.com/yyhh/p/5140852.html
 

## Fiddler抓包工具手机添加代理后连不上网亲测可用 ios13版本

参考地址: https://www.jianshu.com/p/ad84b9094cb7  


2、手机端用浏览器访问http://IP:端口，观察网络是否访问成功。

3、添加代理后连不上网的解决方法

a、关闭电脑防火墙

b、检查Fiddler需要用到对应的.net framework,在Help->About 即可查看需要的版本（安装之后重启电脑）

c、打开注册表（cmd-regedit），在HKEY_CURRENT_USER\Software\Microsoft\Fiddler2下创建一个DWORD，值置为80（十进制）

编写fiddlerScript rule，点击Rules->Customize Rules，用Ctrl+F查找OnBeforeRequest方法添加一行代码

	if (oSession.host.toLowerCase() == "webserver:8888"){
	oSession.host = "webserver:80";
	}

设置完之后重启Fiddler即可。






>> 开开车, 注意打开方式 [JAV高清名优](https://www.kspp.xyz)

>推廣 每日熱點   [cocook 每日熱點](https://blog.cocook.cn/)

