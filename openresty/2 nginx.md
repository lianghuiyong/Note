### server
### location
### 定向
### 重定向

## 区别
|       |    区别   |
| ------------ | ------------ |
|  Apache     |       |
|   Nginx    |       |
|   OpenResty    |       |

```
#user  nobody;
worker_processes  4;

#error_log  logs/error.log;
error_log  logs/error.log  debug;
#error_log  logs/error.log  info;

pid logs/nginx.pid;

events {
    use epoll;
    worker_connections  65535;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  logs/access.log  main;

    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    if_modified_since   off;
    ignore_invalid_headers  on;
    keepalive_disable   msie6;
    keepalive_requests  100;
    keepalive_timeout   75s;
    large_client_header_buffers 4   16k;
    limit_rate  0;
    lingering_time  30s;
    lingering_timeout   5s;

    client_header_buffer_size   2k;
    client_header_timeout   30s;
    client_body_buffer_size 16k;
    client_max_body_size    100m;
    client_body_in_file_only    off;
    client_body_in_single_buffer    on;
    client_body_timeout 60s;
    sendfile        on;
    #tcp_nopush     on;

    #gzip  on;
    map $http_upgrade $connection_upgrade {
        default upgrade;
        '' close;
    }

    upstream tomcat_api{
        server localhost:8085 weight=10;
    }

    upstream tomcat_api_test{
        server localhost:8085;
	#server localhost:8087 weight=10;
        #server localhost:8085 weight=10;
    }

    upstream tomcat_ms{
        server localhost:8086 weight=10;
    }

    upstream tomcat_web{
        server localhost:8078 weight=10;
    }

    upstream tomcat_harry{
        server localhost:8099 weight=10;
    }

    server{

        listen 80;
	charset utf-8;
        server_name sxzxtest.org;
        index index.jsp index.htm index.php index.html;
        root /usr/local/nginx/html;

        #fastcgi_connect_timeout 600;
        #fastcgi_send_timeout 600;
        #fastcgi_read_timeout 600;

        location ~ ^/api/.* {

		set $cur_ups '';

		#rewrite_by_lua '
                #	local request_method = ngx.var.request_method
                #	if request_method == "GET" then
                #        	local args = ngx.req.get_uri_args()
                #        	local a_client = args["client"]
                #        	local a_version = args["version"]
                #        	if (a_client == "ios") and (a_version == "2.6.1") then
                #                	ngx.var.cur_ups = "tomcat_api_test"
                #        	else
                #                	ngx.var.cur_ups = "tomcat_api_test"
                #        	end
                # 	elseif request_method == "POST" then
                #        	ngx.req.read_body()
                #        	local args = ngx.req.get_post_args()
                #        	local a_client = args["client"]
                #        	local a_version = args["version"]
                #        	if (a_client == "ios") and (a_version == "2.6.1") then
                #                	ngx.var.cur_ups = "tomcat_api_test"
                #        	else
                #                	ngx.var.cur_ups = "tomcat_api_test"
                #        	end
                # 	end
                #';

		#proxy_pass $scheme://$cur_ups;
           	proxy_pass http://tomcat_api_test;
		#proxy_pass http://tomcat_api;
		proxy_http_version 1.1;
            	proxy_set_header Upgrade $http_upgrade;
            	proxy_set_header Connection "upgrade";
        }

	location /ms {
		proxy_pass http://tomcat_ms;
        }

        location /ms_v2 {
		proxy_pass http://tomcat_web;
        }

	location /api_v2{
		proxy_pass http://tomcat_harry;
	}

        location ~ .*\.(gif|jpg|jpeg|png|bmp|swf|apk|tar.gz)$ {
              expires      30d;
        }

        location ~ .*\.(js|css)?$ {
              expires      12h;
        }
        #access_log  /chroot/wwwlogs/tomcat_schedule_web_test-access.log  access;
    }


}
```