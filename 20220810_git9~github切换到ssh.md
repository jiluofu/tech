**2022.08.10**

## github切换到ssh
* git remote -v 查看远程连接的方式
* git remote rm origin 删除原先HTTPS的连接方式
* git remote add origin SSH地址，连接方式更改为SSH方式
* git remote -v 会发现已经更改成了ssh的方式

* ssh -T git@github.com 测试
* ssh-keygen -t ed25519 -C "your_email@example.com"
