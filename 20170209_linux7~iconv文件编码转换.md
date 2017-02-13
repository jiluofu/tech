**2017.02.09**

linux shell对文件进行编码转换，先生成中间文件，再mv回去
```
iconv xxx.tpl -f gbk -t utf-8 -o xxx.tpl.1
mv xxx.tpl.1 xxx.tpl
```