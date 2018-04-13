**2018.04.11**

* UIScrollView里添加UIView
* 然后使用masonry对子view进行约束，会发现，居右的子view位置永远不对
* 父view换乘UIView就没有这个问题
* 这是因为UIScrollView的contentSize，在约束时并没有生效
* 解决办法是，UIScrollView放一个容器UIView，这个UIView撑满这个UIScrollView
* 容器UIView再去装子view，子view的约束根据容器UIView去定位即可
