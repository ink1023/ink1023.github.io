---
layout: post
title: 使用LAMP搭建网站
description: >
  
excerpt_separator: <!--more-->
---
*[LAMP]: 在Linux系统下搭建Apache+PHP+Mysql环境

<!--more-->

* [一台Linux服务器](#一台linux服务器)
* [安装LAMP](#安装lamp)
	* [安装Apache（web服务器）](#安装apacheweb服务器)
	* [安装MySQL （数据库）](#安装mysql-数据库)
	* [安装PHP（php脚本解析器）](#安装phpphp脚本解析器)
	* [修改apache的默认首页为index.php](#修改apache的默认首页为indexphp)
	* [让我们来测试一下吧](#让我们来测试一下吧)

# 一台Linux服务器
牛客网为了推广，来找慧河工作室发福利，每个人都可以免费体(bai2)验(piao2)一年的华为云服务器，于是我也开通了一台。

> 服务器配置信息
> 1vCPUs | 2GB | sn3.medium.2
>  Ubuntu 18.04 server 64bit

登陆服务器后先更新一下软件包（可选）

> sudo apt update             # 获取最新资源包
> sudo apt upgrade           # 本机软件全部更新
> sudo apt dist-upgrade    # 本机系统软件更新

# 安装LAMP
## 安装Apache（web服务器）
> apt install apache2         # 安装Apache

命令执行后会提示你即将安装的apache软件包的信息，问你是否执行（[Y/n]），输入 y 回车执行安装。
> systemctl status apache2   # 检查是否开启Apache，一般安装完会默认开启。

你可以尝试着关闭或重启apache服务
> systemctl start apache2    # 开启apache服务
> systemctl stop apache2    # 关闭apache服务
> systemctl restart apache2    # 重启apache服务

华为云的这个服务器为了安全起见默认并未开启21、80、443、ICMP等端口，所以我们现在还不能使用FTP协议、HTTP协议、HTTPS协议以及去ping它，为了能访问到我们的apache，我们需要在华为云控制台的安全组策略中添加允许80和443端口流入的规则。

好了，现在在浏览器里输入你的服务器的公网IP，你就能看到apache的默认页面了。

## 安装MySQL （数据库）
**注意要在华为云安全策略里放行3306端口！否则无法远程访问MySQL的服务**
> apt install mysql-server       # 安装MySQL

提示[Y/n] 输入 y 确定
接下来的mysql配置教程可以参考[这篇文章](https://www.cnblogs.com/opsprobe/p/9126864.html)，我就是按照这个配置成功了的。（其实是因为我懒得写了）

## 安装PHP（php脚本解析器）

> apt install php       #安装PHP

提示[Y/n] 输入 y 确定

> php -v     #可以查看一下PHP版本，顺便检查一下是不是安装好了

## 修改apache的默认首页为index.php

打开apache的这个配置文件
> vim /etc/apache2/mods-enabled/dir.conf    
> 
按 i 进入编辑模式，用方向键移动光标，编辑文件使 index.php 放在第一位（原来不在第一位）


> < IfModeule mod_dir.c>
> ---------DirectoryIndex ==index.php== index.html index.cgi index.pI index.xhtml index.htm
> < /IfModeule>
>  '#  vim: syntax=apache ts=4 sw=4 sts=4 sr  noet

按ESC键退出编辑模式，输入 :wq 回车保存退出。

然后我们重新启动一下apache服务以便使配置生效
> systemctl restart apache2

## 让我们来测试一下吧
在/var/www/html中创建一个名为index.php的新文件。
> vim /var/www/html/index.php

输入以下内容

``` php
<?php

phpinfo();

?>
```
保存并退出该文件。

访问你的服务器的ip，不出意外的话，你将会看到你刚刚新建的测试文件index.php中phpinfo();命令输出的php信息