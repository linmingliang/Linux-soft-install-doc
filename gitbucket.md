# gitbucket搭建(需要caddy转发)
###  镜像安装
>  ##### 1. 下载gitbucket镜像　　　  
>      git pull f99aq8ove/gitbucket    
>  ##### 2. 运行githucket　　
>      docker run -d \
>                -p 8001:8080 \
>                -p 29418:29418  \ (ssh连接使用端口)
>                -v  ${PWD}/gitbucket-data:/gitbucket  \   
>                f99aq8ove/gitbucket
