---
layout:     post
title:      关于recall 和precision
# subtitle:   
date:       2017-11-6
author:     yihao
header-img: img/2017-11-6-header.png
catalog: 	 true
category: private 
tags:
    - Machine Learning 
---

#### 关于recall 和 precision
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>


$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
+ C：一个很大item的集合。
+ π：集合中相关的item的集合（π<< 1）。
+ t：算法所识别出的item的集合。
+ h(t)：t中确实相关的item的集合，通常这部分称作命中（相反的是丢失）\
+ 假设 $\omega$是集合$C$中随机去取出的一个元素

$$ y=1$$ if $$\omega$$ is relevant
$y^{''}=1$if $\omega$ is detected by the algorithm
$y=0$otherwise
$y^{''}=0$otherwise
* $Recall = \frac{h(t)}{\pi} \qquad Recall = Pr(y^{''}=1|y=1)$
* $Precision = \frac{h(t)}t\qquad Precision = Pr(y=1|y^{''}=1)$
* $Precision = \frac{Pr(y^{''}=1|y=1)\cdot Pr(y=1)}{Pr(y^{''}=1)}=\frac{Recall\cdot\pi}{t}$
* **Average Precision** $\frac{define}{}\frac{1}{1-0}\int_0^1p(r)dr = \int_0^1p(r)dr$
<img src = 'https://i.imgur.com/2gVFJzE.png'>
可以使用下图这个结果来理解一下AP 然后对于不用的样本都会有一个ap
<img src = 'https://i.imgur.com/uqbTuUq.png'>

