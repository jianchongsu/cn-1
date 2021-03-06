---
date: '2011-09-12 21:46:22'
layout: post
slug: layer-graphics-device
status: publish
title: 中秋献礼——Layer图形设备
wordpress_id: '575'
categories:
- R
- 学习中
tags:
- GUI
- Layer
- 图层
- 图形设备
- 软件包
- R
- 图形
- GTK+
---

你在用R画图的时候，是否会遇到以下的麻烦：

	
  * 加图例或文字时总是对不准坐标，要花很多精力调整元素的位置；
	
  * 某个细节出错，整幅图得重新绘制；
	
  * 想要更酷的平移、拉伸、旋转操作，就好像在Gimp或Photoshop里面一样；
	
  * 想更方便地使用字体，特别是中文的显示。


于是接下来就有一个好消息和一个坏消息。好消息是有一个软件包可以解决上面的大部分问题了，而坏消息是这个包仍然处于开发阶段，所以各种bug是难以避免的。今天恰逢中秋，我便把这个自己编写的Layer软件包介绍给大家，算是送给大家的一份小礼物。

Layer顾名思义，指的是图层，而这个绘图设备正是采用了图层的思想。在你用Layer画图时，你可以将不同的图形元素放在不同的层上，彼此之间互不影响。例如，你可以将图例单独建立一个图层，当图例移动时，下层的图形并不会发生变化，再加上一定的鼠标操作，就可以方便地绘制出美观的图形。

为了让大家能直观地感受Layer的操作，下面给出了一段Layer的操作演示视频。

<p><center><embed src="http://player.youku.com/player.php/sid/XMzAzNDkyNTU2/v.swf" allowFullScreen="true" quality="high" width="480" height="400" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"></embed></center></p>

此外，Layer有着更方便的字体支持。在打开Layer图形设备时，你可以指定一个ttf字体文件作为图形字体的来源，如果参数为`NULL`，则图形会使用软件包自带的[文泉驿](http://wenq.org)微米黑字体。

Layer软件包的下载地址如下。需要说明的是，Layer需要GTK+环境的支持，对于Windows用户，如果你已经安装了GTK+环境，请选择第二个下载地址；如果尚未安装，可以直接下载第三个文件（软件包中附带了GTK+）。

[源代码](https://bitbucket.org/yixuan/cn/downloads/Layer_0.1-0.tar.gz)

[Windows二进制包](https://bitbucket.org/yixuan/cn/downloads/Layer_0.1-0.zip)

[Windows二进制包（含GTK+运行库）](https://bitbucket.org/yixuan/cn/downloads/Layer.zip)
