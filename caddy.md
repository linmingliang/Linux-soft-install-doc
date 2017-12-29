# caddy搭建
### 1. 裸机安装
>  ##### 1. 进入github中caddy官方仓库：  
>      https://github.com/mholt/caddy/releases    
>  ##### 2. 下载最新的包到服务器   
>  ##### 3. tar -xf 解压   
>  ##### 4. 同路径下防止caddy的配置文件启动即可    

### 2. docker安装   
>  ##### 1.进入docker hub中caddy的官方仓库：
       https://hub.docker.com/r/abiosoft/caddy/   
>  ##### 2.docker pull abiosoft/caddy:{version}
>  ##### 3.touch a config file(Caddyfile)
       justdogo.org {  # 启动 http 和 https，访问 http 会自动转跳到 https
         log access_log.log  # 日志
         gzip  # 使用gzip压缩
       }

 >        https://git.justdogo.org http://git.justdogo.org {
          gzip
          proxy / http://10.104.80.166:8001 {
            header_upstream Host {host}
            header_upstream X-Real-IP {remote}
            header_upstream X-Forwarded-For {remote}
            header_upstream X-Forwarded-Proto {scheme}
          }
        }

>        https://mvn.justdogo.org http://mvn.justdogo.org {
          gzip
          proxy / http://10.104.80.166:8002 {
            header_upstream Host {host}
            header_upstream X-Real-IP {remote}
            header_upstream X-Forwarded-For {remote}
            header_upstream X-Forwarded-Proto {scheme}
          }
        }

>        https://docker.justdogo.org http://docker.justdogo.org {
          gzip
          proxy / http://10.104.80.166:8003 {
            header_upstream Host {host}
            header_upstream X-Real-IP {remote}
            header_upstream X-Forwarded-For {remote}
            header_upstream X-Forwarded-Proto {scheme}
          }
        }

>  ##### 4.save certificates and run
      sudo docker run -d \
                      --name caddy \
                      -v $(pwd)/Caddyfile:/etc/Caddyfile \
                      -v $HOME/.soft/caddy/.caddy:/root/.caddy \
                      -v $(pwd)/srv:/srv \
                      -p 80:80 -p 443:443 \
                      abiosoft/caddy
