## 1. 你的代码测试框架及测试范围通常是？如何做自动化测试？
a)Use XCTest to test logic and interface code.
b)Use UIAutomation of Instruments to do automatic test; then use some third-party tools to do monkey test for software's stabilization and robust.

## 2. Git，多人，中型项目中，你如何保持自己的feature branch更新？push之前的你的步骤是？
a)Fetch and merge remote branch latest code into local feature branch before adding new modules and modifying public code files.
b)The basic steps before pushing：
git checkout master
git pull
git checkout feature
git merge master
fix conflicts
git add
git commit
git checkout master
git merge feature
git commit
git push origin


## 3. 你会操作设计工具么？比如用Sketch切切图，临摹个较复杂的icon啥的。
Mastered simple skills of sketch, complicated icon copy is diffcult for me at present.

## 4. 你最称手的工具们是？可以描述一款你常用的编辑器。列举一些你常用的高级功能（或隐藏的好功能）。
I'm ashamed to answer this question. Only one paid tool, Mousepose, installed in my computer. So, the programing tools may be my specialty tools. My frequent editor is Sublime Text with some programing-related plugins installed.


## 5. 你如何对项目进行目录结构划分？如何划分模块等，可以直接来个例子。
For example, the directory structures in my point as follow:

-Modules
    -XXModule
        -Controllers
        -Models
        -Views
        -Managers
-Managers
	-Network
	-Data
	-Common
-Foundations
	-Application
    	-Categories
    	-Assistants
    	-Components
    	-Vendors
	-DataAccess
    	-Categories
    	-Assistants
    	-Components
    	-Vendors
	-Network
    	-Categories
    	-Assistants
    	-Components
    	-Vendors
-Pods

## 6. Describe your development process (software lifecycle).
Firstly, Design software architecture and data model;
Secondly, Create main directories, class files and writing interface methods' and functions' definitions;
Thirdly, writing primary logic code;
Fourthly, writing detail implementations of every class and its methods and functions
Fifthly, review and refactor code as necessary
Sixly, self-test、debug and fix bugs.


## 7. 你的英语如何？听、说、读、写，你给自己的评分是？这篇文章，https://www.theverge.com/2017/10/19/16501946/the-mr-robot-hack-report-s3e2-undo 翻译The show’s biggest hack is a kind of double spyware double-cross这一整段试试（可以说下大概用时）。

翻译：这部剧最大的看点是双间谍软件的入侵。首先，Darlene趁Elliot正睡觉时在他的电脑里植入了FBI间谍软件，监控Elliot的一举一动。Elliot醒了后察觉到了异常，我们看到他坐下后就准备入侵FBI。随后，他故意让FBI看到他在一份嵌入了URL的加密邮件，然而，当他们点击这个链接时，神不知鬼不觉地触发了下载了暴露了他们位置的反向间谍软件。本着以其人之道还治其人之身 的精神，Elliot利用了敌方的间谍软件来帮助自己反向植入间谍软件，帮助自己直达了他们的安全屋。
（看懂用时不长，翻译加写字大概用时20分钟）

## 8. 你希望成为兼职还是全职？如果是远程全职的话，你的期望薪资是怎样？
全职，期望￥100左右时薪。

## 9. 如果是兼职，你的时间情况是？期望薪资如何？
兼职，时间可以安排在下午、晚上，期望￥100左右时薪。

## 10. 你熟悉的语言是？最喜欢的语言是？对比一下。
最熟悉的是Objective-C，另外，使用过的语言有C/Javascript/Python，最喜欢Python类脚本语言。Python使用简单，入手快，支持函数式编程、闭包、动态运行不需要编译，基础库丰富，更多关注业务逻辑；OC和C++一样编译型语言性能高，它的runtime特性相比C/C++又进了一大步。

## 11. 在iOS开发中，你如何实现最优雅的解耦？对比下MVC、MVVM及其它你熟悉的Design Pattern，介绍下你的应用和项目架构建议。
我的理解：在项目业务长期变化迭代过程中很难保证代码不出现耦合，但可以在编写代码过程中遵守一些基本原则（如单一职责、面向接口编程等）以方便后续解耦。在具体细节代码中可使用MVC，也可使用MVVM，但定好规范确保团队成员间保持一致性，以不增加代码沟通成本为目的。苹果默认使用最简的MVC模式基本可以满足，最简单的模式，重构扩展起来更有优势，也可以减少沟通成本，如果造成C的臃肿，也可以使用其它的规范来规避。后续解耦重构，更多可以放在更大模块上的梳理重构，针对业务变化，把重复的代码抽离出来，能方便多处使用就是比较优雅的方式，重复的功能逻辑可以抽离出来成为一个工具类，重复的业务逻辑可以抽离出来成一个服务，重复的界面代码可以抽离出来成为一个控件，降低重复就能保持代码间的灵活，就比较优雅。

## 12. UITableView Optimizations. 例如，微信朋友圈这样的应用场景（包含图片、视频）。
避免UI线程阻塞，异步加载数据；尽量组合、减少UI元素的使用；尽量使用性能更高的UILayer渲染；尽量避免触发重新渲染的对象属性设置；对动态数据做缓存避免重复计算；对cell中的UI元素做缓存，避免UI对象频繁创建等等。

## 13. 你对bash/zsh熟悉程度如何？列举一些常用的命令，常见工具等等 (P.S. brew list，然后说说)。
a)熟悉程度：掌握基本命令使用
b)常涉及命令:
cd/rm/mkdir/open/ls/pwd
c)常涉及工具:
vi/yum/unzip/tar/pip/brew

## 14. 可否讲讲你对Apple Human Interface Guidelines的理解？
以用户为中心，保持极简、有效、流畅的交互方式；开发者遵守这些原则可确保交付给用户的交互一致性，降低用户学习成本。

Modified from [nickbalestra](https://github.com/nickbalestra/nickbalestra.github.io.git).
