**2022.10.25**

## 升级macos V，ssh报错Unable to negotiate with

```

vi ~/.ssh/config


```
### 添加
```
HostKeyAlgorithms         +ssh-rsa
PubkeyAcceptedKeyTypes    +ssh-rsa
```