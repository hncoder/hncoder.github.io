---
title: iOS之系统篇
date: 2016-10-22
description: 具备对iOS系统较好的全局观，应在三个方面了解清楚，分别是系统历史版本及其主要特征、系统框架以及系统安全。
---

作为一名iOS开发者，我觉得不仅仅只了解开发过程中遇到的某个具体框架，更是要对系统有个较全面的了解。具备对iOS系统较好的全局观，应在三个方面了解清楚，这三个方面分别是系统历史版本及其主要特征、系统框架以及系统安全。  

## 历史版本及其主要特征  
众所周知，iOS是苹果开发的一款运行在移动智能设备上的操作系统。它早在苹果发布iPhone SDK（2008年3月6日发布）之前的1.x版本并没有正式名称，当时，苹果对外宣称iPhone是运行在桌面系统OS X的某个版本上，这也就说明iOS源自OS X。随着版本2.0的发布，苹果才取名为iPhone OS。之后发布的几个版本都叫iPhone OS，直到运行在第一代iPad上的3.2发布才更名为iOS。了解iOS历史版本详情，可以查看以下表格。

|版本号 | 命名 | 发布时间 | 特征|
|----- | ---- | ------ | --- |
|1.0|iPhone Runs OS X|2007年06月|Core UI<br>Multitouch gestures<br>Mobile Safari<br>iPod<br>Visual Voicemail<br>Maps<br>iTunes Sync|
|1.1|iPhone Runs OS X|2007年09月|iTunes Wi-Fi Music Store<br>iPod Touch compatiblity|
|1.1.3|iPhone Runs OS X|2008年01月|Better location<br>Web clips on home screen<br>Re-arrange icons<br>Multitouch keyboard|
|2.0|iPhone OS|2008年07月|Native 3rd-party apps<br>App Store<br>Microsoft Exchange support<br>MobileMe<br>Contact Search|
|2.1|iPhone OS|2008年09月|Battery life and speed fixes<br>iTunes Genius playlists<br>Dropped call fixes|
|2.2|iPhone OS|2008年11月|Google street view<br>Podcast downloads|
|3.0|iPhone OS|2009年06月|Cut, copy, paste<br>Voice Control<br>MMS<br>Spotlight search<br>Push notifications<br>USB & Bluetooth tethering<br>Landscape keyboard<br>Find my iPhone|
|3.1|iPhone OS|2009年09月|Genius features<br>Ringtone downloads<br>Remote lock<br>Voice Control over Bluetooth|
|3.2|iOS|2010年04月|Support for iPad resolution<br>New app views for iPad<br>Location based on Apple data<br>Bluetooth keyboard support<br>iBooks|
|4.1|iOS|2010年09月|Game Center<br>TV rentals<br>iTunes Ping<br>HDR photos|
|4.2.1|iOS|2010年11月|Pad multitasking<br>iPad folders<br>AirPlay<br>AirPrint|
|4.2.5|iOS|2011年02月|Verizon support<br>Personal hotspot (CDMA only)|
|4.3|iOS|2011年03月|Personal Hotspot (GSM)<br>AirPlay for 3rd-party apps<br>iTunes Home Sharing|
|5.0|iOS|2011年10月|Siri<br>Notification Center<br>PC-free<br>iTunes Wi-Fi Sync<br>iMessage<br>iCloud|
|6.0|iOS|2012年09月|Homegrown Maps and turn-by-turn navigation<br>Siri enhancements<br>Facebook integration<br>Passbook<br>iCloud Tabs<br>Mail enhancements<br>FaceTime over cellular
|7.0|iOS|2013年09月|Visual overhaul<br>Control Center<br>AirDrop<br>Refreshed core apps<br>iTunes Radios<br>FaceTime Audio|
|8.0|iOS|2014年09月|Continuity<br>Widgets<br>Extensibility<br>QuickType<br>iCloud Drive<br>HealthKit<br>HomeKit<br>Family Sharing|
|9.0|iOS|2015年09月|3D Touch<br>Back to App<br>Six-Digit Passcode<br>Low Power mode<br>Battery Widget<br>iCloud Drive App<br>Multitasking on iPad: Slide Over,Split View,Picture-in-Picture<br>Impoved Text Selection<br>Select multiple photos<br>Add and Save Attachment in Mail<br>Draw On Image Attachment<br>Transit Directions<br>Nearby<br>Proactive Assistant<br>Quick Reply to Messaging apps<br>Improved Apps:New app,Notes app|
|10.0|iOS|2016年09月|Raise to wake<br>Rich lockscreen notifications<br>Clear all notification button<br>Water detection<br>Lockscreen camera and ‘widgets'<br>Graphical 3D Touch shortcuts<br>Siri for developers<br>Siri-influenced Quicktype keykoard<br>Delete default apps<br>Apps in iMessage<br>Photo memories<br>Better maps<br>A new Apple music|

