---
date: '2011-06-29 15:17:20'
layout: post
slug: convolution
status: publish
title: 卷积
wordpress_id: '531'
categories:
- R
- 学习中
tags:
- 卷积
- 多项式
- 程序
- R
---

又是三个月没写博客了，或许是因为越来越浮躁了吧，都不知道自己应该做什么了。今天因为论坛上的[一个帖子](http://cos.name/cn/topic/104640)，偶然想起了前段时间看的有关卷积的一些东西，于是想着在这里整理一下。

如果学习过概率论的话，应该对卷积不会陌生——求两个独立随机变量之和的密度函数，就是将这两个变量的密度函数进行卷积运算，它实际上就是一个积分。不过今天在这里谈的离散的情形，所以我们来看看下面的这个例子：

设离散随机变量 $$X$$ 取值为 $$0, 1, 2, \ldots, n$$ 的概率分别为 $$p_0,p_1,\ldots,p_n$$，另一个离散随机变量 $$Y$$ 取值为 $$0, 1, 2, \ldots, m$$ 的概率分别为 $$q_0,q_1,\ldots,q_m$$，现在要求 $$Z=X+Y$$ 的分布列。

这个问题并不难，比如说，要使 $$Z=0$$，则一定有 $$X=0$$ 且 $$Y=0$$，于是 $$P(Z=0)=p_0q_0$$。再考虑 $$Z=1$$，它分两种情况，$$X=0,Y=1$$ 和 $$X=1,Y=0$$，于是 $$P(Z=1)=p_0q_1+p_1q_0$$。类似地，要求 $$P(Z=r)$$，就把那些满足 $$i+j=r$$的$$p_iq_j$$ 相加起来即可，例如 $$P(Z=4)=p_0q_4+p_1q_3+p_2q_2+p_3q_1+p_4q_0$$。而根据 $$X$$ 和 $$Y$$ 的取值范围，我们知道 $$Z$$ 的可能取值有 $$0,1,2,\ldots,n+m$$，不妨假设 $$Z$$ 取这些值的概率分别为 $$r_0,r_1,\ldots,r_{n+m}$$，于是有

$$\displaystyle r_k=\sum_{i+j=k}p_iq_j,\ k=0,1,2,\ldots,n+m$$

这就是离散情形下的卷积公式，它实际上就是对两个向量 $$p=(p_0,p_1,\ldots,p_n)',q=(q_0,q_1,\ldots,q_m)'$$ 进行运算，来得到第三个向量 $$r=(r_0,r_1,\ldots,r_{n+m})'$$。

好了，那卷积有什么用呢？在概率和统计中，它最大的用处自然就是求独立随机变量和的分布，但实际上它还有许多有趣的应用。来看下面这个问题：

假设有两个多项式，$$P(x)=p_nx^n+p_{n-1}x^{n-1}+\cdots+p_1x+p_0$$，$$Q(x)=q_mx^m+q_{m-1}x^{m-1}+\cdots+q_1x+q_0$$，现在想要求 $$R(x)=P(x)Q(x)$$ 的表达式中 $$x^k$$ 的系数。你发现了什么？没错，其结果和之前的卷积表达式是完全一样的。这也就是说，已知了两个多项式的系数向量，这两个多项式乘积的系数向量就是它们的卷积。

于是开头提到的帖子中的问题就可以解决了。举个例子来说，我们要求1111的平方，首先可以将1111写为 $$1\times 10^3+1\times 10^2+1\times 10^1+1\times 10^0$$，然后令 $$P(x)=x^3+x^2+x+1$$，则有 $$1111=P(10)$$。接下来，计算 $$R(x)=P(x)P(x)$$ 的系数向量，也就是对 $$(1, 1, 1, 1)'$$ 自身进行卷积，得到的结果是 $$(1,2,3,4,3,2,1)'$$，即 $$R(x)=x^6+2x^5+3x^4+4x^3+3x^2+2x+1$$，于是我们可以很自豪地说，$$1111^2=R(10)=10^6+2\times 10^5+\cdots+2\times 10+1$$，那么1111的平方自然就等于多项式的系数向量组成的数字1234321了。

可是不要高兴得太早，万一出现 $$5\times 10^3+16\times 10^2+11\times 10+1$$ 这种情况怎么办？总不能说是516111吧？也不用急，我们可以从个位数起，依次将数码向高位进位：如果该位的数字小于10，那么就保留这个数，转向更高一位；如果大于10，就将它除以10的余数保留，除以10的商加到更高一位。在这个例子中，个位数等于1，保留；十位上的数除以10余1，商1加到百位；百位17除以10余7，商1加到千位；千位6，保留。因此结果最后就是6711。

在R中，求卷积的函数是`convolve()`，如果要求两个向量`pv`和`qv`的卷积，用法就是`convolve(pv, rev(qv), type = "open")`。注意函数中的第二个向量一定要反向一下，而且`type`参数必须指定为`open`。帖子中的问题，程序代码如下：

{% highlight r %}
square = function(n)
{
    if(n == 1) return(1);
    p = rep(1, n);
    v = convolve(p, rev(p), type = "open");
    v = as.integer(v + 0.5); # 将double转为integer的常见做法
    for(i in length(v):2)
    {
        v[i - 1] = v[i - 1] + v[i] %/% 10;
        v[i] = v[i] %% 10;
    }
    return(v);
}
square(10);
{% endhighlight %}
    