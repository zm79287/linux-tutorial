# Docker ???

???Repository??????��??????????

???????????????????????????Registry??????????????????????????????????????????????????��??????????????????��???????????????????????????????????????????????????????? dl.dockerpool.com/ubuntu ?????dl.dockerpool.com ???????????????ubuntu ????????

## Docker Hub

?? Docker ?????????????????? [Docker Hub](https://hub.docker.com/)??????????????????????? 15,000 ??????????????????? Docker Hub ??????????????????

### ???

??????? [https://cloud.docker.com](https://cloud.docker.com/) ????????? Docker ????

### ???

?????????? `docker login` ????????????????????????????????????��????? Docker Hub??

???????? `docker logout` ????????

### ???????

???????? `docker search` ????????????????��????????? `docker pull` ????????????????????

?????? `centos` ???????????????

```bash
$ docker search centos
NAME                                            DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
centos                                          The official build of CentOS.                   465       [OK]
tianon/centos                                   CentOS 5 and 6, created using rinse instea...   28
blalor/centos                                   Bare-bones base CentOS 6.5 image                6                    [OK]
saltstack/centos-6-minimal                                                                      6                    [OK]
tutum/centos-6.4                                DEPRECATED. Use tutum/centos:6.4 instead. ...   5                    [OK]
```

??????????????????????????????��???????????????????????????????????????????????????????????????????

???????????????????��??????????automated ????????????????????????????

????????????????????????????????

????????? `centos` ?????????????????????????????��?????????? Docker ?????????????????????????????????????????????????????

???????????????? `tianon/centos` ?????????? Docker ????????????????????????????????????????????? `username/` ???????????????????????? tianon ?????

???????????????? `--filter=stars=N` ???????????????????????? `N` ????????

?????? `centos` ????????

```bash
$ docker pull centos
Pulling repository centos
0b443ba03958: Download complete
539c0211cd76: Download complete
511136ea3c5a: Download complete
7064731afe90: Download complete
```

### ???????

????????????????? `docker push` ????????????????????? Docker Hub??

?????????��? `username` ???�I???? Docker ??????????

```bash
$ docker tag ubuntu:18.04 username/ubuntu:18.04

$ docker image ls

REPOSITORY                                               TAG                    IMAGE ID            CREATED             SIZE
ubuntu                                                   18.04                  275d79972a86        6 days ago          94.6MB
username/ubuntu                                          18.04                  275d79972a86        6 days ago          94.6MB

$ docker push username/ubuntu:18.04

$ docker search username

NAME                      DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
username/ubuntu
```

### ???????

?????????Automated Builds????????????????????????????????????????

????????????????????????????????????????���???????????????

??????????????????? Docker Hub ??????????????????????? [GitHub](https://github.com/) ?? [BitBucket](https://bitbucket.org/)???????????????????????????????????????tag????Docker Hub ?????????????????? Docker Hub ?��?

?????????????????????????�s

- ????????? Docker Hub?????????????
- ??????????????????? Docker Hub??
- ?? Docker Hub ?? [??????????????](https://registry.hub.docker.com/builds/add/)??
- ????????????��??????????? `Dockerfile`????????
- ??? `Dockerfile` ??��?????????????

???????? Docker Hub ?? [??????????](https://registry.hub.docker.com/builds/) ?��?????��?????????

