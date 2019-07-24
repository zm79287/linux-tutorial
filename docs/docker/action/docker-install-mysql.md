# Docker ??? MySQL

> ???????Centos

## ???????????

```docker
# docker search mysql
INDEX       NAME                                                             DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
docker.io   docker.io/mysql                                                  MySQL is a widely used, open-source relati...   5757      [OK]       
docker.io   docker.io/mariadb                                                MariaDB is a community-developed fork of M...   1863      [OK]       
docker.io   docker.io/mysql/mysql-server                                     Optimized MySQL Server Docker images. Crea...   397                  [OK]
...
```

## ?????????????

???íà???????????¡ã·Ú???????????????

```docker
docker pull mysql
```

## ??????

```docker
docker run -p 3306:3306 --name mysql -v /opt/docker_v/mysql/conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 -d mysql
```

## ???

* https://hub.docker.com/_/mysql/
