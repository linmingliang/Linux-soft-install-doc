# jdk安装
### 1. 官网下载
### 2. 配置环境变量  
>  1. sudo vi /etc/profile 或者 sudo vi ~/.profile


>  2. export JAVA_HOME=$HOME/jdk1.7.0_21     
      export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib:$CLASSPATH  
      export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH  


>  3. source /etc/profile
   
