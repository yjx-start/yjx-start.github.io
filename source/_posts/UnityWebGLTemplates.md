---
uuid: d73dc796-2d4d-6224-d17c-0516d935b956
title: Unity自定义WebGLTemplates 
tags: Unity Tips
---
# Unity自定义WebGLTemplates
### Untiy 打包WebGL 版本时会有个模板选择 可能绝大多数的项目都需要对原模板进行修改
### 以下说一下如何添加一个自定义的 WebGL Template 
---
#### 首先找到unity 自带的模板位置（2019.3.0f3为例）
*2019.3.0f3\Editor\Data\PlaybackEngines\WebGLSupport\BuildTools\WebGLTemplates\Default*
![](1.jpg)
#### 在unityProject/Assets 下创建一个文件夹命名为 “WebGLTemplates” 在文件夹下创建一个文件夹命名为你想要模板的名字我这里用了”DataPresentation” 将自带模板中的文件复制过来。
![](2.jpg)

#### 这样就会在WebGL Template 中多出一个模板，这里我对缩略图进行了修改所以看起来不同，图片”thumbnail” 对应的是缩略图  其他的图片，在文件中一一对应都是可以更改的 
![](3.jpg)

#### 这样我们就可以对模板进行自己的布置修改。


