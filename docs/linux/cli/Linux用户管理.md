---
title: Linux ???????
date: 2018-02-27
categories:
  - linux
tags:
  - linux
  - command
---

# Linux ???????

> ??????`groupadd`, `groupdel`, `groupmod`, `useradd`, `userdel`, `usermod`, `passwd`, `su`, `sudo`

<!-- TOC depthFrom:2 depthTo:3 -->

- [Linux ??????????](#linux-??????????)
- [???????��?](#???????��?)
    - [groupadd](#groupadd)
    - [groupdel](#groupdel)
    - [groupmod](#groupmod)
    - [useradd](#useradd)
    - [userdel](#userdel)
    - [usermod](#usermod)
    - [passwd](#passwd)
    - [su](#su)
    - [sudo](#sudo)

<!-- /TOC -->

## Linux ??????????

- ????????? - ??? [groupadd](#groupadd)
- ???????? - ??? [groupdel](#groupdel)
- ??????????? - ??? [groupmod](#groupmod)
- ??????? - ??? [useradd](#useradd)
- ?????? - ??? [userdel](#userdel)
- ????????? - ??? [usermod](#usermod)
- ????????????? - ??? [passwd](#passwd)
- ?��???? - ??? [su](#su)
- ???????????????????��????????????????????????? - ??? [sudo](#sudo)

## ???????��?

### groupadd

> groupadd ?????????????????????�?????????????????????????��?
>
> ?��???http://man.linuxde.net/groupadd

?????

```bash
# ??????????�???????? ID ??????
$ groupadd -g 344 jsdigname
```

### groupdel

> groupdel ????????????????????�???????????????????? `/ect/group` ?? `/ect/gshadow`?????????????????��?????????????????��?????????????�
>
> ?��???http://man.linuxde.net/groupdel

?????

```bash
$ groupadd damon  # ????damon?????
$ groupdel damon  # ???????????
```

### groupmod

> groupmod ????????????????????????????????????????????????? groupmod ????????????????
>
> ?��???http://man.linuxde.net/groupmod

### useradd

> useradd ???????? Linux ?��???????????????useradd ?????????????????????????????? passwd ?څ?????????????? userdel ?????????? useradd ??????????????????????????? `/etc/passwd` ???????��?
>
> ?��???http://man.linuxde.net/useradd

?????

```bash
# ????????????
$ useradd ?Cg sales jack ?CG company,employees    # -g??????????�-G??????????

# ??????????????????????? ID
$ useradd caojh -u 544
```

### userdel

> userdel ????????????????????????????????????????????????????????????????????????????
>
> ?��???http://man.linuxde.net/userdel

?????

userdel ????????????????????��???? linuxde???? home ??��??`/var`???��??????????????????????

```bash
$ userdel linuxde       # ??????linuxde?????????????????????
$ userdel -r linuxde    # ??????linuxde???? home ???????????????
```

### usermod

> usermod ????????????????????????usermod ???????????????????????????????????? usermod ??????????? user id????????????? user ????????????�ʦ�???????????????????? crontab ???????????????????? at ???????????? NIS server ???? server ????????? NIS ?څ??
>
> ?��???http://man.linuxde.net/usermod

?????

```bash
# ?? newuser2 ?????? staff ??
$ usermod -G staff newuser2

# ??? newuser ???????? newuser1
$ usermod -l newuser1 newuser

# ??????? newuser1
$ usermod -L newuser1

# ????? newuser1 ??????
$ usermod -U newuser1
```

### passwd

> passwd ?????????????????????????????????????????????????????????????????????????????????��???????????????????????????????????????
>
> ?��???http://man.linuxde.net/passwd

?????

```bash
# ?????????????? passwd ???????????????
# ?????????????????????????????? passwd ????????????? root ????????????????
$ passwd linuxde    # ??????linuxde?????????
Changing password for user linuxde.
New UNIX password:          # ????????????
Retype new UNIX password:   # ????????��?
passwd: all authentication tokens updated successfully. # ?????

# ?????????????????????????????? passwd ????????�y???????????? linuxde??
$ passwd
Changing password for user linuxde. # ????linuxde?????????
(current) UNIX password:   # ???????????
New UNIX password:         # ????????????
Retype new UNIX password:  # ?????????
passwd: all authentication tokens updated successfully. # ????????

# ?????????????????????????????????`-l`???????????
$ passwd -l linuxde    # ???????linuxde???????????
Locking password for user linuxde.
passwd: Success           # ?????????

$ su linuxde   # ???su?��???linuxde?????
$ passwd      # linuxde??????????
Changing password for user linuxde.
Changing password for linuxde
(current) UNIX password:          # ????linuxde????????
passwd: Authentication token manipulation error     # ???????????????

$ passwd -d linuxde  # ???linuxde???????
Removing password for user linuxde.
passwd: Success                         # ????????

$ passwd -S linuxde    # ???linuxde???????????
Empty password.                         # ??????????????????
```

### su

> su ?????????��????????????????????????????????????????????????????
>
> ?��???http://man.linuxde.net/su

?????

```bash
# ??????? root ??????? ls ?????????????????
$ su -c ls root

# ??????? root ??????`-f`????????��? shell??
$ su root -f

# ??????? test ????�a?????? test ???????
$ su -test
```

### sudo

> sudo ?????????????????????????????????? root???? `/etc/sudoers` ???????????? sudo ?????????????��???????????????? sudo?????????????????????????????? sudo ?????????????????????? 5 ???????��??????????????????????????????
>
> ?��???http://man.linuxde.net/sudo

?????

```bash
# ?????????????
$ sudo -u userb ls -l
# ?��????????
$ sudo -l
# ???sudo????
$ sudo -L
```

#### ??????????? sudo

????????????? mary ???? sudo ????

1. `/etc/sudoers` ???????? sudo ??????????????????????��?????????????????��??`chmod u+w /etc/sudoers`
2. ??????????? `mary    ALL=(ALL)       ALL` ?????�g??????? mary ???? sudo ?????????
3. ??? `/etc/sudoers` ????????????????`chmod u-w /etc/sudoers`

#### ????????? sudo

???????????? sudo ??????????????? 2 ????`mary    ALL=(ALL)       NOPASSWD: ALL`??
