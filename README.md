# lnmp-dockerfiles

搭建lnmp环境

## 简介
用docker容器服务的方式搭建lnmp环境，易于维护、升级。使用前需了解Docker的基本概念，常用基本命令。
可以一条条命令执行docker命令来构建镜像，容器。这里推荐使用docker-compose来管理，执行项目，下面是使用流程。

相关软件版本：
- PHP 7.2.19
- MySQL 5.7 (root账号:root;密码13NyjNf,成员账号:ystest;密码:ystest123) [如何修改?](https://github.com/mirrorgdit/dockerfiles-lnmp/blob/master/docs/issue.md)
- Nginx 1.12
- Redis 4.0
- Mongo 3.6 (拓展版)
- Elasticsearch latest (拓展版)
- Rabbitmq latest (拓展版)
- Memcached 1.5 (拓展版)

用到的PHP扩展
- redis 4.0.0
- swoole latest
- memcached 3.0.4

> 注意:标注拓展版的，通过切换extend分支获得文件才能安装

#### 目录

目录 | 说明
---|---
--- app | 应用安装目录
--- data | mongo、mysql数据库文件存储
--- docs | 帮助文档
--- logs | nginx、mongo、mysql、php日志
--- sercices | 服务软件配置包
--- --- memcached | memcached配置及安装文件
--- --- mongo | memcached配置及安装文件
--- --- mysql | mysql配置及安装文件
--- --- nginx | nginx配置及安装文件
--- --- php | php配置及安装文件
--- --- redis | redis配置及安装文件
--- --- docker-composer.yml | docker配置执行文件


## 使用
#### 1.安装Docker，Docker-compose  
- Docker，详见官方文档：https://docs.docker.com/engine/installation/linux/docker-ce/centos/
- docker-compose，文档：https://docs.docker.com/compose/install/
- 镜像加速，参考[docker使用国内镜像](https://github.com/yeasy/docker_practice/blob/master/install/mirror.md)
       不然下载镜像速度会卡的你怀疑人生
- 常见问题，必看。参考[这里](https://github.com/mirrorgdit/dockerfiles-lnmp/blob/master/docs/issue.md)

- 环境安装，看[这里](https://github.com/mirrorgdit/dockerfiles-lnmp/blob/master/docs/start-environment.md)



#### 2.下载dockerfiles-lnmp
直接clone：
```
git clone https://github.com/mirrorgdit/dockerfiles-lnmp.git
# 如果需要完整版再执行 git checkout extend
chmod -R 777 ./dockerfiles-lnmp/logs
cd dockerfiles-lnmp/services
```

#### 3.下载需要的拓展包
先下载好要使用的拓展包，如果编译出错要多次构建容器就可以省掉下载时间。
```
wget https://pecl.php.net/get/redis-4.0.0.tgz -O php/pkg/redis.tgz  
wget https://launchpad.net/libmemcached/1.0/1.0.18/+download/libmemcached-1.0.18.tar.gz -O php/pkg/libmemcached.tar.gz  
wget https://pecl.php.net/get/memcached-3.0.4.tgz -O php/pkg/memcached.tgz  
```

#### 4.docker-compose构建项目
进行docker-compose.yml所在文件夹：
执行命令：
```
docker-compose up
```  

如果没问题，下次启动时可以以守护模式启用，所有容器将后台运行：  
```
docker-compose up -d
``` 

使用 docker-compose 基本上就这么简单，Docker 就跑起来了，用 stop，start 关闭开启容器服务。  
更多的是在于编写 dockerfile 和 docker-compose.yml 文件。 

可以这样关闭容器并删除服务：
```
docker-compose down
```

#### 5. Demo站点搭建

进入app目录

```

cd ../app/demo 
此目录为demo站点目录

```

域名解析

找到 `services/nginx/conf.d` 下的 demo.website.cnf 里修改第三行server_name
```
server_name [为你自己的域名]; 
```
注意重启一下nginx容器才能生效

## 问题反馈

在使用中有任何问题，欢迎反馈给我，可以用以下联系方式跟我交流

邮箱： mirrorgdit@163.com

## 引用

[zPhal-dockerfiles](https://github.com/ZpGuo/zPhal-dockerfiles)

## 学习文档
[Docker 配置详解](https://www.jianshu.com/p/2217cfed29d7)

[Docker 入门教程](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)

[Docker 微服务教程](http://www.ruanyifeng.com/blog/2018/02/docker-wordpress-tutorial.html)

