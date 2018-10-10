commend
===


# rename
https://www.ewdna.com/2012/04/linux-scriptmv-rename.html
rename $1 $2 $3
$1: 要被取代的關鍵字
$2: 新的關鍵字
$3: 檔名符合這個規則的才取代

把 IMG001.jpg, IMG002.jpg… 換成 img001.jpg, img002.jpg… 
rename IMG img IMG*

把所有 .htm 檔案改成 .html
rename .htm .html *.htm


# CURL
``` =
while
do
curl -i -H "Accept: vdn.dac.v2" -H "Content-Type : application/json" http://192.168.111.201/api/io/di/45MR-1601@DI-00 --connect-timeout 15 --max-time 30
done
```

# Docker
docker ps
systemctl restart docker
docker exec -ti mantisbtdb /bin/bash

```bash=
#!/bin/bash
docker-compose stop
docker-compose rm./r
docker-compose up -d
```

```=
docker-compose stop
docker-compose rm -f
docker-compose up -d
```



docker exec -ti william_mysql_1 /bin/bash

# Git


# MySQL



mantis 因為MySQL版本太新，有密碼加密問題，導致其他人版本太舊，無法使用。
記得+ports，讓外部也可使用3306port。

mysql -uroot -proot

mysql -h 127.0.0.1 -P 3306 -u root -proot

mysql> show databases;
mysql> select host,user from mysql.user;

mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
https://hub.docker.com/r/vimagick/mantisbt/


mysql>ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root'; 
http://binary-space.iteye.com/blog/2412769


set password for 'root'@'%' = password('root'); 


