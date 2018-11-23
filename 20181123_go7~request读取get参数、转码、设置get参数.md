**2018.11.23**

## request读取get参数、转码、设置get参数
### 要做什么：
* 接收到一个http请求，要拿到其中的所有get参数
* get参数解析成map，内容decode
* 对参数map进行增删修改
* 生成一个不编码的参数url

### 步骤
* 解析url的get参数，params是map，里面的每个参数都会自动解码
* 请求url为：http://22.22.22.22/xxxxx?test=%E4%B8%AD%E5%9B%BD&time=2222222
```
params, _ := url.ParseQuery(xx.Request.URL.RawQuery)
```
* 拿到params结果
```
map[test:[中国] time:[2222222]]
```
* 修改params，删掉time参数
```
params.Del("time")
```
* 生成新的url参数字符串，并且不编码（url.QueryUnescape）
```
res, _ := url.QueryUnescape(params.Encode())
```
* 结果
```
test=中国
```