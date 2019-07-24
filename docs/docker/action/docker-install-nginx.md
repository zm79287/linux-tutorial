# Docker ??? Nginx

> ???????Centos

## ?????????

??? `docker search nginx` ????????????

```docker
# docker search nginx
INDEX       NAME                                                             DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
docker.io   docker.io/nginx                                                  Official build of Nginx.                        8272      [OK]       
docker.io   docker.io/jwilder/nginx-proxy                                    Automated Nginx reverse proxy for docker c...   1300                 [OK]
docker.io   docker.io/richarvey/nginx-php-fpm                                Container running Nginx + PHP-FPM capable ...   540                  [OK]
docker.io   docker.io/jrcs/letsencrypt-nginx-proxy-companion                 LetsEncrypt container to use with nginx as...   336                  [OK]
...
```

## ??????????

??? `docker pull nginx` ???????????

## ???зр???

```
docker run -p 80:80 --name mynginx -d nginx
```

