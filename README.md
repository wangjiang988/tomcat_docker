部署手册
------------

## 1. 安装docker-ce
参考网址: https://docs.docker.com/install/linux/docker-ce/centos/

1.1 如果有就版本，删除旧版本
    sudo yum remove docker \
                    docker-client \
                    docker-client-latest \
                    docker-common \
                    docker-latest \
                    docker-latest-logrotate \
                    docker-logrotate \
                    docker-selinux \
                    docker-engine-selinux \
                    docker-engine
1.2 安装依赖
    sudo yum install -y yum-utils \
        device-mapper-persistent-data \
        lvm2

1.3 添加源并安装
    sudo yum-config-manager \
        --add-repo \
        https://download.docker.com/linux/centos/docker-ce.repo

    sudo yum update
    sudo yum install docker-ce
    查看安装结果
    yum list docker-ce --showduplicates | sort -r
1.4 启动docker
    sudo systemctl start docker

## 2. 安装docker-compose
参考地址 https://docs.docker.com/compose/install/

两行命令
    sudo curl -L https://github.com/docker/compose/releases/download/1.19.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
 
查看
    docker-compose --version

## 3. 启动项目

1. 进入项目（路径下存在docker-compose.yml）

2. 将war包放入tomcat/webapps下

3. 启动
    docker-compose up -d 

4. 其他命令
    docker-compose stop 关闭项目   
    docker-compose restart 重启  
    docker-compose down 删除项目   
    docker-compose ps  查看项目   
    docker-compose exec tomcat(注：docker-compose.yml文件里边的servies名，这个项目是tomcat) bash

## 4. docker-compose 参数讲解
参考这个网址
https://www.cnblogs.com/freefei/p/5311294.html


## 5. jdbc连接mysql
application.yml 
jdbc 配置
改为： 
 
    url: jdbc:mysql://mysql:3306/service_platform?useUnicode=true&characterEncoding=utf-8&useSSL=true&autoReconnect=true&allowMultiQueries=true

 127.0.0.1 改为  docker-compose 文件里 tomcat配置的links项 第一个名字
