---
title: Opencv Python 熊猫人头像生成
date: 2016-03-09 16:48:49
tags: 
    - Python
    - Opencv
---



# 1. 介绍
之前看到有人发了一个Matlab程序，可以根据照片上的人脸抠出相应的眼睛鼻子嘴巴，然后放到熊猫人上。生成头像。
熊猫人原型如下：
![熊猫人](http://7xrh75.com1.z0.glb.clouddn.com/python_base.jpg)
写出来的程序放在[Github](https://github.com/LichAmnesia/Pandamen-Generator)了。
稍微说下程序流程。
# 2. opencv的人脸识别
首先使用opencv的Haar特征分类器。人脸的Haar特征分类器就是一个XML文件，该文件中会描述人脸的Haar特征值。当然Haar特征的用途可不止可以用来描述人脸这一种，用来描述眼睛，嘴唇或是其它物体也是可以的。
这个文件在opencv的安装目录的/data/haarcascades文件夹下面，进行人脸识别或者是脸部其他部位的识别的时候需要引用这个目录下的相应文件。
主要运行这个CvHaarClassifierCascade可以抠出人脸，把人脸的图像存下来进行下一步操作。
# 3. 根据人脸抠出五官
这个熊猫人只需要眼睛，鼻子和嘴巴就可以了。比较好的是opencv已经有一套可以识别五官的分类器了。直接使用就可以了。但是识别率不高。把仅有人脸的图片作为原始图像可以识别出眼睛，鼻子来。然后根据位置把其他的不想关的位置的像素直接设置为255。
不过这个分类器效果比人脸的差太多了。要自己先做一次把明显不是的去掉。后面可能还得实现个其他的分类器。

# 4. 中值滤波和二值化
已经只有眼睛鼻子嘴巴的图像经过一次中值滤波滤掉一些杂质。然后使用二值化，把图像变成二值图像放到熊猫人上。
记得要调用resize变化图像的大小，不然会很奇怪。

# 5. 最终结果
![熊猫人](http://7xrh75.com1.z0.glb.clouddn.com/python_merge_output_meizi_0.jpg)