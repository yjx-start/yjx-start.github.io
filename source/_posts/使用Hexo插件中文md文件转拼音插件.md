---
uuid: e6df99fe-ccdf-f626-dc22-ab42f6cae858
title: Hexo
tags: Hexo Plugins
---
当md文档为中文名称时，网页连接中无法显示。
这时候就可以使用Hexo的插件将中文的md文件名自动转为拼音来显示。

插件来源：https://github.com/viko16/hexo-permalink-pinyin

安装：

```
npm i hexo-permalink-pinyin --save
```
使用：
在 _config.yml 中配置
```
# https://github.com/viko16/hexo-permalink-pinyin
permalink_pinyin:
  enable: true
  separator: '-' # default: '-'

```

