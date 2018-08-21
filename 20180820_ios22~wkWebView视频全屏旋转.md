**2018.08.20**

## wkWebView视频全屏旋转
### 需求
* 全局上所有vc都是竖屏
* 只有wkWebView全屏播放h5时才支持旋转横屏
### 思路
* wkWebView监听视频播放开始全屏和结束全屏
* wkWebView监听屏幕旋转
* 视频全屏的情况下，屏幕旋转时进行横屏处理
* 退出全屏时也要恢复状态栏为竖屏
### 代码
* 监听全屏
```
[[NSNotificationCenter defaultCenter] addObserver:self
                                                 selector:@selector(videoBeginFullScreen)
                                                     name:UIWindowDidBecomeVisibleNotification
                                                   object:nil];
        
[[NSNotificationCenter defaultCenter] addObserver:self
                                                 selector:@selector(videoStopFullScreen)
                                                     name:UIWindowDidBecomeHiddenNotification
                                                   object:nil];
```
* 监听屏幕旋转
```
[[NSNotificationCenter defaultCenter] addObserver:self
                                                 selector:@selector(handleDeviceOrientationDidChange)
                                                     name:UIDeviceOrientationDidChangeNotification
                                                   object:nil];
```
* self.videoFullScreen表示进入全屏
* 处理函数
```
- (void)handleDeviceOrientationDidChange {
    
    if (!self.videoFullScreen) {
        
        return;
    }
    
    UIDevice *device = [UIDevice currentDevice];
    switch (device.orientation) {
        case UIDeviceOrientationFaceUp:
            [self endFullScreen];
            NSLog(@"屏幕朝上平躺");
            break;
            
        case UIDeviceOrientationFaceDown:
            [self endFullScreen];
            NSLog(@"屏幕朝下平躺");
            break;
            
        case UIDeviceOrientationUnknown:
            [self endFullScreen];
            NSLog(@"未知方向");
            break;
            
        case UIDeviceOrientationLandscapeLeft:
            [self startFullScreenRight];
            NSLog(@"屏幕向左横置");
            break;
            
        case UIDeviceOrientationLandscapeRight:
            [self startFullScreenLeft];
            NSLog(@"屏幕向右橫置");
            break;
            
        case UIDeviceOrientationPortrait:
            [self endFullScreen];
            NSLog(@"屏幕直立");
            break;
            
        case UIDeviceOrientationPortraitUpsideDown:
            [self endFullScreenUpsideDown];
            NSLog(@"屏幕直立，上下顛倒");
            break;
            
        default:
            [self endFullScreen];
            NSLog(@"无法辨识");
            break;
    }
}

- (void)startFullScreenRight {
    
    NSLog(@"进入全屏");
    UIApplication *application = [UIApplication sharedApplication];
    [application setStatusBarOrientation: UIInterfaceOrientationLandscapeRight];
    application.keyWindow.transform = CGAffineTransformMakeRotation(M_PI / 2);
    application.keyWindow.bounds = CGRectMake(0, 0, kSCREEN_WIDTH, kSCREEN_HEIGHT);
}

- (void)startFullScreenLeft {
    
    NSLog(@"进入全屏");
    UIApplication *application = [UIApplication sharedApplication];
    [application setStatusBarOrientation: UIInterfaceOrientationLandscapeRight];
    application.keyWindow.transform = CGAffineTransformMakeRotation(3 * M_PI / 2);
    application.keyWindow.bounds = CGRectMake(0, 0, kSCREEN_WIDTH, kSCREEN_HEIGHT);
}

- (void)endFullScreen {
    NSLog(@"退出全屏XXXX");
    UIApplication *application=[UIApplication sharedApplication];
    [application setStatusBarOrientation: UIInterfaceOrientationPortrait];
    application.keyWindow.bounds = CGRectMake(0, 0, kSCREEN_WIDTH, kSCREEN_HEIGHT);
    application.keyWindow.transform = CGAffineTransformMakeRotation(M_PI * 2);
    [application setStatusBarHidden:NO];
}

- (void)endFullScreenUpsideDown {
    
    NSLog(@"退出全屏XXXX");
    UIApplication *application=[UIApplication sharedApplication];
    [application setStatusBarOrientation: UIInterfaceOrientationPortrait];
    application.keyWindow.bounds = CGRectMake(0, 0, kSCREEN_WIDTH, kSCREEN_HEIGHT);
    application.keyWindow.transform = CGAffineTransformMakeRotation(M_PI);
    [application setStatusBarHidden:NO];
}

- (void)videoBeginFullScreen {
    
    self.videoFullScreen = YES;
}

- (void)videoStopFullScreen {
    
    self.videoFullScreen = NO;
    UIApplication *application=[UIApplication sharedApplication];
    [application setStatusBarOrientation: UIInterfaceOrientationPortrait];
    [application setStatusBarHidden:NO];
}
```
