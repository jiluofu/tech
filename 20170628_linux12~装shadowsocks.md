**2017.06.28**

## 在机器上装shadowsocks

```
yum install m2crypto python-setuptools
easy_install pip
pip install shadowsocks

vi  /etc/shadowsocks.json

{
    "server":"机器ip",
    "server_port":443,
    "local_address": "机器ip",
    "local_port":1080,
    "password":"222222",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}


nohup ssserver -c /etc/shadowsocks.json &

```



