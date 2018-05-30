**2018.05.31**

## UITapGestureRecognizer使用requireGestureRecognizerToFail区分单击双击

* 添加单击事件
```
UITapGestureRecognizer *singleGesture = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(onSingleTappedGestureRecognizer:)];
singleGesture.numberOfTapsRequired = 1;
[self addGestureRecognizer:singleGesture];
```
* 添加双击事件
```
UITapGestureRecognizer *doubleGesture = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(onDoubleTappedGestureRecognizer:)];
doubleGesture.numberOfTapsRequired = 2;
[self addGestureRecognizer:doubleGesture];
```
* 添加单击双击区分
```
[singleGesture requireGestureRecognizerToFail:doubleGesture];
```