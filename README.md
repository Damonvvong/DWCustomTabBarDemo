

#进来的朋友点个星星呀~

---
# 2015-10-24
- 有朋友私信我说用 Xcode6.4运行我程序有问题。

> target specifies product type 'com.apple.product-type.bundle.ui-testing', but there's no such product type for the 'iphonesimulator' platform

- 如果你也遇到如下问题，可以尝试stackoverflow上的[这个解答](http://stackoverflow.com/questions/31465852/target-specifies-product-type-com-apple-product-type-bundle-ui-testing-but-th)

- 其实我本人还是建议装最新版的 Xcode 的。

# 2015-10-20

----

### 写在最前面
- 昨天在[这里](https://github.com/NoCodeNoWife/LLRiseTabBar-iOS)看到一种完全自定义的 TabBar，但是作者说缺陷是自己继承的是 UIButton，和系统的 UITabBarButton 有所区别。
- 接着，[又在这里](https://github.com/lianleven/LLRiseTabBar-iOS)给出了一种直接利用系统自带的 tabBar 来实现。
- ~~但是我发现两者都有一个共同的特点，就是利用到了一个占位控制器，个人感觉不是特别好。~~（一定是昨晚没睡好，原作者其实没有用占位控制器，之后后面那哥们搞了个占位控制器）
- 所以献上自己写的一个小 Demo，供大家对比学习，如有不足，欢迎 issue，共同学习。



----
###个人感觉对前两者的优化

- 首先，我觉的在 AppDelegate.m 文件中写的东西越少越好，我对前作者的项目进行了优化，把添加自控制器功能加入到了 TabBarController 的 ViewDidLoad 中。尽量做到，自己的事情，写到自己的控制器中。

- 其次，不使用占位控制器的情况下，在 tabBar 的最中心添加一个按钮。

- 最后，对于自定义这个东西，其实我自己也是很喜欢，但是由于不开源，自定义的控件很难完美的做一个和系统一模一样的功能，所以给出一个在系统基础上，适当修改，满足需求的情况下，带上系统的控件。

----

### 实现思路

- 要做到[这里](https://github.com/NoCodeNoWife/LLRiseTabBar-iOS)所提到的需求，我是这么做的：
- 首先是只添加4个控制器。
- 再自定义一个 DWTabBar 并继承 UITabBar。
- 在DWTabBar的 initWithFrame 中添加一个按钮（这个按钮我也是使用了自定义，原因有两个，一个是因为图片文字是上下结构，第二个是我吧点击事件写到了DWTabBar.m 文件中，原作者的按钮点击是通过代理实现的）
- 添加完按钮之后，重写DWTabBar的 setFrame 方法，自定义 TabBar 内部的控件位置。
- 最后在 DWTabBarController 中，利用 KVC 吧系统的TabBar类型修改了。


