**2018.09.25**

## item2在ssh下中文乱码
~/.bashrc 文件里面加入以下代码：
```
export LANG='UTC-8'
export LC_ALL='en_US.UTF-8'
```
