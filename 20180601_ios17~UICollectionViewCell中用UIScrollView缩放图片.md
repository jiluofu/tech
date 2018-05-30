**2018.06.01**

## UICollectionViewCell中添加UIScrollView，使用UIImageView来缩放图片

* 设置scrollView，maximumZoomScale，minimumZoomScale，delegate
```
self.scrollView.userInteractionEnabled = YES;
self.scrollView.scrollEnabled = YES;
self.scrollView.bounces = YES;
self.scrollView.maximumZoomScale = 3.0f;
self.scrollView.minimumZoomScale = 1.0f;
self.scrollView.delegate = self;
self.scrollView.clipsToBounds = YES;
```
* cell在willDisplay的时候，要恢复缩放状态
```
[self.scrollView setZoomScale:self.scrollView.minimumZoomScale animated:NO];
```
* 双击图片放大
```
- (void)onDoubleTappedGestureRecognizer:(UITapGestureRecognizer *)recognizer {
    

    if (self.scrollView.zoomScale > self.scrollView.minimumZoomScale) {
        // 已经放大 现在缩小
        [self.scrollView setZoomScale:self.scrollView.minimumZoomScale animated:YES];
    }
    else {
        [self.scrollView setZoomScale:self.scrollView.maximumZoomScale animated:YES];
    }

}
```
* UIScrollViewDelegate，选中要缩放的UIImageView
```
- (UIView *)viewForZoomingInScrollView:(UIScrollView *)scrollView
{
    return self.imageView;
}
```
* UISCrollViewDelegate，缩放时保持图片居中
```
- (void)scrollViewDidZoom:(UIScrollView *)scrollView
{
    CGFloat scrollW = CGRectGetWidth(scrollView.frame);
    CGFloat scrollH = CGRectGetHeight(scrollView.frame);
    
    CGSize contentSize = scrollView.contentSize;
    CGFloat offsetX = scrollW > contentSize.width ? (scrollW - contentSize.width) * 0.5 : 0;
    CGFloat offsetY = scrollH > contentSize.height ? (scrollH - contentSize.height) * 0.5 : 0;
    
    CGFloat centerX = contentSize.width * 0.5 + offsetX;
    CGFloat centerY = contentSize.height * 0.5 + offsetY;
    
    self.imageView.center = CGPointMake(centerX, centerY);
}
```
