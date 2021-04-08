---
uuid: ca7f0092-49f6-0f78-b48d-badbaf7a963e
title: EPPlus插件
tags: Unity Plugins
---
# EPPlus的写入Excel功能简单运用和Build运行错误的解决方法
### EPPlus 是使用Open Office XML格式（xlsx）读写Excel 2007 / 2010文件的.net开发库。
### 官网文档：https://github.com/JanKallman/EPPlus
### EPPlus.dll下载地址：https://pan.baidu.com/s/13Pn3zSLDL-kgVgUnn4ZUPA
### 本案例使用unity版本：unity2018.3.2f1
### 编程工具：VS2017
---
##### 插件导入Plugins文件夹中
![](导入.png)
##### 在脚本中引用
``` C#
using OfficeOpenXml;
using System.IO;
```
![引用](引用.png)
##### 创建及写入EXCEL的方法
![方法](方法.png)
此方法在需要是位置调用即可 方法中 
**outPutDir**是生成文件的路径可以根据需求改变（本例中在D盘根目录创建了名为FileName的xlsx文件）。
**hitinfo** 变量是 Text 便于查看状态

![](导出.png)
![](效果.png)
**本例并未对Excel表格进行更深入的设置，如有需要可自行百度。**

## Build后运行出错
#### 本案例在Unity打包后出现错误：导出的exe可正常打开但是在保存写入的数据时发生错误，以下是项目日志：
![](报错.png)
可以看出是无法找到名为 **437**的编码数据，导致保存文件时发生了错误。2017版本日志说法不同：**ArgumentException: Encoding name 'IBM437' not supported。** 都是**437** 数据的错误。
在网上搜索后发现很多都是这样的情况，以下给出解决以上问题的方法：
**1、打包时  选net2.0 而不是它的子集subset   我再2018下选subset没办法成功打包  会报错**
![](配置.png)
**2、成功打包以后  在调用dll时若报错“Encoding name 'IBM437' not supported”  从Unity安装路径下找到Unity\Editor\Data\Mono\lib\mono\unity这个文件夹中  找到所有的I18N.dll   大概五六个吧    全部复制到项目的Assets文件夹里   复制完毕后 再重新打包**
![](文件1.png)
![](文件2.png)
**以上两部操作后 Unity导出的EXE运行后也可以进行保存实现预想功能。**
### Ps:解决方法仅供参考。