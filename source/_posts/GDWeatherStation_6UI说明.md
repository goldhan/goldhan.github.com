---
title: GDWeatherStation_6 UI说明
date: 2018-11-05 15:30:00
tags: 
    - ESP8266 
    - 12864
    - Arduino
    - Weather
    - UI
    - Sketch
cover: /img/GDWeatherStation/UI_0.png
---

# GDWeatherStation_6 UI说明

> 关于设计方面的说明

## UI 展示

![01](/img/GDWeatherStation/UI_1.png)
![02](/img/GDWeatherStation/UI_2.png)
![03](/img/GDWeatherStation/UI_3.png)

具体源文件 [Sketch](https://github.com/goldhan/GDWeatherStation/tree/master/UI_Design)

## 12864 OLED

由于此模块网上有很多成熟的代码，所有选择12864显示模块，只需要显示简单的信息，已经足够。OLED的特性，所以显示效果还不错。

## 设计思路

### 简单，美观

显示模块所提供的可显示的区域其实不多，再加上单片机性能有限，所以尽量简单明了，只需要显示所需要的信息即可，但是本人大学艺术专业，所以还是要求自己在足够简单的同时，尽量美观！所以只运行了简单的圆角框即可，外加一点元素点缀即可。

### 卡片

由于显示的信息一个屏幕肯定不足够，所有设计成上下轮播的卡片展示。已足够显示，网络时间、今日天气、以及明日天气和少许的自定义信息。
