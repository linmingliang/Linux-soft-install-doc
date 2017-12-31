# harbor搭建(需要caddy转发)
###  裸机安装(https)
>  ##### 1. 进入github中harbor官方仓库：  
>      https://github.com/vmware/harbor/releases   
>  ##### 2. 下载最新的包到服务器   
>  ##### 3. tar -xf 解压   
>  ##### 4. 修改配置文件开启https(harbor.cfg)
       hostname = docker.justdogo.org
       ui_url_protocol = https
       customize_crt = on
       ssl_cert = /home/wangchen/.soft/caddy/.caddy/acme/acme-v01.api.letsencrypt.org/sites/docker.justdogo.org/docker.justdogo.org.crt   
       ssl_cert_key = /home/wangchen/.soft/caddy/.caddy/acme/acme-v01.api.letsencrypt.org/sites/docker.justdogo.org/docker.justdogo.org.key  
       secretkey_path = /home/wangchen/.soft/caddy/.caddy/acme/acme-v01.api.letsencrypt.org/sites/docker.justdogo.org  
       harbor_admin_password = 123456　　
>  ##### 5. 修改端口映射(docker-compose.yml)　　
```
　　　　proxy:
　　　　　　ports:
　　　　　　  - 8003:443
            - 4443:444
```
>  ##### 6. 启动harbor   
        sudo ./install 　　　
