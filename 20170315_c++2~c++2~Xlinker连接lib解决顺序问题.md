**2017.03.15**

```
gcc -o output.bin -Xlinker "-(" liba.ar libb.ar -Xlinker "-)" -lrt
```

这样可以解决库顺序的问题了！问题是，如果你的库相互间的依赖如果错综复杂的话，可能会增加连接的时间。