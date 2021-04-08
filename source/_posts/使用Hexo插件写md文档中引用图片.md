---
uuid: 05f7c69c-c22d-a14d-3273-465eafd154ec
title: Hexo
tags: Hexo Plugins
---
## 使用  [hexo-asset-image](https://github.com/xcodebuild/hexo-asset-image) 插件在基于Hexo框架编译md文档中添加图片

### 安装
```
npm install hexo-asset-image --save
```

### 文件结构：
md文件同级目录下（sourece/_posts）创建同md文件名称的图片文件夹

```
blogs
├── apppicker.jpg
├── logo.jpg
└── rules.jpg
blogs.md
```
在文档中图片地址为图片名称加后缀无需添加文件夹路径。

```
![](logo.jpg)
```

### 配置：

确保 _config.yml 中 ```post_asset_folder: true```


### 问题：

正确配置之后文档中配置的图片无法正常显示,通过查看未加载图片连接发现 图片地址改变。

**域名是xxx.io的情况下，图片路径会从原本/xxx.jpg变成 /.io/xxx.jpg**

### 解决：
通过 npm 安装的包出现 以上情况，因为插件已经修复但npm包并未更新。通过配置插件中的 **index.js**可以解决以上问题。

将 **hexo-asset-image/index.js** 文件中 24 行 修改为```var endPos = link.length-1;```即可。
```
hexo-asset-image/index.js

Line 24 in 3c114cf

 var endPos = link.length-1; 
```