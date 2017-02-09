**2017.02.08**

增加写权限
chmod +w xxx

增加执行权限
chmod +x

取消执行权限
chmod -x

ls

 -l中显示的内容如下：

-rwxrw-r‐-1 root root 1213 Feb 2 09:39 abc

- 10个字符确定不同用户能对文件干什么

- 第一个字符代表文件（-）、目录（d），链接（l）

- 其余字符每3个一组（rwx），读（r）、写（w）、执行（x）

- 第一组rwx：文件所有者的权限是读、写和执行

- 第二组rw-：与文件所有者同一组的用户的权限是读、写但不能执行

- 第三组r--：不与文件所有者同组的其他用户的权限是读不能写和执行

也可用数字表示为：r=4，w=2，x=1  因此rwx=4+2+1=7

- 1 表示连接的文件数

- root 表示用户

- root表示用户所在的组

- 1213 表示文件大小（字节）

- Feb 2 09:39 表示最后修改日期

- abc 表示文件名

 

改变权限的命令

chmod 改变文件或目录的权限

chmod 755 abc：赋予abc权限rwxr-xr-x

chmod u=rwx，g=rx，o=rx abc：同上u=用户权限，g=组权限，o=不同组其他用户权限

chmod u-x，g+w abc：给abc去除用户执行的权限，增加组写的权限

chmod a+r abc：给所有用户添加读的权限

改变所有者（chown）和用户组（chgrp）命令

chown xiaoming abc：改变abc的所有者为xiaoming

chgrp root abc：改变abc所属的组为root

chown root ./abc：改变abc这个目录的所有者是root

chown ‐R root ./abc：改变abc这个目录及其下面所有的文件和目录的所有者是root

 

改变用户所在组

在添加用户时，可以指定将该用户添加到哪个组中，同样用root的管理权限可以改变某个用户所在的组

- usermod ‐g 组名 用户名

你可以用

- usermod ‐d 目录名 用户名，改变该用户登录的初始目录