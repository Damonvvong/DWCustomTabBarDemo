#基于 KVC 的 咸鱼 TabBar 模仿

> 效果图如下



![image](http://7xlv6p.com1.z0.glb.clouddn.com/DWTabBarController.gif)

> 核心代码

```objc

/**
 *  添加子控制器，我这里值添加了4个，没有占位自控制器
 */
- (void)setUpChildViewController{
    
    [self addOneChildViewController:[[UINavigationController alloc]initWithRootViewController:[[DWHomeViewController alloc]init]]
                          WithTitle:@"首页"
                          imageName:@"home_normal"
                  selectedImageName:@"home_highlight"];
    
    [self addOneChildViewController:[[UINavigationController alloc]initWithRootViewController:[[DWSameFityViewController alloc] init]]
                          WithTitle:@"同城"
                          imageName:@"mycity_normal"
                  selectedImageName:@"mycity_highlight"];
    
    
    [self addOneChildViewController:[[UINavigationController alloc]initWithRootViewController:[[DWMessageViewController alloc]init]]
                          WithTitle:@"消息"
                          imageName:@"message_normal"
                  selectedImageName:@"message_highlight"];
    
    
    [self addOneChildViewController:[[UINavigationController alloc]initWithRootViewController:[[DWMineViewController alloc]init]]
                          WithTitle:@"我的"
                          imageName:@"account_normal"
                  selectedImageName:@"account_highlight"];
    
}

/**
 *  添加一个子控制器
 *
 *  @param viewController    控制器
 *  @param title             标题
 *  @param imageName         图片
 *  @param selectedImageName 选中图片
 */

- (void)addOneChildViewController:(UIViewController *)viewController WithTitle:(NSString *)title imageName:(NSString *)imageName selectedImageName:(NSString *)selectedImageName{
    
    viewController.view.backgroundColor     = DWRandomColor;
    viewController.tabBarItem.title         = title;
    viewController.tabBarItem.image         = [UIImage imageNamed:imageName];
    UIImage *image = [UIImage imageNamed:selectedImageName];
    image = [image imageWithRenderingMode:UIImageRenderingModeAlwaysOriginal];
    viewController.tabBarItem.selectedImage = image;
    [self addChildViewController:viewController];
    
}


```

> 只加了4个控制器，但是有5个按钮。
> 基于系统自带，重新布局，没有完全自定义


