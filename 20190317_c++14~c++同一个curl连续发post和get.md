**2019.03.17**

## c++同一个curl连续发post和get
* curl_easy_init创建1个CURL句柄
* 使用这个句柄先发post，再发get，中间不curl_easy_cleanup
* 每次发的时候，要curl_easy_init(curl)，然后再curl_easy_setopt
