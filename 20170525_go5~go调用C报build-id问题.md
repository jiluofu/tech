**2017.05.25**

## centos4.3下，使用go1.8版本，调用C报错build-id问题
* 需要修改go/src/cmd/build.go，把disableBuildID中的--build-id那一行注释
* 重新编译go
    * 把当前的go目录复制一份，命名为go1.8
    * export GOROOT_BOOTSTRAP=/home/work/tmp/go1.8
    * source ~/.bash_profile
    * ./go/src/make.bash重新编译




