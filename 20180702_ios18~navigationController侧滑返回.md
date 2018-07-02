**2018.07.02**

## UINavigationController实现侧滑返回

* appDelgate中didFinishLaunchingWithOptions里，设置root
```
self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
self.window.backgroundColor = [UIColor whiteColor];
self.window.rootViewController = [[BaseNav alloc] init];
[self.window makeKeyAndVisible];
```

* BaseNav继承UINavigationController

* BaseNav实现UINavigationControllerDelegate和UIGestureRecognizerDelegate
```
@interface BaseNav ()<UINavigationControllerDelegate,UIGestureRecognizerDelegate>

@end
```
* viewDidLoad中设置代理
```
//UIGestureRecognizerDelegate
self.interactivePopGestureRecognizer.delegate = self;

//UINavigationControllerDelegate
self.delegate = self;
```
* 实现pushViewController，禁止侧滑，侧滑放到后面UINavigationControllerDelegate处理
```
- (void)pushViewController:(UIViewController *)viewController animated:(BOOL)animated{
    
    //push 时关闭手势响应
    self.interactivePopGestureRecognizer.enabled = NO;
    
    [super pushViewController:viewController animated:animated];
}
```

* UINavigationControllerDelegate的didShowViewController中去处理侧滑，保证第1级root时关闭手势，避免回到root时卡死
```
- (void)navigationController:(UINavigationController *)navigationController didShowViewController:(UIViewController *)viewController animated:(BOOL)animated{
    
    if (navigationController.viewControllers.count == 1) {
        //如果是 rootViewController 就关闭手势响应
        self.interactivePopGestureRecognizer.enabled = NO;
    }
    else{
        //如果不是 rootViewController 就开启手势响应
        self.interactivePopGestureRecognizer.enabled = YES;
    }
}
```

* BaseNav.h
```

#import <UIKit/UIKit.h>

@interface BaseNav : UINavigationController

@end

```

* BaseNav.m
```
#import "BaseNav.h"

@interface BaseNav ()<UINavigationControllerDelegate,UIGestureRecognizerDelegate>

@end

@implementation BaseNav

- (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view.
    
    //UIGestureRecognizerDelegate
    self.interactivePopGestureRecognizer.delegate = self;
    
    //UINavigationControllerDelegate
    self.delegate = self;
}

- (void)didReceiveMemoryWarning {
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

- (void)pushViewController:(UIViewController *)viewController animated:(BOOL)animated{
    
    //push 时关闭手势响应
    self.interactivePopGestureRecognizer.enabled = NO;
    
    [super pushViewController:viewController animated:animated];
}

#pragma mark - UINavigationControllerDelegate

- (void)navigationController:(UINavigationController *)navigationController didShowViewController:(UIViewController *)viewController animated:(BOOL)animated{
    
    if (navigationController.viewControllers.count == 1) {
        //如果是 rootViewController 就关闭手势响应
        self.interactivePopGestureRecognizer.enabled = NO;
        self.interactivePopGestureRecognizer.delegate = nil;
    }
    else{
        //如果不是 rootViewController 就开启手势响应
        self.interactivePopGestureRecognizer.enabled = YES;
        self.interactivePopGestureRecognizer.delegate = self;
    }
}

@end

```



