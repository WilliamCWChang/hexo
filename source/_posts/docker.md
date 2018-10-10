---
title: docker
date: 2018-09-22 11:01:25
categories:
    - test
tags:
    - docker
---


# https://my.oschina.net/bysu/blog/1805153
```
#拉取archlinux镜像
sudo docker pull base/archlinux

#查看目前有几个容器，多少个暂停，多少个停止，多少个正在运行
[bysu@subaoya ~]$ sudo docker info

docker ps  #查看正在运行的容器

docker ps -a   #查看所有状态的容器

#查看所有容器的名字
sudo docker ps -a -q

#删除不在运行的所有容器
sudo docker rm $(sudo docker ps -a -q)
docker rm $(docker ps -a -q)

#停止一个正在运行的容器
sudo docker stop a56a719eb52a


实时查看日志可以使用下列命令。
sudo docker logs -f my_daemon
#实时查看最新日志
sudo docker logs --tail 0 -f my_daemon
#实时查看最新日志，加上-t标志为每条日志项加上时间戳，方便调试
sudo docker logs --tail 0 -ft my_daemon

容器中运行后台任务
sudo docker exec -d my_first_container touch /etc/createFile
容器中运行交互命令
sudo docker exec -t -i my_first_container /bin/bash


docker run -it base/archlinux
docker run --name my_first_container -i -t base/archlinux /bin/bash
```



https://github.com/xlrl/docker-mantisbt
https://github.com/meedan/MantisBT
https://github.com/mantisbt/mantisbt/blob/master/config/config_inc.php.sample
https://github.com/Mikroways/mantisbt