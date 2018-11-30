---
title: GDWeatherStation_5 Arduino端
date: 2018-11-06 13:31:14
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

> __在修改编辑中......__

### GDWeatherStation.ino

``` c
#include "GDDraw.h"

void setup()
{
    char ssid[] = "xxx"; // wifi ssid
    char password[] = "xxx"; // wifi password
    char url[] = "https://raw.githubusercontent.com/goldhan/MockJSON/master/GDWeather.json"; // git url
    // SHA1 fingerprint of the certificate  
    //把你需要调用的请求地址用浏览器访问，然后打开调试工具选择“安全”即可看到对应请求的fingerprint，复制到这个地方即可
    char fingerprint[] = "CC AA 48 48 66 46 0E 91 53 2C 9C 7C 23 2A B1 74 4D 29 9D 33"; 
    Serial.begin(115200);
    u8g2Begin();
    GDWifiBegin(ssid, password, fingerprint, url);

    // theFirst();
}
void loop()
{
    // SHA1 fingerprint of the certificate  
    //把你需要调用的请求地址用浏览器访问，然后打开调试工具选择“安全”即可看到对应请求的fingerprint，复制到这个地方即可
    char fingerprint[] = "CC AA 48 48 66 46 0E 91 53 2C 9C 7C 23 2A B1 74 4D 29 9D 33";
    char url[] = "https://raw.githubusercontent.com/goldhan/MockJSON/master/GDWeather.json"; // git url
    GDStart(fingerprint, url);
}

```

> __请按照注释去填写对应的值__

### 注意

- 接线

`U8G2_SSD1306_128X64_NONAME_F_SW_I2C u8g2(U8G2_R0, /* clock=*/D6, /* data=*/D5, /* reset=*/U8X8_PIN_NONE);`
代码已经很明确了，请对应接线即可，也可以按照自己的喜好去换引脚端口，OLED屏幕支持 i2c, SPI,本代码用的是 i2c协议，可以按照自己的需求去更改下代码即可，具体不懂可以百度，关键字：U8G2 spi，
类似：`U8G2_SSD1306_128X64_NONAME_1_4W_SW_SPI u8g2(U8G2_R0,/* clock=*/4, /* data=*/ 5, /* cs=*/ 3, /* dc=*/ 6, /* reset=*/ 7); `

- url 地址

url 地址是git里面可以直接访问json的地址，一般都是以 `https://raw` 为开头的地址

- fingerprint

由于是https请求，所以请用浏览器访问上边的地址，打开调试工具选择“安全”即可看到对应请求的fingerprint，__SHA1__
