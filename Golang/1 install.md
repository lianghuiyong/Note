# Mac平台

```
brew install go
```

## 环境设置
```
vim .bash_profile 

export GOPATH=/usr/local/Cellar/go/1.7.6
export GOBIN=$GOPATH/bin
export PATH=$PATH:$GOBIN

source .bash_profile
```

## 查看安装信息

```
go env


```