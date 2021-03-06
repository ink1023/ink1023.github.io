---
layout: post
title: 静态网站和动态网站
description: >
  
excerpt_separator: <!--more-->
---

![静态网站还是动态网站？](https://i.loli.net/2019/12/04/cL5xNjhA8wMWF3Z.png)
<!--more-->


## 概念与特点
### 静态网站

> 1. 静态网站是最初的建站方式，浏览者所看到的每个页面是建站者上传到服务器上的一个 html 文件，这种网站每增加、删除、修改一个页面，都必须重新对服务器的文件进行一次下载上传。网页内容一经发布到网站服务器上，无论是否有用户访问，每个静态网页的内容都是保存在网站服务器上的，也就是说，静态网页是实实在在保存在服务器上的文件，每个网页都是一个独立的文件；
> 2. 静态网页的内容相对稳定，因此容易被搜索引擎检索；
> 3. 静态网页没有数据库的支持，在网站制作和维护方面工作量较大，因此当网站信息量很大时完全依靠静态网页制作方式比较困难；
> 4. 静态网页的交互性较差，在功能方面有较大的限制。

### 动态网站


>1. 交互性：网页会根据用户的要求和选择而动态地改变和响应，浏览器作为客户端，成为一个动态交流的桥梁，动态网页的交互性也是今后 Web 发展的潮流。
>2. 自动更新：即无须手动更新 HTML 文档，便会自动生成新页面，可以大大节省工作量。
>3. 因时因人而变：即当不同时间、不同用户访问同一网址时会出现不同页面。

## 我的理解

 - 上面的话都太官方了（我复制粘贴的……<i class="fas fa-smile"></i>），我个人的理解就是：服务器输出的内容和服务器上的存放资源内容是否完全一致，一直就是静态，反之就是动态。
 - 对于一个静态网站，服务器只需要将HTML、JS、CSS这些文件的内容简单的直接打印输出就好。你把一个html页面文件丢到服务器上，用户要访问这个页面文件的时候服务器再把这个html文件原封不动的丢给你的浏览器，你的浏览器再把这个html文件解释成你看到的页面。
 - 对于一个动态网站，你在浏览器的查看源代码页面看到的内容似乎看似就是一个存放在服务器上的静态页面，但实际不是这样的的，这些内容是服务器的在预先写好的程序经过了各种逻辑判断与分支跳转后才输出给你的，你访问同一个地址（页面）在不同的条件下（比如你是否登录，）服务器给你输出的内容（我指的是输出的页面源代码）是不同的。
 - 现在的网站大都采用动态输出页面内容的方法是有原因的，打个比方，你到学校教务处的网站查询你的期末考试成绩，采用动态技术的话你要访问的查询页面对应的那个服务器上的程序大概是这样的逻辑

>  1. 接受你的查询关键字（比如你的名字或者学号）并且连接数据库获取你的考试成绩
>  2. 输出网页的头部（一个网页必要的内容）
>  3. 输出网页的主体部分（其中自动嵌入你的姓名、考试成绩等信息）
>  4. 输出网页结尾部分（一个网页必要的内容）

 - 而如果你们学校的考试成绩查询网站是个静态的网站<i class="fas fa-meh-blank"></i>，那么学校就得为每一个同学都制作一个成绩信息展示页面，然后在一个成绩查询页面输入你的学号后那个页面就把你导航到你的成绩信息所在的那个页面，如果你们学校有100人，那么难道就要制作100个下面这样的成绩页面？（教务处的老师发出反996抗议）
 
>  1. 网页的头部（一个网页必要的内容）
>  2. 网页的主体部分（其中包含你的姓名、考试成绩等信息）
>  3. 网页结尾部分（一个网页必要的内容）

 - 而且如果别人知道了你的成绩展示地址别人一访问这个页面就能直接看到了你的个人信息了，更糟的是别人就会知道你的成绩，发现你其实是个学渣，后果无法想象<i class="fas fa-meh"></i>。


 - 在上述这种场合显然动态网站更适合一些，不过在如今静态网站也有它生存的空间，静态网站对于服务器性能的要求非常低，所以在于一些内容简单且很长时间也不用更新的网站上会有它的用武之地，比如你现在看到的这个博客网站就是一个静态网站（其实这句话不完全正确，回头我把这个博客的搭建方法写出来的时候再细谈）。

 - 当然，如果你是土豪，就是一年几百几千RMB的服务器随便买，连眼睛都不带眨一下的那种，还关心什么静态动态服务器的选择，阿里云ECS主页就挂一个纯html页面用来炫富完事了<i class="fas fa-grin-beam-sweat"></i>。


