macOS 10.12.6 (16G29)

1. `brew install homebrew/nginx/openresty`

2.下载openssl源码

3.编译config
```
./configure --prefix=/usr/local/Cellar/openresty \
--with-openssl=/usr/local/Cellar/openssl-1.0.2l \
--with-cc-opt="-I/usr/local/Cellar/pcre/8.41/include" \
--with-ld-opt="-L/usr/local/Cellar/pcre/8.41/lib" \
-j4 \
--with-luajit
```

4.make

5.make install