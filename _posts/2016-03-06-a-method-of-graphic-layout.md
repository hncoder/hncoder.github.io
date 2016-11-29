---
title: 仿蝉游记图文排版方法
date: 2016-03-06
description: 这两天查看分析了下蝉游记的图文排版，忍不住写了一个Demo。
---
为了增加应用的阅读体验，一种友好的图文排版必不可少。查看市场上各类应用，大体上有两种方式来展现图文，一种是很简单的方式，即加载H5页，另一种便是根据事先约定好的数据格式使用TableView来进行展现。使用第二种方式为了让文字段落更加优美更具多样性，也不得用到CoreText。
这两天查看分析了下蝉游记的图文排版，忍不住写了一个Demo。

浏览蝉游记图文展现界面可以发现，其中图文是以一定格式进行排版的。如下图中蓝线框所示，它是以几种类型的cell来组合展示图文，比如第一个框中的cell包含一个标题和一段文字，第二个框中的cell包含图片段落文字。当然，定义好cell类型之后，还需根据数据的具体格式来进行展现，比如服务器下发的某条数据仅包含一个标题并没有文字段落，那第一个框中的cell则只展现标题，总之每个cell需根据数据内容调整布局。

![](https://github.com/peterlog/peterlog.github.io/blob/master/img/chan1.png)

蝉游记图文中的段落文字十分美观，免不了使用CoreText，CoreText的渲染原理可以查阅相关文档，相关开源框架Github上也不少，请自行搜索。同时，展现优美的文字，需要加入第三方字体库，怎么加入请查看相关资料。

为了更灵活组装图文布局，cell的种类可以更小粒度定义。本Demo作为参考，仅定义三种基本的cell类型，分别是标题cell、图片cell以及文字段落cell，如下图蓝线框所示。通过这三种基本的cell即可组合很友好的图文了，当然，如果页面元素较复杂，可以定义出更多丰富的cell类型。相比蝉游记的cell类型定义，我想，cell粒度越小越好，比如某条数据中只包含图片或者只包含文字时，就不需去特意调整cell的布局。

![](https://github.com/peterlog/peterlog.github.io/blob/master/img/chan2.png)

定义好了三种cell，就需要定义一下数据格式了。服务器以定义好的数据格式下发，客户端解析后进行图文展现。数据采用JSON格式下发，拟定某条数据的格式如下：

        {
            "type":xx,
            "info":{
                "param1":"xxx",
                "param1":"xxx",
                ...
            }
        }
        
根据三种cell类型的定义，本Demo中对应的数据格式分别如下：

        {
            "type":0, // 标题
            "info":{
                "title":"xxx",
            }
        }

        {
            "type":1,
            "info":{
                "text":"xxx", // 锻炼文字
                "user":"xxx",  // 用户名，如果有则会以@的方式显示，无则不展示
                ...
            }
        }

        {
            "type":2, // 图片
            "info":{
                "image":"http://xx", //图片链接
                "ratio":xx, // 图片高宽比
            }
        }

那么，服务器下发的是一个多条基本数据组成的列表，如：

        [{
            "type":0,
            "info":{
                "title":"xxx",
            }
        },
        {
            "type":2, // 图片
            "info":{
                "image":"http://xx", //图片链接
                "ratio":xx, // 图片高宽比
            }
        },
        ...
        ]

这些工作确定好后，就可开始编写代码了。另外，为了实现蝉游记的导航栏变化效果，需要生成对应的高斯模糊图片，具体实现细节，可参考本文 [demo源码](https://github.com/hncoder/ImageTextLayout) 吧。下图为demo截图（有需要的朋友请下载体验哦）：

![](https://github.com/peterlog/peterlog.github.io/blob/master/img/chan3.png)

本Demo仅实现了图文排版的展开，相对比较简单，但对于图文编辑并怎么保存数据以及怎样同步到服务器就不是这么简单了，分析相关应用目前图文编辑有使用TableView来插入图片文字的，有使用CoreText框架的，有使用WebView来实现的。
