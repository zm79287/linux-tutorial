---
title: Linux ??????????
date: 2019-03-06
---

# Linux ??????????

> :bulb: ?????????????????????????????? Centos ???�ѷ�??

## ???????

### ???????????????

??1???? hosts ??????????? IP ?????????????????

```bash
echo "192.168.0.1 hostname" >> /etc/hosts
```

????????????????????? `hostname` ???????????????????????? IP????? `ifconfig` ??????

??2???????????? DNS ??????

??? `vi /etc/resolv.conf` ??????????????

```bash
nameserver 114.114.114.114
nameserver 8.8.8.8
```

> 114.114.114.114 ????????? DNS
>
> 8.8.8.8 ?? Google DNS
>
> :point_right: ?��???[???? DNS ????](https://www.zhihu.com/question/32229915)

??3???????????? ping ? www.baidu.com

### ?????????????

firewalld ????????

```bash
??????systemctl start firewalld
????systemctl stop firewalld
??????systemctl status firewalld
?????????systemctl disable firewalld
?????????systemctl enable firewalld
```

systemctl ?? CentOS7 ???????????????????????????? service ?? chkconfig ?????????�^

```
???????????systemctl start firewalld.service
??????????systemctl stop firewalld.service
???????????systemctl restart firewalld.service
???????????????systemctl status firewalld.service
?????????????????systemctl enable firewalld.service
?????????????????systemctl disable firewalld.service
????????????????systemctl is-enabled firewalld.service
??????????????��?systemctl list-unit-files|grep enabled
??????????????��?systemctl --failed
```

???? firewalld-cmd

```
???��??firewall-cmd --version
????????firewall-cmd --help
???????firewall-cmd --state
?????��?????firewall-cmd --zone=public --list-ports
???��????????firewall-cmd --reload
?????????:  firewall-cmd --get-active-zones
????????????????firewall-cmd --get-zone-of-interface=eth0
??????��???firewall-cmd --panic-on
??????????firewall-cmd --panic-off
?????????firewall-cmd --query-panic
```

????????????

```
????firewall-cmd --zone=public --add-port=80/tcp --permanent    ??--permanent??????��????��???????????��??
????????firewall-cmd --reload
????firewall-cmd --zone= public --query-port=80/tcp
?????firewall-cmd --zone= public --remove-port=80/tcp --permanent
```

> :point_right: ?��???[CentOS7 ??? firewalld ????????????](https://www.cnblogs.com/moxiaoan/p/5683743.html)

## ?????

### ??? NTP ??????????

??1???????????????? ntp

```
yum -y install ntp
```

ntp ?????????��????? `/etc/ntp.conf`

??2?????? NTP ????

```bash
systemctl start ntpd.service
```

??3?????????? 123 ???

NTP ????????? 123,?????? udp ��?�???? NTP ????????????????????? udp 123 ???????

```
/sbin/iptables -A INPUT -p UDP -i eth0 -s 192.168.0.0/24 --dport 123 -j ACCEPT
```

??4???????????

```
/usr/sbin/ntpdate ntp.sjtu.edu.cn
```

ntp.sjtu.edu.cn ??????????? ntp ????????

??5??????????????

??????????????????????ْ 3 ??????????

```
echo "* 3 * * * /usr/sbin/ntpdate ntp.sjtu.edu.cn" >> /etc/crontab
systemctl restart crond.service
```

> :point_right: ?��???https://www.cnblogs.com/quchunhui/p/7658853.html

## ????????

### Linux ?????????????

??1???? `/etc/rc.local` ????????????

??????????????????????????????? `/etc/rc.local` ????????????????

1. ???????????????????�Y??????????????????????;
2. ???? `/etc/rc.local` ???��???????????��?????????????;
v
????

??? `vim /etc/rc.local` ?????????????????

```bash
#!/bin/sh
#
# This script will be executed *after* all the other init scripts.
# You can put your own initialization stuff in here if you don't
# want to do the full Sys V style init stuff.

touch /var/lock/subsys/local
/opt/pjt_test/test.pl
```

??2???? `/etc/rc.d/init.d` ????????????????

Linux ?? `/etc/rc.d/init.d` ???��??????????????????????????????????????�� shell ??????????��??????????

Linux ????????????????? `/etc/rc.d/init.d` ????????????????????????????��???????????????��??????????????????????????????

??3?????��???????

?????????��????????????????????��???????

```
????????��?????????:
# 0 - ???????????initdefault ?????0 ??
# 1 - ???????       ??????????#init s = init 1
# 2 - ?????????? NFS
# 3 - ??????????(????????��?)
# 4 - ??????
# 5 - X11 ????????????xwindow)
# 6 - ???????? ????????initdefault ?????6 ??
```

??��?????? `/etc/inittab` ?????????????????? init ???????????????????????��?????????/etc/rc.d ??????????

?? `/etc` ???????????????????????rcS.d rc0.d rc1.d ... rc6.d (0??1... 6 ???????????? 0 ????????1 ???????????2-5 ????????????6 ????????) ?????????????? redhat ??? rc.d ????????????? rcS.d????????????????????????????????: S88mysql

???????????????????????????????��????????:

??1??????? mysql ??? /etc/init.d ????

??2???????????????????

```bash
$ runlevel
N 3
```

??3???څ????????

```
#  98 ????????
#  2 ?????????��??????????????????????��????
$ update-rc.d mysql start 98 2 .
```

????????? /etc/rc2.d ??????????? S98mysql ??????????????

??4??????????????????????��??

??5?????????????

???????????????????????????????????

1. ???? `/etc/rc2.d` ???????????????????????????????

2. ?????????`update-rc.d -f s10 remove`
3. ??? update-rc.d ?????????????????????? rcconf ?????????????

> :point_right: ?��???
>
> - https://blog.csdn.net/linuxshine/article/details/50717272
> - https://www.cnblogs.com/ssooking/p/6094740.html

### ?????��??

??1????? crontab

??2?????? crontab ????

??????????? crond ????`chkconfig crond on`

????????????????????????

```bash
# ????????
systemctl start crond.service
# ??????
systemctl stop crond.service
# ????????
systemctl restart crond.service
# ????????????
systemctl reload crond.service
# ????
systemctl status crond.service
```

??3???????????��???

???????????

- ????????????`crontab -e` ???????????????????????
- ???? `/etc/crontab` ??????? `vi /etc/crontab`??????????????

?????

```bash
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed

# ???????3????????
* 3 * * * /usr/sbin/ntpdate ntp.sjtu.edu.cn

# ?????��???root?????? /home/hello.sh ???
0 */2 * * * root /home/hello.sh
```

> :point_right: ?��???[linux ?????��??](https://blog.csdn.net/z_yong_cool/article/details/79288397)

## ????

### ???? Linux ??????

1. ???(??��???? initdefault ????? 0???????????? Linux ????????)
2. ????????????? Win9X ???????
3. ?????????????? NFS
4. ???????????????????��?
5. ???????????��?????????????????????��????
6. X11???????? X-Window ??
7. ???????? (??��???? initdefault ????? 6???????????? Linux ?????????????)

???��?????

```bash
$ sed -i 's/id:5:initdefault:/id:3:initdefault:/' /etc/inittab
```

## ?��?????

- [CentOS7 ??? firewalld ????????????](https://www.cnblogs.com/moxiaoan/p/5683743.html)

- [linux ?????��??](https://blog.csdn.net/z_yong_cool/article/details/79288397)
