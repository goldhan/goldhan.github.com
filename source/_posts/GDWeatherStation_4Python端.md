---
title: GDWeatherStation_4 Python端
date: 2018-11-05 16:45:00
tags: 
    - ESP8266 
    - 12864
    - Arduino
    - Weather
---

# GDWeatherStation_4 Python端

## 服务器端——Python实现

### 为啥要写个这样的程序

- 首先单片机性能有限，并且来来回回烧录程序比较麻烦，目前网上的接口对于单片机来讲数据量还是比较大的，解析会耗费很大的硬件资源，且接口不稳定。所以想自己组装一个自己能够把控的接口。
- 自己组装接口可以只要自己想要的信息，使数据量变的小巧，适合单片机的解析，并且可以保证接口的稳定

### 目前已经实现的功能

- 定时从网上的接口获取数据，解析成自己组装的接口并且上传到指定的git仓库上
- 定时上传和天气数据
- ~~定时上传糗事百科段子~~ （已删除此功能）
- 定时push自己的自定义信息

### 使用

- 程序有一个json文件，当第一次使用时需要配置自己的申请的一些接口，和key
- userData.json 文件存放着所用的接口及key

``` json
{
  "city": "shenzhen",  // 城市拼音
  "heWeatherKey": "xxxxxx", // 和风天气Key
  "qiuShiAPI": "http://m2.qiushibaike.com/article/list/text?count=5&page=1",
  "gitUrl": "https://xxxxxxx.git", // 所申请的 Git 仓库地址
  "title": "about me", // 推送标题
  "detail": "qq:xxxxxx    have a good Day! This is my first push!" // 推送内容
}
```

1. `git clone https://github.com/goldhan/GDWeatherStation.git`
2. 修改 service 目录下的 userData.json 文件
3. 终端 cd 到 Service 目录下
4. `python3 Main.py` 即可

### 问题

> 已经删除关于糗事百科的功能，所以没有了中文的烦恼，不过自定义的推送内容依然不支持中文

- ~~目前糗事百科接口都是中文，但是ESP8266 上的程序不支持中文（不知道有没有英语版的类似糗事百科的接口~~
- ~~还是中文中文中文！~~

### 注意

- 当请求有问题时程序会停止，请注意。
- 请严格的按照json文件里的格式进行填写，不要乱加多余的空格或者其他不必要的字符。
- 注意定义推送消息不要多，因为屏幕显示区域有限
- 因为对应的ESP8266 端的程序不支持中文，所以请用英语写推送消息。
