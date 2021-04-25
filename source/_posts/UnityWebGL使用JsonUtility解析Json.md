---
uuid: 88bae899-1603-5a9d-cadf-df395f9f7793
title: UnityWebGL使用JsonUtility解析Json
tags: Unity Tips
---
# UnityWebGL使用JsonUtility解析Json
### 编辑器：Unity 2019.3.0f3 (64-bit) 
### 由于UnityWebGL 发布后引用的.DLL 会出错 所以 使用LitJson 在打包后运行会出错。然后听说 Newtonsoft.json 可以在2019.3.0 版本发布的WebGL版本正常运行，以前也没用过看了之后还是用unity 自带的Json 去解析数据。有兴趣的可以去看看。
---
#### 这里用Unity接收和风天气的天气API接口返回的Json数据来进行示范，简单的记录一下。
**首先看一下返回的Json数据：**
![](1.jpg)
#### 我用了PHP去请求接口。C#具体的方法和风天气官网都有实例代码。
#### 首先要针对Json数据创建相应的类，直接上代码：
```csharp
    public class WeatherInfo
    {
        public List<Weather> HeWeather6;
    }

    [System.Serializable]
    public class Weather
    {
        public basic basic;
        public update update;
        public now now;
        public string status;
    }

    [System.Serializable]
    public class update
    {
        public string loc;//当前国家时间
        public string utc;//世界时间
    }

    [System.Serializable]
    public class basic //基本信息
    {
        public string cid; //城市cid
        public string location; //本地区域
        public string parent_city; //当前所属城市
        public string admin_area;// 当前省份
        public string cnty; //国家
        public string lat;// 纬度
        public string lon;//经度
        public string tz;//时区
    }

    [System.Serializable]
    public class now
    {
        public string cloud;//云量
        public string cond_code;//天气代号
        public string cond_txt;//天气文字
        public string fl;//体感温度
        public string hum;//相对湿度
        public string pcpn;//降水量
        public string pres;//大气压强
        public string tmp;//温度
        public string vis;//能见度
        public string wind_deg;//风的强度
        public string wind_dir;//风向
        public string wind_sc;//风力
        public string wind_spd; //风速
    }
```

#### 这里类的命名都要跟返回的数据名称相同， 最重要的一点就是 一定要将类序列化。
##### 这里用WeatherInfo 对网络请求之后返回值进行解析

```csharp
cityInfo = JsonUtility.FromJson<WeatherInfo>(re.downloadHandler.text);
```
##### 然后遍历获取想要的数据：
```csharp
 foreach (var item in cityInfo.HeWeather6)
 {
    Debug.Log(item.now.cond_txt);
 }
```


