---
layout: post
title: "cloudflare 全球节点备忘录"
subtitle: 'cloudflare 全球节点备忘录'
author: "panmg"
header-style: text
catalog:    true
tags:
  - cloudflare ip
  - cloudflare 节点
---


具体步骤不叨叨了 自己搜索 大概就是用cloudflare的cdn 以CNAME别名方式解析  然后到各种智能dns里面a到节点就ok了  暂时收入精华博文

接入CF之后，CF会给域名分配一个入口IP，一般是美西洛杉矶那边的。这个IP其实是采用的AnyCast技术，当用户访问到时候，会就近分配一个真实的节点IP，以加快访问速度。

访问：http://{节点IP/域名}/cdn-cgi/trace。比如要查看访客的真实IP ，则访问 https://www.31du.cn/cdn-cgi/trace

 MaxCDN (StackPath) vs CloudFlare vs Amazon CloudFront vs Akamai Edge vs Fastly

需要用到的
CF:www.cloudflare.com

cfp（Cloudflare合作伙伴）
推荐笨牛:cdn.bnxb.com (介绍 lowvps.cn/bnxb-cloudflare-cdn/)

稳定很长时间的: https://cf.tlo.xyz/

https://cdn.wzfou.com/

萌精灵 https://cdn.moeelf.com/

智能解析 国内随便选 建议dnspod/dnsdun/dnsla

都比较不错 因为这三家支持智能三网/四网解析 外加搜索引擎百度等单独解析

 

下面说一下IP段 比较杂乱  可以参考CloudFlare节点IP收集(全球附亚洲节点/日本,香港,韩国,印度,美国)

这里面有一个思想 就是需要 自己添加后 不断去优化! 也就是 用各种ping命令检查一下 把 延迟比较高的换掉

