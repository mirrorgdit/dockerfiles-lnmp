# dockerfiles-lnmp

搭建lnmp环境

## 简介
用docker容器服务的方式搭建lnmp环境，易于维护、升级。使用前需了解Docker的基本概念，常用基本命令。
可以一条条命令执行docker命令来构建镜像，容器。这里推荐使用docker-compose来管理，执行项目，下面是使用流程。

相关软件版本：
- PHP 7.3.6
- MySQL 5.7 (root账号:root;密码5eNyjNf,成员账号:ystest;密码:ystest) [如何修改?](https://github.com/jianyan74/lnmp-dockerfiles/blob/master/docs/issue.md)
- Nginx 1.12
- Redis 4.0
- Mongo 3.6 (完全版)
- Elasticsearch latest (完全版)
- Rabbitmq latest (完全版)
- Memcached 1.5 (完全版)

用到的PHP扩展
- redis 4.0.0
- swoole latest
- memcached 3.0.4

> 注意:标注完全版的，通过切换full分支获得文件才能安装

