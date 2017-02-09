**2017.01.09**

问题：iOS下，header滚动时吸顶，使用position:fixed，当底下输入评论文本框，调起软键盘，在UC浏览器下，position:fixed失效，header位置错乱。safari直接把header扔回顶部。

成本低的解决方法：评论文本框focus时，讲header改成position:static，下面的部分留白去掉，变成普通不吸顶。