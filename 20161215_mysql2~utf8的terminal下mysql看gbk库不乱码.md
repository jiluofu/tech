**2016.12.15**

utf8的terminal下mysql看gbk库不乱码
iterm里mysql查看数据库中文都是问号，强制加字符集设定为utf8

```mysql -uxxxx -p -hxxxxxx -Pxxxx --default-character-set=utf8```