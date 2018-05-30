**2018.05.30**

## UICollectionView做全屏浏览器，显示单图，横向滚动，图直接间距20，pagingEnabled=YES，滚动起来会露出间隔

* 设置collectionView.pagingEnabled=YES
* 当前collectionView的frame宽度设置为屏幕宽度+
* 自定义UICollectionViewFlowLayout，itemSize是屏幕宽度，设置间距minimumLineSpacing为20
```
xxxFlowLayout *layout = [xxxFlowLayout new];
layout.itemSize = CGSizeMake(SCREEN_WIDTH, SCREEN_HEIGHT);
layout.scrollDirection = UICollectionViewScrollDirectionHorizontal;
layout.minimumLineSpacing = 20;
layout.minimumInteritemSpacing = 0;
```
* 自定义的flowlayout中，设置contentSize，宽度为图片个数*(屏幕宽度+间距20)
```
- (CGSize)collectionViewContentSize {
    
    CGSize size = [super collectionViewContentSize];
    size.width = ITEM_COUNT * (kSCREEN_WIDTH + 20);
    return size;
}
```
* 这样collectioView加宽20，留出了间距，横向滑动的contentSize增加了间距20，保证每次滑动都会让出间距的位置
