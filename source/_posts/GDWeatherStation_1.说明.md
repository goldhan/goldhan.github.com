---
title: GDWeatherStation_1.说明
date: 2018-10-24 13:15:14
tags: ESP8266,12864,Arduino,Weather
---

# ESP8266 OLED WeatherStationServer

## 目录

- GDWeatherStation_1.说明
    > 简介以及说明

- GDWeatherStation_2.前期准备
    > 你需要准备什么？

- GDWeatherStation_3.接口说明
    > 你需要准备的接口说明，以及申请工作

- GDWeatherStation_4.Python端
    > Python端服务脚本说明

- GDWeatherStation_5.Arduino端
    > Arduino端说明

- GDWeatherStation_6.UI说明
    > 关于UI设计

- GDWeatherStation_7.后续
    > 进一步改进

## 最终效果说明

> 通过ESP8266连接WIFI访问网络获取天气，网络时间，自定义的信息，然后进行显示

## 需要了解的技术栈

- Arduino
- C
- Python

## 流程说明

利用Python获取申请的api返回信息，进行整理，上传到中转的稳定的api接口，Arduino端再访问此中转的api接口，进行数据展示
