---
layout:     post
title:      caffe的matlab接口编译错误
# subtitle:   
date:       2017-11-6
author:     yihao
header-img: img/2017-11-6-header.jpg
catalog: 	 true
tags:
    - caffe
---

修改makefile里面的CXXFLAGS，添加CXXFLAGS += -std=c++11.然后重新编译就可以了。 
即：在那一句话下面添加，如下这样 
CXXFLAGS += -MMD -MP 
CXXFLAGS += -std=c++11

+ 遇到这个问题在终端输入：

<img src = "https://i.imgur.com/6Wnsjkf.png">
```
export LD_LIBRARY_PATH=/usr/local/MATLAB/R2013b/sys/os/glnxa64 *这里要替换成系统的matlab路径*  
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libstdc++.so.6 
```
+ 接着遇到这个问题，这时候输入：

<img src = "https://i.imgur.com/fNA3PDb.png">
```
export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/:/usr/local/cuda-8.0/lib64  
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libopencv_highgui.so.2.4:/usr/lib/x86_64-linux-gnu/libopencv_imgproc.so.2.4:/usr/lib/x86_64-linux-gnu/libopencv_core.so.2.4:/usr/lib/x86_64-linux-gnu/libstdc++.so.6:/usr/lib/x86_64-linux-gnu/libfreetype.so.6 
```