**2017.06.30**

## 使用rsync

* 默认设置保存认证，选yes
* files目录放到/home/work/tmp/目录下
* 限速3000KB

```
rsync  -azP --bwlimit=3000 -e "ssh  -o PubkeyAuthentication=yes  -o stricthostkeychecking=no" xxx.com:/home/work/files /home/work/tmp/

```



