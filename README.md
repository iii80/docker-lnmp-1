## start

`docker pull westeast/lnmp-ubuntu:latest`
docker.io: https://hub.docker.com/r/westeast/lnmp-ubuntu
github.com:https://github.com/westeast/docker-lnmp


## lnmp-ubuntu:latest

Version:
- lnmp 1.6 lnmp.org
- MySQL 5.5.62  dong@1988
- php 7.1.30
- nginx/1.16.1

Useage:
```
cd $HOME/data;
git clone https://github.com/westeast/docker-lnmp;

#运行容器
docker run -dit \
-p 8001:80 -p 443:443 -p 3306:3306 \
--privileged=true \
-v /Users/likenan/git:/code \
-v /tmp/lnmplogs:/home/wwwlogs \
-v $HOME/data/docker-lnmp/mysql/data:/usr/local/mysql/data \
-v $HOME/data/docker-lnmp/mysql/var:/usr/local/mysql/var \
-v $HOME/data/docker-lnmp/nginx_conf:/usr/local/nginx/conf \
--name=lnmp  westeast/lnmp-ubuntu:latest


#用name进入进入容器
docker exec -i -t lnmp /bin/bash
lnmp start 运行所有lnmp软件 
lnmp status 查看各软件 的运行状态
```


## lnmp-ubuntu:init 
ubuntu 16.04 
- 安装 了vim
- apt的源设置成国内清华的源

## lnmp-ubuntu:brpc
ubuntu 16.04
- baidu AnyQ 
- brpc 
- paddle  
- for learn c/c++ deep/machine learning
- protobuff3 gflag leveldb


## FAQ
1. 如果docker 进入bash后，`lnmp start`启动不了mysql  可执行下面的命令
```
/usr/local/mysql/bin/mysqld  --initialize   初始化下mysql
/usr/local/mysql/bin/mysqld --initialize --user=root
/usr/local/mysql/bin/mysqld --initialize --user=mysql  
#重启容器  docker stop lnmp / docker start lnmp`
#进入容器 docker exec -it lnmp /bin/bash   lnmp mysql start
如果 还不行就重启容器后再试下，目前没有发现mysql 在docker中偶现启动出错是哪里的问题。。。(如果不行可重复以上几步：使用lnmp mysql start 如果能正常启动之后就一切正常了)
```

2. mysql root  password:
```
dong@1988
```


