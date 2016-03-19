Start a MySQL instance
====
# --name : assign 'midi-mysql' to the container
# -e : set environment variables
# -d : Run container in background and print container ID
$docker run --name midi-mysql -e MYSQL_ROOT_PASSWORD=midi -d mysql

Connect to MySQL from the MySQL command line client
========
$ docker run -it --link midi-mysql:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'


Container shell access and viewing MySQL logs
========
$ docker exec -it midi-mysql bash
$ docker logs midi-mysql

Docker tips: check container
======
$docker ps

Docker tips: check images
========
$docker images
