---
uuid: d5d6336b-3e48-6003-f901-d7f2b5d649c5
title: UntiyWebGL发布上传服务器
tags: Unity Tips
---
# UntiyWebGL发布出来文件上传到服务器出问题
### <font color="#dd0000">SyntaxError: expected expression, got "<"</font><br /> 
#### 编辑器：Unity 2019.3.0f3 (64-bit) 
#### 服务器：Windows Server 2012 R2
---
#### 原因是服务器IIS配置问题 ；
**IIS 文件配置无法识别.unitywebgl 文件所以导致无法运行程序。**
#### 解决方法：
**服务器界面 win+R**
![](1.jpg)
**右键空白 添加MIME类型**
![](2.jpg)
![](3.jpg)
#### 设置之后再次访问 程序就会正常运行。


