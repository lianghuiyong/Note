**openresty**

macOS 10.12.6 (16G29)

1.`brew install homebrew/nginx/openresty`

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


二 .ngx_lua

1。下载luajit

2。lua-nginx-module-0.10.10

3.ngx_devel_kit-0.3.0

4.nginx-1.12.1

 ./configure --prefix=/usr/local/Cellar/openresty/nginx \
         --with-ld-opt="-Wl,-rpath,/usr/local/Cellar/openresty/luajit/lib" \
         --with-cc-opt="-I/usr/local/Cellar/pcre/8.41/include" \
         --with-ld-opt="-L/usr/local/Cellar/pcre/8.41/lib" \
         --with-openssl=/usr/local/Cellar/openssl-1.0.2l \
         --add-module=/Users/huiyong/Documents/project/work/ngx_devel_kit-0.3.0 \
         --add-module=/Users/huiyong/Documents/project/work/lua-nginx-module-0.10.10
         
 5.make -j4
 
 6.make install
 