---
title: Linux ???????
date: 2018-02-26
categories:
  - linux
tags:
  - linux
---

# Linux ???????

> ??????`rpm`, `yum`, `apt-get`

<!-- TOC depthFrom:2 depthTo:3 -->

- [rpm](#rpm)
- [yum](#yum)
    - [yum ?](#yum-?)
- [apt-get](#apt-get)
- [?��?????](#?��?????)

<!-- /TOC -->

## rpm

> rpm ?????? RPM ?????????????rpm ????? Red Hat Linux ???��???????????? Linux ????????????????????? GPL ????????????????????????????????????��????��?RPM ???????????????? Linux ??????????????????????? Linux ????????
>
> ?��???http://man.linuxde.net/rpm

?????

??1????? rpm ??

```
rpm -ivh xxx.rpm
```

??2?????.src.rpm ?????

?????????????????????? rpm ???????????????��???

```bash
rpm -i xxx.src.rpm
cd /usr/src/redhat/SPECS
rpmbuild -bp xxx.specs             #??????????????????specs???
cd /usr/src/redhat/BUILD/xxx/      #????????????????????
./configure                        #????????????????????????????????????
make
make install
```

??3??��?? rpm ?????

??????? `rpm -e ????`??????????????��??????????????????��??.rpm??????��??????? proftpd-1.2.8-1????????????��????

```bash
rpm -e proftpd-1.2.8-1
rpm -e proftpd-1.2.8
rpm -e proftpd-
rpm -e proftpd
```

???????????��????

```bash
rpm -e proftpd-1.2.8-1.i386.rpm
rpm -e proftpd-1.2.8-1.i386
rpm -e proftpd-1.2
rpm -e proftpd-1
```

?????????��?????????��

```
... is needed by ...
```

????????????????????????????????��????????? rpm -e --nodeps ???��??

??4?????? rpm ??????????????????

```bash
rpm -qa # ?��????��???????
```

## yum

> yum ???????? Fedora ?? RedHat ??? SUSE ?��??? rpm ??????????????????????????????????????????????????? RPM ????????????????????????????? RPM ???????????????????????????????????????????????????????????????????��???????????
>
> ?��???http://man.linuxde.net/yum

?????

?????????????????

- ????????????????`yum install yum-fastestmirror`
- ??? yum ??��???????`yum install yumex`
- ????????????????��?`yum grouplist`

**???**

```
yum install              #??????
yum install package1     #????????????package1
yum groupinsall group1   #?????????group1
```

**?????????**

```
yum update               #???????
yum update package1      #????????????package1
yum check-update         #???????????
yum upgrade package1     #????????????package1
yum groupupdate group1   #??????????group1
```

**????????**

```
yum info package1      #???????????package1
yum list               #??????????????????????????
yum list package1      #?????????????????package1
yum groupinfo group1   #?????????group1???yum search string ????????string????????
yum search <keyword>   #?????????
```

**???????**

```
yum remove <package_name>          #????????package_name
yum groupremove group1             #?????????group1
yum deplist package1               #??????package1???????
```

**???????**

```
yum clean packages       #?????????????????
yum clean headers        #???????????? headers
yum clean oldheaders     #????????????? headers
```

### yum ?

yum ??????????????????????????????????�I????????? yum ???

| ??? yum ?????              | ????                                                                                                                     |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| <http://mirrors.163.com/>    | Centos6??http://mirrors.aliyun.com/repo/Centos-6.repo<br>Centos7??http://mirrors.aliyun.com/repo/Centos-7.repo             |
| <http://mirrors.aliyun.com/> | Centos6??http://mirrors.163.com/.help/CentOS6-Base-163.repo<br>Centos7??http://mirrors.163.com/.help/CentOS7-Base-163.repo |

> ???Cento5 ????????????? http://vault.centos.org/ ?�I???????????????????????

?�I???????? aliyun CentOS7 ?????

```
cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
yum clean all
yum makecache
```

## apt-get

> apt-get ?????? Debian Linux ???��??��? APT ???????????????��??? Debian ????��?????????????????deb ??????????????????????????????? Windows ??????????
>
> ?��???http://man.linuxde.net/apt-get

?????

??? apt-get ??????????????????????????Debian ???????????????? Debian ???????????????????????????��???????????????????????apt-get ????????????????????????/etc/apt/sources.list ??????��????��????????????????????

deb [web ?? ftp ???][???��?????] [main/contrib/non-free]
???????? Ubuntu ??????????? Debian ????��???????? apt-get ??????????��?????????????????????

????? /etc/apt/sources.list ???? /etc/apt/preferences ??????��????��

```bash
# ???? apt-get
apt-get update

# ???????????
apt-get install packagename

# ��???????????????????????????????
apt-get remove packagename

# ��??????????????????????????????
apt-get ?Cpurge remove packagename

# ????????????????????????????????????????????
apt-get autoclean apt

# ????????????????????????????????????????????
apt-get clean

# ???????????????????
apt-get upgrade

# ???????????���
apt-get dist-upgrade
```

## ?��?????

- http://man.linuxde.net/rpm
- http://man.linuxde.net/yum
- http://man.linuxde.net/apt-get
- http://www.runoob.com/linux/linux-yum.html
