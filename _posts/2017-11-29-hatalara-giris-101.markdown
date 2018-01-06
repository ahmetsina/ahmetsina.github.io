---
title: Hatalara Giriş 101
layout: post
date: 2017-11-29 13:07

tag:
- Android
- iOS
- Notification
blog: true
author: ahmetsina
description: Android ve OneSignal ile ilgili bir hatanın çözümü
---

## OneSignal Hatası
Şu anda İnegöl ilçesinde yer alan internet haberciliği yapan [InegolOnline](http://inegolonline.com) için Android uygulaması geliştiriyorum. Uygulama geliştirmenin son safhalarına doğru bildirim özelliğini de eklemek için [OneSignal SDK](https://documentation.onesignal.com/docs/mobile-sdk-setup)'ini kullanacaktım. `build.gradle`  dosyasında gerekli bağımlılıkları ekledim. OneSignal dökümantasyonundaki her şeyi doğru yaptığımı sanıyordum. Bildirim gönderdiğimde ise hata alıyordum. Hata ile 3-4 saat uğraştıktan sonra anladım. Hata şöyle başlıyordu.
```
Field 'android.support.v4.app.NotificationCompat$Builder.mNotification'
```

Aynı zamanda diğer librarylerde de version çakışması hatası veriyordu şunun gibi :

```
All com.android.support libraries must use the exact same version specification (mixing versions can lead to runtime crashes). Found versions 25.1.1, 24.0.0. Examples include com.android.support:animated-vector-drawable:25.1.1 and com.android.support:mediarouter-v7:24.0.0
```

Stackoverflow'un dibini gördüm fakat yine de cevabını bulamadım. Çıkmazdan çıkmanın yolu geri adım atmaktır. Bunu bilerek attığım adımları tekrardan gözden geçirdim ve build.gradle dosyasına eklemediğim önemli bir bölümü ekledim. O da şu bölümdü:
```
plugins {
    id 'com.onesignal.androidsdk.onesignal-gradle-plugin' version '0.7.0'
}
apply plugin: 'com.onesignal.androidsdk.onesignal-gradle-plugin'
```

## Kanna Hatası

Hali hazırda Swift 3 ile yazılmış uygulamaları Swift 4'e taşırken aldığım hatalardan biri Kanna ile ilgiydi.

```
Let 'kDefaultXmlParseOption' is private and cannot be referenced from a default argument value
```
Bu hatayı da asıl araştırmam gereken konuyu yani kütüphaneleri de Swift 4'e taşımayı unuttuğumdan bayağı bir bocaladım. Benim gibi sorunlarla karşılaşmak istemiyorsanız herhangi bir taşınmada o taşınmaya bağlı şeylerin yani kütüphanelerin de değişime uğrayacağını unutmayın.

 
