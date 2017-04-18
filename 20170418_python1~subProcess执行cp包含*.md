**2017.04.18**

```
subprocess.check_output(['cp', '-r', '/home/work/test/*', '/home/work/tmp/'], universal_newlines=True)
```
把/home/work/test/目录下的所有东西复制到/home/wrok/tmp/下

但是python3.5下用subprocess执行，会报找不到/home/work/test/*这个文件或目录。

这个原因是*是shell命令通配符，这里需要增加shell=True，同时把命令合成一个字符串
```
subprocess.check_output(['cp -r /home/work/test/* /home/work/tmp/'], universal_newlines=True, shell=True)
```