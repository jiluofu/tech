**2018.10.27**

## libcurl进行post
main函数，初始化和清理curl
```
// 全局初始化curl
curl_global_init(CURL_GLOBAL_ALL);  

std::string url = "http://xxxx";
std::string postParams = "aa=33&bb=33";
std::string response;

curl_post_req("http://sss", "aa=33&bb=33", response);

// 程序结束前清理curl
curl_global_cleanup();  
```

发请求，设置参数，传入url、post参数、响应
检查response_code
```
bool curl_post_req(const std::string &url, const std::string &postParams, std::string &response)  
{  
    
    CURL *curl = curl_easy_init();  
    CURLcode res;  
    if (curl)  
    {  
        // set params  
        curl_easy_setopt(curl, CURLOPT_POST, 1);
        curl_easy_setopt(curl, CURLOPT_URL, url.c_str());
        curl_easy_setopt(curl, CURLOPT_POSTFIELDS, postParams.c_str());
        curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, write_call_back);  
        curl_easy_setopt(curl, CURLOPT_WRITEDATA, (void *)&response);  
        
        // start req  
        res = curl_easy_perform(curl);  
        if (res != CURLE_OK) {

            LOG(NOTICE) << "curl_easy_perform() failed: " + std::string(curl_easy_strerror(res));      
            return false;
        }  

        long response_code = 0;
        curl_easy_getinfo(curl, CURLINFO_RESPONSE_CODE, &response_code);
        
        if (response_code < 200 || response_code >= 300 || response.empty()) {

            LOG(WARNING) << "http failed code: " << response_code;      
            return false;
        }
        else {

            LOG(NOTICE) << "http success code: " << response_code;
        }

    }  
    // release curl  
    curl_easy_cleanup(curl);  
    return true;  
}  
```  

回调函数
```
size_t write_call_back(void *contents, size_t size, size_t nmemb, std::string *userp) {

    userp->append((char *) contents, size * nmemb);
    return size * nmemb;
}
```
