**2018.04.28**

## UICollectionView每个cell动态决定大小，cell间有间距

```
layout.minimumInteritemSpacing = 20;
layout.estimatedItemSize = CGSizeMake(xxx, xxx);

- (CGSize)collectionView:(UICollectionView *)collectionView layout:(UICollectionViewLayout *)collectionViewLayout sizeForItemAtIndexPath:(NSIndexPath *)indexPath{}
```
* 动态设定大小，在代理函数里实现，不要layout.estimatedItemSize
* 两处都有estimatedItemSize，会造成初始的contentSize因为间距minimumInteritemSpacing加入，显示不全
* 去掉layout.estimatedItemSize = CGSizeMake(xxx, xxx);之后，动态计算cell宽度，这时contentSize会加入minimumInteritemSpacing，正确显示

