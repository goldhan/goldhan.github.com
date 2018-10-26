---
title: GDWeatherStation_2.前期准备
date: 2018-10-25 13:31:14
tags: 
    - ESP8266 
    - 12864
    - Arduino
    - Weather
---

# ESP8266 OLED WeatherStationServer

## 硬件准备

- ESP8266 模块
    > 注意 ESP8266 模块有差别，但是基本都是一样的，需要注意引脚定义
- 12864 OLED 模块 i2c接口
    > 当然也可以使用SPI接口，只是需要更改 Arduino程序代码即可
- 连接线若干
- __可选__ usb 下载器
    > 有些 ESP8266 没有自带 usb下载功能，需要自己买个usb下载器，进行程序烧录

## 环境准备

- Arduino IDE
    > 百度下，有下载
- usb下载器驱动
    > 根据自己型号去驱动，多数店家会有提供，百度也能找到
- Python3 环境

## 所需要的第三发库

### Arduino IDE 需要的库

> 具体怎么去安装库，请自行百度，关键字：Arduino 添加库，__Arduino 添加ESP8266支持__

``` C
#include <NTPClient.h>
#include <ArduinoJson.h>
#include <ESP8266WiFi.h>
#include <ESP8266HTTPClient.h>
#include <U8g2lib.h>
#include <WiFiUdp.h>
```

### Python

无