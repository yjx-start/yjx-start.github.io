---
uuid: cf60c75b-d801-5bcf-8852-5d2dd474f3d3
title: Hololens2模型皮肤权重异常问题
tags: Hololens
---
# Hololens2模型皮肤权重异常问题
## 问题描述：
   - **引擎版本**：Untiy **2019.4.3** 版本
   - **程序环境**：
      - 使用 MRTK.2.5.3.unitypackage
      - 场景添加了**MixedRealityToolkit**并将Asset设置为 **DefaultHololens2ConfigurationProfile**
   - **出现问题**
      - 问题一：fbx模型导入后在fbx源文件文件下没有找到模型的Avatar文件。
      - 问题二：解决问题一之后运行模型动画，出现模型皮肤权重异常问题。（模型动画使模型变形）
## 问题原因：
   - **问题一成因**
      - Unity在2019.4版本中不会自动生成Avatar文件。
   - **问题二成因**
      - 程序的 Skin Weights（设置可以影响单个顶点的最大骨骼数量）选项设置数值过低。其数值改变在**MixedRealityToolkit**Asset设置为Hololens时被MRTK改变，用于优化性能。

## 解决方法：
   - **问题一**
      - 导入fbx模型后在模型**Rig**选项中**Avatar Definition**选择需要的选项来生成或引用Avatar。
   - **问题二**
      - 打开Unity**Project Settings**选择**Quality**选项，在Quality中的**Other**一栏中，找到**Skin Weights**选项，如果是模型通过MRTK中切换Hololens2配置的此选项值应该为**1 Bones**，这就是模型皮肤权重出现问题的关键，将此项值设置为更高的选项即可解决。
   - **Skin Weights选项是在2019.1中开始加入模型设置中的**

## [Model Import Settings window 官方文档](https://docs.unity3d.com/Manual/class-FBXImporter.html)

