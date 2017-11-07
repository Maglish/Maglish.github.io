---
layout:     post
title:      Deep Forest : Towrads an Alternative to Deep Neural Networks
# subtitle:   
date:       2017-11-7
author:     yihao
header-img: img/2017-11-6-header.png
catalog: 	 true
tags:
    - Machine Learning 
    - Ensemble Learning
    - Deep Learning
---

<div align=left> 

# deep forest : Towrads an alternative to Deep Neural Networks


## 什么是深度学习

周老师开篇利用SIAM News2017的一篇文章中的一句话来解释什么是深度学习
<div align = left><img src = "https://i.imgur.com/VVuvlwG.png" > </div>

> 深度学习是一类使用神经网络的机器学习方法

## 为什么要深？

<div align = left><img src = "https://i.imgur.com/rUOYAbg.png"/> </div> 

+ 在传统机器学习中，通过提升模型的复杂度来提高模型的学习能力，但是也存在问题就是更复杂的模型就意味着更容易过拟合。
+ **深度神网络通过使用更加复杂的结构和提高网络深度来增加模型复杂度**来提高模型的学习能力
+ 网络的宽度增加只是增加了基函数的个数但是深度的增加增加了其在泛函空间的表达能力
    > Adding layers is more effective than adding units : Increasing not only the number of units with activation functions, but also the embedding depths of the functions
+ 增加模型复杂度会带来两个crucial 的问题：
    - 首先就是过拟合
    - 其次是模型过于复杂就难以使用传统的BP算法来使模型收敛到稳定的状态
+ 解决上面问题的方法是：
    + big data （使用大数据减少过拟合风险）
    + facilities (GPU,TPU)
    + training Tricks

## DNN的本质？

<div align=left><img src = "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicngWVXDibJJfDawAIYX22TSpPC37mMAfyw8QYMS6RuCVLGMxZVyVWKkww/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1"></div>

+ 传统的Representation learning 是通过认为设计特征达到分类学习的目的
+ 深度学习的重点在于让网络进行Representation learning从而实现了一种特征空间的映射关系

    **因此深度学习在某些特定任务上可以取得显著的效果，这些领域的共同点是数据的原始空间与最终用于分类或其他任务的数据空间之间具有较大的距离**

    **为什么不能宽度网络！？**
    <div align= left><img src = "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicnUYBGEK6ZHhpDS0EJwK4ypl6sRxcyxcmqu5BKh4nQGDP00FtmyHibuFQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1"></div>
+ 实际上，DNN的深度结构就是一层层的堆叠设计，其实不断的**逐层抽象、逐层加工和特征转换**的过程


# 决策树与boosting


+ 深度网络的结果可重复性差，并且trciks依赖大量的training经验
+ 决策树与boosting同样具有和DNN一样的结构特性但是却没有DNN那样强大的建模能力，其复杂度不够并且不能很好的跨空间学习
<div align = left><img src= "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicnvlZbOFBw5EyEHfqAJ6icgRQmJF2icJR4uMXvyBibLgRv4EyVL0gdnI2iaw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1"></div>


# gcForest
## multi-Grained Cascade Forest
**Cascade forest + Multi-Grained**
<div align=left>
<img src="https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicnZaj5KuNIwGe8zrtOKh1gF1h6dibVFp6djw0I0dO57MklVSibjrwMu00Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1">
</div>

使用级联结构让gcforest做表征学习能和深度神经网络媲美同时参数更少并且可以**根据数据量自适应模型复杂度**

+ 集成学习
    集成学习是数据比赛大杀器！！！使用多个学习器来集成最终结果的方法可以显著提高学习效果。
    下面是历年KDDCup的比赛结果
    <div align=left>
    <img src= "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicnJickibQiaDD29CFOeqqoCicZVJZM9mrHUWYgEbJTyU2SsTj78uOxFvDweg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1">
    </div>
</div>

+ 为了保证集成结果，模型个体的差异性就显得非常关键，个体学习期的精度越高，差异性越大则集成效果就越好。
    <div align=left >
    <img src = "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicnxnSUtSb3sicv7o0HkyIVib1d4gcYaOcNoEBcrKaJLxXicng5S68Usyozw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1">
    <div align=left>
    但是关于ambiguty的定义是一个比较抽象的概念，学习器之间的差异性就难以判断，因此在学习的过程中加入一些随机扰动成为了增加学习器之间差异性的核心思想,下图给出了一些常用的方法
    <div align=left>
    <img src = "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicncv0m4YhYXabpHTgjSfsGoATkImVsrDn260AQuS3mXib8sQmLq3cVzaw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1">
    </div>
    </div>
    </div>

## Cascade Forest
深度学习中的表征学习主要依赖于对原始特征的组曾处理，受此启发，gcForest 采用级联结构，如下图所示
<div align=left >
<img src = "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicnIE7ibwW3IC7RM3Wp1K3TTR8ZRkREkblQDwsswnRhSiaAZfSZVx67MyhQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1">
</div>
从图中可以看出concatenate多个Random Forest的方式就是一种ensemble learning的学习方法（diversity）

## Multi-Grained 
Multi-Grained 其实就是使用一个sliding window在原始数据上做扫描的过程，滑动窗口实际上是引入了严重的分类噪声来增加分类器的差异性,使用sliding window的缺点就是原始数据维度过高时候就会导致最后的concatenate feature的维度太高所以该方面的future是使用hash或者其他更加高效的采样方法
<div align=left>
<img src = "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicnCCshDIPCgNcGibR5CY0n8ItDiacd8Qicibs0DJ5n2xUOrTW67SP41NHDSA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1">
</div>
下图是gcForest的Framework
<div align=left>
<img src = "https://mmbiz.qpic.cn/mmbiz_png/AefvpgiaIPw2pXianibVD94ibeOvQWZYkHicne667qOtwQW5H4173EhbEhqgVrUSEhecX0UqxshoeqZBgKz2FRveQtg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1">
</div>


