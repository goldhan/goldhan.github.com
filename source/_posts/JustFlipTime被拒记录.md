---
title: JustFlipTime被拒记录
date: 2019-06-22 19:20:00
tags:
  - iOS
  - APP
cover: /img/JustFlipTime/JustFlipTime_stop.png
---

# JustFlipTime 被拒记录

> 上架 APP Store 被拒

![01](/img/JustFlipTime/JustFlipTime_stop.png)

## 原因

```OC
Guideline 2.3.7 - Performance - Accurate Metadata

Your app name or subtitle to be displayed on the App Store includes keywords or descriptors, which are not appropriate for use in these metadata items.

Specifically, the following words in your app name or subtitle are considered keywords or descriptors:

- フリップ、時計、シンプル、最も美しい、フリップ、古い機器
- Flip, clock, simple, old Phone
- Flip,时钟,简约,最美,翻页,旧设备

Next Steps

To resolve this issue, please revise your app name or subtitle to remove any keywords and descriptors from all localizations of your app. Keywords can be entered in the Keywords field in App Store Connect to be used as search terms for your app.

Before submitting your app to the App Store, ensure there are no unnecessary phrases, words, or descriptions in the app's name, description, icons, preview, or other metadata fields. As a best practice, your app's metadata should communicate the app's value in as few words as possible.

Resources

For information on how to revise your app name, please review Renaming a Project or App.

For information on changing the app name and other metadata in App Store Connect, please review the View and edit app information page.

For resources on selecting a memorable and unique app name and subtitle, you may want to review the App Store Product Page information available on the Apple Developer website.

Guideline 2.5.10 - Performance - Software Requirements


We noticed that your app or its screenshots include test advertisements. Apps or metadata items that include features that are for test or demonstration purposes are not appropriate for the App Store.

Next Steps

To resolve this issue, please revise your app to complete, remove, or fully configure any partially implemented features. Please ensure your screenshots do not include any images of demo, test, or other incomplete content.

Guideline 3.2.2 - Business - Other Business Model Issues - Unacceptable


Your app displays or promotes third-party apps, which is not appropriate for the App Store.

Next Steps

To resolve this issue, please remove the feature from your app.

Please see attached screenshots for details.
```

## 总结下

1. 在宣传关键字上使用了和 APP 本身名字相关，这个在于 APPLE 看来是不合理的

> 于是我把对应的 Flip 关键字删除掉

2. 在内购的截图上，有出现 Test 关键字，APPLE 认为，在截图上出现测试等相关的关键字是不合理的

> 于是重新截图并上传

3. APP 内部出现类似其他 APP Store 的界面，其实是我嵌入的第三方广告，APP WALL，当时在嵌入时，我还特地的去其官网看，有没有什么注意事项，结果什么也没说，于是觉得嵌入应该没问题，结果还是被拒，之前就知道，iOS 应用内部不能实现类似 APP Store 的功能。本以为 SDK 提供商没说，还以为放宽了呢。

> 代码屏蔽对应的模块，重新打包上传，注意打包时的版本号

## 最后

希望我的经历给予大家再次注意~~~
