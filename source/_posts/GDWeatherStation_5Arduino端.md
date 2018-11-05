---
title: GDWeatherStation_5 Arduino端
date: 2018-10-25 13:31:14
tags: 
    - ESP8266 
    - 12864
    - Arduino
    - Weather
---

# GDWeatherStation_5 Arduino端

> __ESP8266__ 源码，使用 Arduino 烧录到 ESP8266

## Arduino IDE 需要的库

> 具体怎么去安装库，请自行百度，关键字：Arduino 添加库，Arduino 添加ESP8266支持

``` C
#include <NTPClient.h>
#include <ArduinoJson.h>
#include <ESP8266WiFi.h>
#include <ESP8266HTTPClient.h>
#include <U8g2lib.h>
#include <WiFiUdp.h>
```

## Arduino 使用说明

### GDWeatherStation.ino

``` c
#include "GDDraw.h"

void setup()
{
    char ssid[] = "xxxxxx"; // wifi ssid
    char password[] = "xxxxxxxx"; // wifi password
    char apiKey[] = "c85bd9d844646649b69a6476d53cae6f"; // yeelink apiKey
    char url[] = "http://api.yeelink.net/v1.0/device/355774/sensor/402747/datapoints"; // yeelink url
    Serial.begin(115200);
    u8g2Begin();
    GDWifiBegin(ssid, password, apiKey, url);

    // theFirst();
}
void loop()
{
    char apiKey[] = "c85bd9d844646649b69a6476d53cae6f"; // yeelink apiKey 和上边值相同
    char url[] = "http://api.yeelink.net/v1.0/device/355774/sensor/402747/datapoints"; // yeelink url 和上边值相同
    GDStart(apiKey, url);
}
```

> __请按照注释去填写对应的值__