> 开开车, 注意打开方式 [点这里](https://www.kspp.xyz) ,  最好手机打开, 别曝光了

******************************************节点开始*****************************

CloudFlare的节点：国内速较快的IP段：

（联通移动推荐节点）

104.23.240.0-104.23.243.254

（电信推荐CloudFlare 百度云合作 ip）

162.159.208.4-162.159.208.103

162.159.209.4-162.159.209.103

162.159.210.4-162.159.210.103

162.159.211.4-162.159.211.103

各线路推荐列表：

电信：推荐走圣何塞，例：104.16.160.* 或者上面的百度云合作 ip。

移动：推荐走移动香港, 联通有很多比如 v2ex.com， 198.41.214.162,  104.16.160.1

联通：没发布什么好线路，可走日本。日本最佳: 162.158.116.1(不可用) ,  圣何塞  104.28.16.14  , 日本:104.20.157.1

cdnjs: 104.16.133.229  v2ex: 可用
   
延迟和速度不错，IP地址：162.159.211.3-162.159.211.103

移动很不错：


	162.158.26.1
	172.68.144.1
	172.69.152.1
	104.19.195.151
	104.18.177.69
	104.25.176.1
	
可以设置用于 移动网络
	
	108.162.227.1
	162.158.4.1
	172.69.152.1
	
可以设置用于 联通网络走日本快
	
	162.158.116.1
	108.162.226.1
	
可以设置用于 默认网络

	172.68.32.1
	108.162.243.1
	108.162.245.1
	108.162.246.1
	172.68.172.1
	
可以设置用于 电信网络


CloudFlare官方公开的所有节点 https://www.cloudflare.com/zh-cn/ips/

	IPv4
	173.245.48.0/20
	103.21.244.0/22
	103.22.200.0/22
	103.31.4.0/22
	141.101.64.0/18
	108.162.192.0/18
	190.93.240.0/20
	188.114.96.0/20
	197.234.240.0/22
	198.41.128.0/17
	162.158.0.0/15
	104.16.0.0/12
	172.64.0.0/13
	131.0.72.0/22
	


	108.162.236.1/24 联通 走美国
	 172.64.32.1/24 移动 走香港
	 104.16.160.1/24 电信 走美国洛杉矶
	 ​
	 -----------------------------------------
	 ​
	 172.64.0.0/24 电信 美国旧金山
	 104.20.157.0/24 联通 走日本
	 104.28.14.0/24 移动 走新加坡
	 ​
	  （联通移动推荐节点）
	  104.23.240.0-104.23.243.254
	  
	  （电信推荐百度云合作ip）
	  162.159.208.4-162.159.208.103
	  162.159.209.4-162.159.209.103
	  162.159.210.4-162.159.210.103
	  162.159.211.4-162.159.211.103
	  
	 -----------------------------------------
	 ​
	 节点速度比较快的有：
	 104.20.157.2 
	 104.18.62.2 
	 141.101.115.3 
	 104.16.160.3
	 ​
	 百度云加速与Cloudflare合作节点还有：
	 162.159.211.4-103
	 103.21.244.0/22
	 103.22.200.0/22
	 103.31.4.0/22
	 104.16.0.0/12
	 108.162.192.0/18
	 131.0.72.0/22
	 141.101.64.0/18
	 162.158.0.0/15
	 172.64.0.0/13
	 173.245.48.0/20
	 188.114.96.0/20
	 190.93.240.0/20
	 197.234.240.0/22
	 198.41.128.0/17
	 ​
	 -----------------------------------------
	 ​
	 其它的节点还有：
	 ​
	 #适合电信的节点
	 104.23.240.*
	 ​
	 #走欧洲各国出口 英国德国荷兰等 延迟比美国高一些 适合源站在欧洲的网站
	 172.64.32.*
	 ​
	 #虽然去程走新加坡，但是回程线路的绕路的，实际效果不好，不推荐
	 104.16.160.*
	 ​
	 #圣何塞的线路，比洛杉矶要快一点，推荐
	 108.162.236.*
	 ​
	 #亚特兰大线路，延迟稳定，但是延迟较高
	 ​
	 #适合移动的节点
	 ​
	 162.158.133.* 
	 #走的丹麦，这一段ip只有部分能用，可以自己试一下。绕美国。
	 ​
	 198.41.214.*
	 198.41.212.*
	 198.41.208.*
	 198.41.209.*
	 172.64.32.*
	 141.101.115.*
	 #移动走香港的IP段有很多，以上并不是全部。CF移动走香港的分直连和走ntt的效果都挺不错的，不过部分地区晚上还是会丢包。
	 ​
	 172.64.0. *
	 #这是走圣何塞的，一般用香港的就行
	 172.64.16.* 
	 #欧洲线路.绕
	 ​
	 -----------------------------------------
	 ​
	 电信部分
	 大多数省直接使用1.0.0.0即可，延迟低，丢包少，
	 ​
	 -----------------------------------------
 ​
 #移动部分
 ​
 #新加坡
  104.18.48.0-104.18.63.255
 104.24.112.0-104.24.127.255
 104.27.128.0-104.27.143.255
 104.28.0.0-104.28.15.255
 ​
 #圣何塞 
 104.28.16.0-31.255
 104.27.144.0-243.254
 104.23.240.0-243.254
 ​
 #香港cloudflare1-100g.hkix.net
 1.0.0.0-254
 1.1.1.0-254
 ​
  #香港直连
 104.16.0.0-79.255
 104.16.96.0-175.254
 104.16.192.0-207.255





******************************************节点结束*****************************

所有这些节点 摘自各个博主  不保证效果  , 只有自己去测试 筛选

 

国内的CDN譬如 dnspod/ dnsdun/ dnsla/ 阿里dns /百度DNS/ 华为云dns /京东云dns / cloudxns /蓝汛 网宿 Azure之类

 

其他参考资料

https://www.shanyemangfu.com/cloudflare-hk.html (我的启蒙贴)

https://zhang.ge/5149.html

https://www.wanvi.net/10187.html

Cloudflare免费版详细使用教程 https://www.imhunk.com/cloudflare-tutorials/

 