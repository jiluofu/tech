**2017.10.31**

**charles抓https**



## 配置 Charles 根证书

![image](http://upload-images.jianshu.io/upload_images/51001-67bb750cd29e3ab7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

之后会弹出钥匙串，如果不弹出，请自行打开钥匙串，如下图：

![image](http://upload-images.jianshu.io/upload_images/51001-0b9f8e86b01f1fa4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

系统默认是不信任 Charles 的证书的，此时对证书右键，在弹出的下拉菜单中选择『显示简介』，点击使用此证书时，把使用系统默认改为始终信任，如下图：

![image](http://upload-images.jianshu.io/upload_images/51001-08cb4bd4d4df1df9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后关闭，就会发现 charles 的证书已经被信任了，如下图：

![image](http://upload-images.jianshu.io/upload_images/51001-a04a103ab4cb6f4e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 在移动设备上配置证书

如下图，选择在移动设备上安装 Charles 根证书：

![image](http://upload-images.jianshu.io/upload_images/51001-a8ccf2541ef0e0d8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

会弹出一个提示框，如下图：

![image](http://upload-images.jianshu.io/upload_images/51001-d9fec8d8522b30a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

进入手机设置界面：

![image](http://upload-images.jianshu.io/upload_images/51001-b561c29c7b816365.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


然后打开手机的浏览器，输入
`charlesproxy.com/getssl` 会弹出如下界面：

![image](http://upload-images.jianshu.io/upload_images/51001-34a974c5a073694c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


点击安装即可，如果出现的不是这个界面，那么把链接换成
`https://www.charlesproxy.com/documentation/additional/legacy-ssl-proxying/`，点击安装 itself 后面的 here 就可以了。

这里以简书为例...😜,

![image](http://upload-images.jianshu.io/upload_images/51001-6b19c4004ad16aaf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


此时还是获取不到 https 的数据，各位童鞋不要着急，下面还有操作，接着还是进入 Charles ,如下图操作：

![image](http://upload-images.jianshu.io/upload_images/51001-f8f79ffdd6951103.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如下图，勾选`Enable SSL Proxying`,点击添加，弹出下面的对话框，Host 表示你要抓取的 ip 地址或是链接，Port 填写 443 即可：

![image](http://upload-images.jianshu.io/upload_images/51001-13151599fb9bae42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


设置完成后，就可以抓取数据啦，如下图：

![image](http://upload-images.jianshu.io/upload_images/51001-147c003efb39a432.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**手机为什么https请求是unknown？**
**通用->关于本机->证书信任设置->CA勾选 选择charles的CA**
**模拟器里安装证书，勾选信任后需要重启才能生效**
