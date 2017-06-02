**2017.06.02**

## golang用bytes.TrimSpace无法去掉C初始化数组带来的\0
* Golang中字符串与C中的字符串的不同之处：C中的字符串是以\x0为结尾的字节序列，而Golang中的字符串则更严格，并不是以\x0为结尾来判断，而是计算字符串变量的值中的所有字节。
* TrimSpace处理的只是空格
* 解决办法是bytes.Time
    ```
    text = bytes.Trim(text, "\x00")
    ```



