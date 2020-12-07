# dnmp

#### 介绍
php7.3 + nginx + mysql + redis + elasticsearch + kibana + rabbitmq + mongo + mongo-express + portainer 一键集成环境


#### 软件架构
DNMP（Docker + Nginx + MySQL + PHP7 + Redis）是一款全功能的LNMP一键安装程序。


#### 安装教程

1. 本地安装`git`、`docker`和`docker-compose`。
2. `clone`项目：
    ```
    国内地址：
    git clone https://gitee.com/qiuapeng921/dnmp.git
    全网地址：
    git clone https://github.com/qiuapeng921/dnmp.git
    ```
3. 如果不是`root`用户，还需将当前用户加入`docker`用户组：
    ```
    curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyu
	sudo groupadd docker
	sudo usermod -aG docker ${USER}
	sudo systemctl restart docker
	newgrp - docker
    ```
4. 拷贝环境配置文件`.env.example`为`.env`，启动：
    ```
    cd dnmp
    cp .env.example .env   # Windows系统请用copy命令，或者用编辑器打开后另存为.env
    docker-compose up

#### 使用说明


1. 添加快捷命令
    在开发的时候，我们可能经常使用`docker exec -it`切换到容器中，把常用的做成命令别名是个省事的方法。
    打开~/.bashrc，加上：
    ```bash
    alias dnginx='docker exec -it dnmp_nginx_1 /bin/sh'
    alias dphp73='docker exec -it dnmp_php-swoole_1 /bin/sh'
    alias dmysql='docker exec -it dnmp_mysql_1 /bin/bash'
    alias dredis='docker exec -it dnmp_redis_1 /bin/sh'
    alias drabbit='docker exec -it dnmp_rabbit_1 /bin/bash'
    alias dmongo='docker exec -it dnmp_mongo_1 /bin/bash'
    ```