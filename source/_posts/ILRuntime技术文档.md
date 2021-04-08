---
uuid: 8f5d9e68-fc60-7778-1022-12b977b44f18
title: ILRuntime
tags: ILRuntime
---
# [ILRuntime](http://ourpalm.github.io/ILRuntime/public/v1/guide/index.html)
### [ILRuntime的实现原理](http://ourpalm.github.io/ILRuntime/public/v1/guide/principle.html)
   - **ILRuntime借助Mono.Cecil库来读取DLL的PE信息，以及当中类型的所有信息，最终得到方法的IL汇编码，然后通过内置的IL解译执行虚拟机来执行DLL中的代码。**

### [ILRuntime的环境搭建](http://ourpalm.github.io/ILRuntime/public/v1/guide/tutorial.html)
   - **Unity版本**：在2018以上版本可直接通过Package Manager安装。

   - **VS版本**：ILRuntime提供了一个支持Visual Studio 2015、Visual Studio 2017和Visual Studio 2019的[调试插件](https://github.com/Ourpalm/ILRuntime/releases)，用来源码级调试你的热更脚本。

   - **Unity环境**：由于ILRuntime使用了unsafe代码来优化执行效率，所以你需要在Unity中开启unsafe模式。(以2019.4.13为例：File=>PlayerSettings=>OtherSettings\Allow'unsafe'Code(勾选))

### [ILRuntimeU3D示例工程]
   - **获取途径**：
      - 通过[GitHubILRuntimeU3D示例工程链接]((https://github.com/Ourpalm/ILRuntimeU3D))下载使用Untiy 打开。
      - 在Unity引擎中 Package Manager 获取ILRuntime在介绍信息中将Demo导入（推荐）
   - **运行示例工程**
       ILRuntimeU3D示例工程中通过读取StreamingAssets文件夹下的**HotFix_Project.dll**、**HotFix_Project.pdb**，两个文件来模拟热更。但示例工程Asset下没有StreamingAssets文件夹以及用到的文件，需要进行以下操作：
       - 在资源管理器中打开ILRuntime中Demo文件夹在文件夹中可以看到  **HotFix_Project~** 文件夹(文件夹为示例工程中dll的VS工程)，运行并生成文件夹中的VS工程解决方案。
       - 刷新ILRuntimeU3D示例工程Asset，会生成StreamingAssets文件夹以及**HotFix_Project.dll**、**HotFix_Project.pdb**文件。
       - 选择示例场景即可正常运行ILRuntimeU3D示例工程。
   - **更改示例工程热更代码**
      - 在**HotFix_Project**VS工程修改完毕想要的逻辑后。生成解决方案即可自行覆盖原dll。

### ILRuntime功能实现 （持续更新）
 - **在官方Demo中各个场景对应的脚本都有详细的注释演示。此部分建议看官方Demo，未在项目中使用，暂时根据官方Demo的方法运行一遍，后期特殊运用持续更新**

   - **ILRuntimeDemo中脚本用法相对详细。**
      - **AppDomain**：AppDomain是ILRuntime的入口
         ```c#
         //AppDomain是ILRuntime的入口，最好是在一个单例类中保存，整个游戏全局就一个
         //首先实例化ILRuntime的AppDomain，AppDomain是一个应用程序域，每个AppDomain都是一个独立的沙盒
         AppDomain appdomain = new ILRuntime.Runtime.Enviorment.AppDomain();
         ```

      - **读取加载dll**：将Dll 与 PDB文件 转换为Byte[] 然后appdomain进行加载读取。
         ```c#
            System.IO.MemoryStream fs;
            System.IO.MemoryStream p;
            byte[] dll;
            byte[] pdb;
            fs = new MemoryStream(dll);
            p = new MemoryStream(pdb);
            appdomain.LoadAssembly(fs, p, new ILRuntime.Mono.Cecil.Pdb.PdbReaderProvider());
         ```
      - **调用dll中方法**：在官方Demo中各个场景对应的脚本都有详细的注释演示。
### 记录疑问解答（持续更新）
   - **官方常见问题解答**
      - [我要怎么才能在Profiler里看见热更内的方法耗时情况呢？](http://ourpalm.github.io/ILRuntime/public/v1/guide/FastQA.html)
      - [运行出现报错ObjectDisposedException: Cannot access a closed Stream](http://ourpalm.github.io/ILRuntime/public/v1/guide/FastQA.html)
      - [用mono打包的时候，ILRuntime相关的功能都正常，改用IL2Cpp之后，注册的所有委托都不执行了？](http://ourpalm.github.io/ILRuntime/public/v1/guide/FastQA.html)
      - [真机上调试或运行时出现随机闪退](http://ourpalm.github.io/ILRuntime/public/v1/guide/FastQA.html)
      - [使用ILRuntime后产生的GC Alloc比用之前大和很多啊，为什么](http://ourpalm.github.io/ILRuntime/public/v1/guide/FastQA.html)
      - [使用ILRunitme后某个方法调用比之前慢了很多啊](http://ourpalm.github.io/ILRuntime/public/v1/guide/FastQA.html)
   - **PDB文件功能**：
      - PDB文件是调试数据库，如需要**在日志中显示报错的行号**，则必须提供PDB文件，不过由于会额外耗用内存，正式发布时请将PDB去掉。
