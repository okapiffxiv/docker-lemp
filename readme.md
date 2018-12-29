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

# server stop
$ docker-compose stop web
```