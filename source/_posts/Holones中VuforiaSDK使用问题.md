---
uuid: e45c4b87-39ba-dd9f-78f6-f626f08bacee
title: Untiy&Holones&VuforiaSDK出现的问题(持续更新)
tags: FAQ
---
# Unity开发Holones2中使用Vuforia识别遇到的问题与解决方法

## 出现问题
#### 一：[使用VuforiaImageTarget识别之后，随着移动识别出现物体也会跟着移动拉近走远。](#一)
#### 二：[在使用Hololens官方程序 Microsoft Hololens 进行直播画面查看或Hololens自带录屏后开启带有Vuforia识别的程序，会导致直播或录屏停止中断。](#二)

## 对应解决方案
#### 一：
   - 在Vuforia官网上传图片填写尺寸时，尽量测量准确实际应用的图片大小。尺寸越接近移动时，识别出现物体位置越稳定。
#### 二：
   - Vuforia在启动后获取摄像头画面时会与已存在的直播录屏冲突，将直播录屏强制关闭。所以需要在程序启动Vuforia后启动同屏或录屏就可以同时使用。
