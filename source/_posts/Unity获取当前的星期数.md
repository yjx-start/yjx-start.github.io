---
uuid: afc426a1-d4ee-fdfd-1efd-3bcf1d5c2787
title: Unity获取当前中文星期数
tags: Unity Tips
---
## Unity获取当前中文星期数
**Untiy 在程序中使用 ```DateTime.Now.DayOfWeek ```可以获取到当前的星期数。**

**如果要想去对应成中文星期数显示可以用以下方法：**

```csharp
string[]  weekdays = new string[] { "星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"};

string  week = weekdays[Convert.ToUInt32(DateTime.Now.DayOfWeek)];
```

**这样输出的week 就会对应的显示中文的星期数**



