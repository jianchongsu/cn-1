---
date: '2009-11-06 19:55:51'
layout: post
slug: farewell-sina
status: publish
title: 别了，sinα
wordpress_id: '162'
categories:
- R
- 学习中
tags:
- R
- 实习
- 开源
- 新浪
- 程序
- COS
---

走之前用这里的电脑留个记号吧。

 

补记：回到寝室了，在sinα的实习也算是告一段落了，干脆就在这里总结一下这一段时间的经历和感受好了。

首先要说的当然还是那些被无数人实践过的结果：

企业和学校是不同的；  
职员和学生是不同的；  
报告和论文是不同的。  

不过虽然是陈词，但应该还不算是滥调，因为毕竟是自己亲身经历的，总好过凭空的想像。

在那边的工作基本上划分为两块，老师和那边的合作项目，以及sinα日常的一些事务。合作项目就不用说了，主要是数据的处理，收获还是很大的，毕竟是真真正正的数据啊。在这个项目中学到了用Prediction Strength来确定聚类数的方法，我还在想是不是可以给主站投一稿呢。结果有可能不能公开，但至少可以介绍一下方法吧。

其实真正想说的是日常的事务，尽管从“技术含量”上看远不如前者。当时几乎每天要做的工作就是定时更新几张Excel表格，里面是一些从网站上获取的数据，包括每天要更新的，每周要更新的，还有每月要更新的。而每天的操作，基本上就是Ctrl+C/Ctrl+V或者如某著名饼干产品广告说的，“框一框，拖一拖，填一填”。曾经有那么几个下午，由于实在太困，大脑几乎失去了意识，但手中的鼠标还在指定的位置进行着指定的操作，而正因为这个，我才体会到卓别林的《摩登时代》可能真的不只是一部电影。

后来，十一假期的时候，为了能够摆脱这样的处境，能够进一步解放生产力、发展生产力，我再一次向Mr. R求救。由于其中的几个网站是公开的，所以可以通过读取源代码的方式来抓取需要的信息，用到的函数主要是`readLines(url())`和一些正则表达式。等十一之后正式投入使用时，效果确实十分明显，原来要一个小时的工作，那时就只要十来分钟就行了。

当然了，Mr. R肯定不能只在这种地方发挥作用。之前提到的那个合作项目，里面的结果基本上都是用R跑出来的。当时我跟我的主管说，这个方法太新，ABAA没有办法算，所以我就用R软件了。而他们也没有像传闻那样，听到是开源免费的就一副紧张的样子。事实上，在我用过的两台电脑里面，都已经装上了R软件，版本都是2.9以上的。这离不开PLF和暑假里面几位师兄的功劳啊。
今天要走的时候，主管还特意吩咐我，给后面来实习的人写一份自动获取数据程序的说明文档。看样子，Mr. R是要继续在那里工作一段时间了。

所以呢，我有一些想法：

1. 商业公司不是坚决不用开源软件，关键是要有人推广；  
2. 要推广开源软件，就要找到它们相对于商业软件的优势；  
3. 我们其实每天都在享受开源作者的劳动果实，比如很多网站的后台，还有你吃到的“正宗宫保鸡丁”的配料。  

俗话说，一波未平，一波又起。好在现在sin这一波已经平息了，接下来，我得多花点心思到COS这一波吧……