上述表格中列出的特性是一些关键字，若要了解细节，需要根据关键字再去查阅详细的资料。但是，每个版本更新的功能细节很多，尤其是最近几个版本功能点很多，全部搞清楚没有很大必要，而了解每个版本变化关键特性，在大体上把握系统的演进变化即可。在iOS的版本演进过程中，功能特性从早期的匮乏到如今的相当丰富，提供的体验也变得越来越人性友好化。以下是我梳理的一些系统变化情况：

1. iOS从桌面系统OS X发展而来。
2. 1.x版本没有正式名称，不同市场上其它智能设备，划时代性的支持全屏幕触摸操作，提供更好用的浏览器，这是早期iPhone在市场上众多智能设备中受欢迎的关键。
3. 2.x版本开始取名iPhone OS，发布SDK，开放App Store，可以安装第三方开发应用，开放App Store及支持第三方开发者激活了iOS的整个生态良性发展。
4. 3.x版本提供非常多的功能，弥补了之前各种系统上缺陷，比如支持了早该有的文本剪切、复制、粘贴等功能，相比市场上其它智能设备更有竞争力。
5. 3.2.x版本发布，主要为兼容第一代iPad，从此系统更名为iOS。
6. 4.x版本重大变化是支持了多任务，尽管并不像桌面系统中真正的多任务处理，但这是苹果理解的在移动设备上用户所需要的多任务。随着多任务支持，双击home键的功能也变化了，之前双击是截屏操作，从此双击即为显示出最近运行的应用了。
7. 5.x版本提供更多功能，比如通知中心，iMessage免费发送短信等，但重点提供Siri功能，支持无线激活，iCloud。
8. 6.x版本大多是功能的增强，但之前一直使用的Google Maps在这个版本被替换成苹果自己的Maps。
9. 7.x版本是一次重大变化，UI由原因的拟物化设计变成扁平化设计。另外提供了控制中心，支持指纹识别，并增强了多任务处理，支持远程通知激活应用更新数据等。
10. 8.x版本加强了开放，给开发者开放了更多框架开发出更多功能的应用，比如支持小插件，支持更多操作的通知，支持第三方键盘，开放指纹识别给开发者等。
11. 9.x版本增加了很多新特性，比较明显的如iPhone 6s/6s plus支持3D-Touch，6位数字键盘，Back to App，iPad中支持分屏等多任务处理，邮件图片附件可以涂鸦等。
12. 10.x版本更加人性化了，比如，锁屏界面有三个滑屏，可以快速使用相机，相册照片自动集合，允许删除苹果默认应用，Siri开放给第三方应用等。

<br>  
除了上述表格中列出来的较大版本的发布，每个大版本发布后多少会有几个小版本更新，小版本主要是为了处理一些大版本发布后暴露出的问题或者为兼容更多设备(包括新设备发布)。另外，也有一些版本是为Apple TV、iWatch发布的，这里不再涉及。
