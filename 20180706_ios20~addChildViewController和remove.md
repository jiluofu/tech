**2018.07.06**

## addChildViewController

parentVC里面增显示子vc
```

UIViewController *parentVC = [UIViewController new];
UIViewController *vc = [UIViewController new];
UINavigationController *nav = (UINavigationController *)[UIApplication sharedApplication].keyWindow.rootViewController;

[nav.view addSubview:vc.view];
[nav addChildViewController:vc];
```

## 这个子vc关闭的时候，要从parentVC上彻底移除，否则parentVC进行pushViewController时无法显示
子vc中调用
```
[self willMoveToParentViewController:nil];
[self.view removeFromSuperview];
[self removeFromParentViewController]; //ios7中崩溃
```


