**openresty**

# macOS 10.12.6 (16G29)

1. brew install pcre openssl

2. brew install homebrew/nginx/openresty

3. vim .bash_profile

   export NGINX_HOME=/usr/local/Cellar/openresty/1.11.2.5/nginx/sbin:

   export PATH=$PATH:$NGINX_HOME

4. Code 

   ```
   worker_processes  1;        #nginx worker 数量
   error_log /Users/huiyong/Documents/project/work/logs/error.log;   #指定错误日志文件路径
   events {
       worker_connections 1024;
   }

   http {
       server {
           listen 6767;
           location / {
               default_type text/html;
               content_by_lua '
                   ngx.say("Ping!  You got here because you have no cookies!")
               ';
           }
       }
   }
   ```

5. nginx -c /Users/huiyong/Documents/project/work/conf/nginx.conf

6. curl  127.0.0.1:6767

   Ping!  You got here because you have no cookies!


# CentOS
1、安装依赖库
   ```
yum install readline-devel pcre-devel openssl-devel gcc
   ```
2、下载openresty
```
wget --no-check-certificate https://openresty.org/download/openresty-1.11.2.2.tar.gz
```
   
3、解压
```
tar xvf ngx_openresty-1.9.7.1.tar.gz
```
4、./configure，默认配置，openresty会安装在/usr/local/openresyt


5、gmake


6、gmake install

7、设置环境变量：

vim ~/.bash_profile

```
export NGINX_HOME=/usr/local/openresty/nginx/sbin:
export PATH=$PATH:$NGINX_HOME
```

source .bash_profile

8、查看版本
```
nginx -v
如果出现nginx version: openresty/1.11.2.2，则安装成功
```