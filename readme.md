- CentOS7
- Nginx
- MariaDB
- PHP7
- composer
- node

```console
$ docker pull centos:7
$ docker pull centos/mariadb
$ docker-compose up -d

# server start
$ docker-compose start web

# bash
$ docker-compose exec web bash

# 外部から接続する場合
# mysql -u root
# GRANT ALL PRIVILEGES ON *.* TO root@gateway WITH GRANT OPTION;

# server stop
$ docker-compose stop web
```