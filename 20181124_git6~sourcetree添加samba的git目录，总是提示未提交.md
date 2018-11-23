**2018.11.24**

## sourcetree添加samba的git目录，总是提示未提交
* 问题是macos上的sourcetree连远程linux上的samba目录，遇到了文件权限变更，会认为文件都要修改
## 解决方法
* 进入项目的.git目录，修改config的core
* filemode=false，autocrlf=true