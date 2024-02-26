**2024.02.27**

## bilibili无法的问题
https://github.com/soimort/you-get/pull/3017/commits/30d6c642f94d19b979cc4ea3461db1fea1901a6b

### 需要修改src/you_get/extractors/bilibili.py
```
return 'https://interface.bilibili.com/v2/playurl?%s&sign=%s' % (params, chksum)

```
替换为
```
return 'https://api.bilibili.com/x/player/wbi/v2?%s&sign=%s' % (params, chksum)
```

### 查看you_get位置
```
pip show you-get
```

```
Name: you-get
Version: 0.4.1650
Summary: Dumb downloader that scrapes the web
Home-page: https://you-get.org/
Author: Mort Yao
Author-email: mort.yao@gmail.com
License: MIT
Location: /opt/homebrew/lib/python3.9/site-packages
Requires:
Required-by:
```
