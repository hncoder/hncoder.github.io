---
title: 将MVVM演化为MVVMM
date: 2016-05-02
description: 结合项目实情，将MVVM演化为MVVM+Manager模式。
---

我司产品属于初创项目，早期业务相对简单，最初项目中采用了简单的MVC设计模式。然而随着业务逻辑增多，某些Controller变得十分臃肿。众所周知，MVVM模式解决了Controller的臃肿并方便单元测试，为了方便后续代码维护，在上版本新功能开发中，项目开始使用[MVVM模式](http://www.sprynthesis.com/2014/12/06/reactivecocoa-mvvm-introduction)进行开发。   

![](https://raw.githubusercontent.com/hncoder/hncoder.github.io/master/assets/images/MVVM.png) 

但从上图可以看出，MVVM模式中，Controller即便清爽了，但无疑是将臃肿的代码移到了ViewModel中。  
上述上个版本中所开发的新功能为“爱疯抢”，从业务交互及界面状态展现来看，有多个界面存在相同的业务交互和元素展现，比如正在疯抢列表、疯抢商品详情、我关注的疯抢、我参与的疯抢等等，这些界面都存在抢拍、提醒、取消提醒、关注、取消关注、购买、支付已抢拍成功商品等业务交互，同时按钮展现（抢拍、提醒等状态切换）及时间展现（抢拍开始时间、抢拍中倒计时、下次抢拍时间）等展示逻辑也无差别。  
因此，结合这些具体情形，我在模块类设计时，决定将这些公有的业务交互及界面展现状态转换逻辑抽离出来。依照MVVM设计模式，这些逻辑代码理应放到ViewModel中。  
但从实际出发，如果将所有的逻辑的都放进ViewModel，将导致ViewModel变得十分臃肿，同时使得具体业务逻辑代码不够粒度化，这样无疑在代码上耦合严重、不利于代码扩展及重复利用。举个例子，假如某些界面出现不同的展现方式及逻辑，但却具有相同的业务交互逻辑（抢拍、提醒、关注等），针对这种情况，就不能共用同一个ViewModel来满足了，这时不得不新写一个ViewModel来包含不同的展现逻辑和相同的业务交互逻辑，这无疑导致编写重复的业务交互代码，增加代码维护成本。  
​为了ViewModel最终不变得臃肿，同时利于代码扩展及重复利用，我想到将ViewModel的职责更进一步细化，ViewModel负责网络请求及界面展示逻辑，而将业务交互部分单独再抽出来，将其封装在独立的业务交互处理类Manager（或许这里取名Manager不恰当，暂且先这样）当中。  
​这样，不同展现逻辑但具有相同业务交互逻辑的界面即可使用不同的ViewModel而共用同一个Manager了，满足了一份业务交互逻辑代码可以多处使用、多处组装，在一定程度上不仅降低了开发工作量，同时增强了代码的可维护性。    
我将这种演化后的模式称为MVVM+Manager模式，简称为MVVMM。Manager既然负责业务交互逻辑，这其中的业务就少不了和服务器交互、和本地数据交互等，因此，MVVMM模式的示意图可以定义为如下所示：  

![](https://raw.githubusercontent.com/hncoder/hncoder.github.io/master/assets/images/MVVMM.png) 

为了更具体说明MVVMM模式各个部分职责，我写了一个简明的逻辑描述[Demo](https://github.com/hncoder/MVVMM.git)供参考。  
对于复杂的功能模块，ViewModel仍然显得很臃肿的话，可继续将其职责再细化，例如将网络请求逻辑也从ViewModel中抽离出来单独成为一个处理类，类似猿题库中即使用单独的DataController类来负责网络数据请求，详情可以参考[博文](http://gracelancy.com/blog/2016/01/06/ape-ios-arch-design/)。 
**MVVMM Demo**：  
https://github.com/peterlogme/MVVMM.git  
参考：  
MVVM模式：  
http://www.sprynthesis.com/2014/12/06/reactivecocoa-mvvm-introduction  
http://yulingtianxia.com/blog/2015/05/21/ReactiveCocoa-and-MVVM-an-Introduction/  
猿题库MVVM设计博文：  
http://gracelancy.com/blog/2016/01/06/ape-ios-arch-design/  
