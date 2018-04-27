**2018.04.29**

## UICollectionView动画修改contentOffset.x移动时，有些cell会突然消失

```
[self.collectionView layoutIfNeeded]
```
* 修改后要执行layoutIfNeeded
* 动画移动前，不要去reloadData，如果一定要在移动前修改cell，可以在didSelectItemAtIndexPath中直接调用willDisplayCell中自定义的修改cell样式的方法
* 把点击之前的cell对应的数据进行清理，然后修改cell样式；再对当前点击对象数据进行设置，然后修改cell样式
