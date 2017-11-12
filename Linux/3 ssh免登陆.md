## 有机器A、B。A想通过ssh免密码登录到B。

### A
1、生成公钥/私钥对。

```
ssh-keygen -t rsa
```

2、把A机下的id_rsa.pub 复制到B机的.ssh/authorized_keys文件里

```
scp /Users/huiyong/.ssh/id_rsa root@192.168.0.2:/root/.ssh/authorized_keys
```

3、修改文件权限
```
chmod 600 /root/.ssh/authorized_keys
```