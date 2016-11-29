---
title: 源码分享：APIRequester & PTWVJSBridge
date: 2016-02-21
description: 前段时间整理了两份代码，谈不上是开源项目，因为都是基于开源代码上优化修改的。

---

前段时间整理了两份代码，谈不上是开源项目，因为都是基于开源代码上优化修改的。

## APIRequester

[APIRequester](https://github.com/peterlog/APIRequester)是一种API网络请求方案，基于RTNetworking修改，一是为了加深理解API粒度化思想，二是对于自身项目，RTNetworking不能拿来直接使用，作者在博客评论也建议重写。

需了解RTNetworking请查看博客文章[《iOS应用架构谈 网络层设计方案》](http://casatwy.com/iosying-yong-jia-gou-tan-wang-luo-ceng-she-ji-fang-an.html)及作者[Github源码](https://github.com/casatwy/RTNetworking)。

相比RTNetworking，APIRequester整体结构相差无几，但有些类的含义及内部实现做了调整，如APIRequestService将负责请求URLRequester的生成以及数据的处理（包括是否需要加解密、压缩等），因此在使用上也有所区别。APIRequestService被定义为一个protocol，开发人员可根据项目具体情况实现。了解Severce的思想可参考源码中已实现的一个通用的Service（APIRequestCommonService）。

总的来说，APIRequester主要是对RTNetworking再实现，目前网络请求缓存还未完成，在后续项目实际开发中再进一步优化完善，欢迎交流学习。具体细节请参考[APIRequester Github源码](https://github.com/peterlog/APIRequester)，其中给出了清晰的使用Demo。

## PTWVJSBridge

[PTWVJSBridge](https://github.com/peterlog/PTWVJSBridge)是基于开源库[WebViewJavascriptBridge](https://github.com/marcuswestin/WebViewJavascriptBridge)的优化，优化的目的有以下几点：

1 让Native端注册方法、JS端调用方法更友好便利；

2 JS端调用Native端时，Native端可异步返回结果；

3 保留最常用功能，即仅支持JS端调用Native注册方法，所以修改了WebViewJavascriptBridge源码，去掉其它在一般项目中几乎用不着的功能。

PTWVJSBridge使用说明如下：

### 1）Native端注册方法

    // 创建webView，不要设置 webView.delegate
    self.webView = [[UIWebView alloc] initWithFrame:self.view.bounds];
    [self.view addSubview:_webView];

    // 创建JSBridge
    self.bridge = [[PTWVJSBridge alloc] initWithWebView:_webView bridgeName:@"ptBridge" delegate:self];

    // 注册js调用native端的方法
    [_bridge registerHandler:@"testObjcCallback" target:self selector:@selector(testObjcCallback:callback:)];

### 2）Javascript端调用

	if(window.ptBridge)
	{
    	ptBridge.testObjcCallback({
            // 传递给native端的参数，是一个json格式数据
            data:{
                    param1:"parma1",
                    param2:"parma2"
            },
            callback:function(data){
                    // native 回调，json格式数据
            }
        });
	}

或者：

	if(window.ptBridge)
	{
        ptBridge.send("testObjcCallback",{
            data:{
                    param1:"parma1",
                    param2:"parma2"
            },
            callback:function(data){
                    // native 回调
            }
        });
	}

### 3）Native端方法处理回调
	- (void)testObjcCallback:(id)data callback:(WVJBResponseCallback)cb
	{
    	// 收到js传递过来的数据是一个NSDictionary
    	NSLog(@"收到数据:%@",[data description]);

    	// 返回的数据到JS端，必须是一个NSDictionary
    	if (cb)
    	{
       		// 返回结果给js端
        	cb(@{@"code":@(0)});

        	// 也可以异步返回数据，如
			/*
        	dispatch_async(dispatch_get_global_queue(0, 0), ^{
    		// TO DO: 做一些网络数据请求操作或者其它处理

    			dispatch_async(dispatch_get_main_queue(), ^{
        			//主线程中将结果回调给JS端
        			cb(@{...});
    			});
			});
			*/
    	}

	}
