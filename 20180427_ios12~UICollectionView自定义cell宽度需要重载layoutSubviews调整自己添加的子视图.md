**2018.04.27**

## UICollectionView用sizeForItemAtIndexPath动态设定cell宽度，reloadData后有些cell的子视图宽度有问题

```
- (void)layoutSubviews {
    
    [super layoutSubviews];
    
    // 根据estimateditemsize，更新title这些子视图
    self.title.frame = self.contentView.frame;
}
```
* 子视图都放到contentView下
* cell要重载layoutSubviews，把子视图的frame根据contentView.frame进行更新


