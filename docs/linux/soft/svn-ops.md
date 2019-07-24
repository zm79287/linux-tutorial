# Svn ��ά

> Svn �� Subversion �ļ�ƣ���һ������Դ����İ汾����ϵͳ���������˷�֧����ϵͳ��
>
> ����Ŀ�����ڼ�¼ svn �İ�װ�����á�ʹ�á�

<!-- TOC depthFrom:2 depthTo:3 -->

- [1. ��װ����](#1-��װ����)
    - [1.1. ��װ svn](#11-��װ-svn)
    - [1.2. ���� svn �ֿ�](#12-����-svn-�ֿ�)
    - [1.3. ���� svnserve.conf](#13-����-svnserveconf)
    - [1.4. ���� passwd](#14-����-passwd)
    - [1.5. ���� authz](#15-����-authz)
    - [1.6. �����ر� svn](#16-�����ر�-svn)
    - [1.7. ���������� svn ����](#17-����������-svn-����)
    - [1.8. svn �ͻ��˷���](#18-svn-�ͻ��˷���)
- [2. �ο�����](#2-�ο�����)

<!-- /TOC -->

## 1. ��װ����

### 1.1. ��װ svn

```bash
$ yum install -y subversion
```

### 1.2. ���� svn �ֿ�

```bash
$ mkdir -p /share/svn
$ svnadmin create /share/svn
$ ls /share/svn
conf  db  format  hooks  locks  README.txt
```

�� conf Ŀ¼����������Ҫ�������ļ�

- authz - ��Ȩ�޿����ļ�
- passwd - ���ʺ������ļ�
- svnserve.conf - �� SVN ���������ļ�

### 1.3. ���� svnserve.conf

```bash
$ vim /share/svn/conf/svnserve.conf
```

������� 5 ��ע��

```ini
anon-access = read      #�����û��ɶ�
auth-access = write     #��Ȩ�û���д
password-db = passwd    #ʹ���ĸ��ļ���Ϊ�˺��ļ�
authz-db = authz        #ʹ���ĸ��ļ���ΪȨ���ļ�
realm = /share/svn      # ��֤�ռ������汾������Ŀ¼
```

### 1.4. ���� passwd

```bash
$ vim /share/svn/conf/passwd
```

����������£�

```ini
[users]
user1 = 123456
user2 = 123456
user3 = 123456
```

### 1.5. ���� authz

```bash
$ vim /share/svn/conf/authz
```

����������£�

```ini
[/]
user1 = rw
user2 = rw
user3 = rw
*=
```

### 1.6. �����ر� svn

```bash
$ svnserve -d -r /share/svn # ���� svn
$ killall svnserve # �ر� svn
```

### 1.7. ���������� svn ����

��װ�� svn �����Ĭ����û����ϵͳ�����Զ������ģ���һ��������Ҫ�� svn �����ȶ��������ṩ�������ԣ��б�Ҫ���ÿ��������� svn ����

#### Centos7 ��ǰ

�༭ `/etc/rc.d/rc.local` �ļ���

```bash
$ vi /etc/rc.d/rc.local
```

�����������ݣ�

```bash
# �����Զ����� svn��Ĭ�϶˿��� 3690
$ /usr/bin/svnserve -d -r /share/svn --listen-port 3690
```

ע�⣺

���������ն˲�����ʱ�򣬿���ֱ��ʹ�������������� SVN��`svnserve -d -r /share/svn`�������� `/etc/rc.d/rc.local` �ļ��б���д��������·����

�����֪�� svnserve ���װ���Ķ�������ʹ�� whereis svnserve ���ҡ�

#### Centos7

CentOS 7 �е� `/etc/rc.d/rc.local` ��û��ִ��Ȩ�޵ģ�ϵͳ���鴴�� `systemd service` ��������

�ҵ� svn �� service �����ļ� `/etc/sysconfig/svnserve` �༭�����ļ�

```bash
$ vi /etc/sysconfig/svnserve
```

�� `OPTIONS="-r /var/svn"` ��Ϊ svn �汾���ŵ�Ŀ¼��:wq �����˳���

ִ�� `systemctl enable svnserve.service`

������������ִ�� `ps -ef | grep svn` Ӧ�ÿ��Կ��� svn ����Ľ����Ѿ�������

### 1.8. svn �ͻ��˷���

���� [svn �ٷ����ص�ַ](https://tortoisesvn.net/downloads.html)��ѡ����ʵİ汾�����ز���װ��

�½�һ��Ŀ¼��Ȼ�������Ҽ��˵���ѡ�� **SVN Checkout**��

���µĴ��ڣ������ַ `svn://<��� IP>` ���ɣ��������������û���������������ӳɹ��ˣ�������û������������ passwd �����ļ����嵥�У���Ĭ�϶˿� 3690��������޸��˶˿ڣ���ôҪ�ǵü��϶˿ںš�����ͼ��ʾ��

<br><div align="center"><img src="https://raw.githubusercontent.com/dunwu/images/master/snap/20190129175443.png"/></div><br>

## 2. �ο�����

- https://www.cnblogs.com/liuxianan/p/linux_install_svn_server.html
- https://blog.csdn.net/testcs_dn/article/details/45395645
- https://www.cnblogs.com/moxiaoan/p/5683743.html
- https://blog.csdn.net/realghost/article/details/52396648
