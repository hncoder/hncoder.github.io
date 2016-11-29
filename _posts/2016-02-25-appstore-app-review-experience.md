---
title: 那些AppStore审核踩过的坑
date: 2016-02-25
description: 梳理一下产品各个版本发布以来踩过的一些坑，这些坑很常见易犯。
---

我司产品分了三个端，属于创业早期产品，每次提交发布都是心惊胆战的。现梳理一下产品各个版本发布以来踩过的一些坑，这些坑很常见易犯。

在做用户端的第一个版本时，在产品功能还未完善、后台还保留测试数据的时候秉着试试水的侥幸就猴急地提交了一个版本，当时提交我毫无含蓄地向领导表示希望极其渺茫，苹果这么注重用户体验，审核人员不是傻子，就等着被高富帅无情拒绝吧。果不其然，审核结果是被拒绝了，但是给出的理由是，应用中有展现送iPhone的活动，但没有给出活动和苹果公司无关的表明。

App完善好后，立即提交了第二次审核，这次不幸又被拒了，有两个原因，一是被队友坑了，不知哪位在Info.plist里开启了后台运行权限（这点竟在第一次审核未被告知，好无赖），而后台运行权限只能是音乐类、VOIP类应用才可申请；二是应用中加入了金币乐兑这个模块，所述的金币很容易被误解为类似游戏虚拟币，金币商品容易被误解为虚拟商品，而苹果规定如果是购买虚拟商品（如游戏币、购买电子图书音像等）一定需要使用应用内支付，因此，苹果明确要求我们给出解释。于是，我们以中英文（理论上中文就可以，加上英文出于保守考虑，连续被拒被吓怕了）的方式给予了回复，并在备注信息中注明。
斗胆贴出我们当时给出说明解释，如果有类似产品，可以作为一点参考：

*金币乐兑是面向会员的参加特定的活动，所积累的金币数进行的商品兑换。金币一般都可兑换成商家所提供的服务或商品。当会员兑换金币时，系统自动扣除金币积分，并可根据各个条件查询到每笔兑换记录、商品兑换明细。*

*金币说明如下：*

*1. 金币专属飞常U惠，仅限飞常U惠内使用；*

*2. 金币可以累积，不过期；*

*3. 在飞常U惠消费，均可获得金币，金币的基准返点比例为商品售价的100%；*

*4. 消费者在付款后，消费者在完成该笔交易后（飞常U惠系统显示该交易状态为“交易成功”），才能得到此次交易的相应金币；*

*5. 金币不能兑现，不可转让，不可单独购买。*

*The so-called gold-exchange is that the VIP users can exchange goods or offline-services with their virtual gold coins. After the users exchange, their virtual gold coins will be deducted in our system, and they can check the detail exchange records in the application.*

*Details of virtual gold coins as follows:*

*1. The virtual gold coins are exclusive to 飞常U惠 app, only consumed in the app.*

*2. The virtual gold coins can be accumulated, not expired.*

*3. The users obtain rebate virtual gold coins after purchasing commodities or offline-services offered by the near shops in the app; the rebate ratio is 100% of price of commodities or offline-services they purchased.*

*4. After their payment of commodities or offline-services (as the app to show that the transaction is successful), the users will get corresponding virtual gold coins.*

*5. The virtual gold coins can not be exchanged to cash, not transferable, not purchased.*


被拒的最老火的是上一个版本审核，连续被拒绝了三次，原因很怄火——AppStore上的营销截图与App功能无关。不过想想，这也是在所难免的，我司这么拼面子的公司，文案要有多浮夸就有多浮夸，估计碰到了某个处女座的审核人员实在看不下去了。结果还是从App里直接截了三张图上传才通过了审核。
另外，还有一些其它端被拒的情况，就一并做个最后总结吧：

1）在高富帅面前，保持一个良好的认错态度。每次被拒后，我都会立即回复表示感谢，如需解释的则给出解释，比如我回复的开头都是：Thank you for your information…。这条不是绝对真理，只是个人觉得这是一个长期打交道的过程，态度上保持友好点没有坏处。至少，千万不要去跟“高富帅”怄气骂娘咯；

2）上传App审核时后台有轻微测试（垃圾）数据并不会影响审核，但是不要把苹果当傻子，最好在App审核期间把后台测试（垃圾）数据都清除，同时App的首页交互不能太烂了，做的好看点，审核人员看着舒服，说不定一高兴就轻松过了；

3）App内有活动，比如抽奖类活动，或者有实物商品买卖，一定要在显眼位置声明与苹果公司无关；

4）App中不能有检查更新按钮，另外，对于早期App，由于前期考虑不周，造成很多情况下新版本开发时又不想去兼容老版本，于是就很早在版本中做了后台控制强制升级的功能，但这个强制升级弹窗千万不要出bug，如果在新版本中弹出让审核人员看到，那就很无幸撞枪口上了;

5）App有下载视频的功能很容易被拒，尽管视频是自己的也可能被拒，我们就有被无情拒了，只能说明苹果很看重音乐、视频、图书下载版权；

6）App中不能有云测SDK(Testin sdk)，被拒后这点特意被苹果工作人员电话告知;

7）AppStore上营销截图、文案一定要和App功能点匹配，如果是特意设计的图，建议设计时图中嵌入某些App功能界面截图，切记一定不能浮夸，不能浮夸，不能浮夸，重要的事说三遍。

