# Redis ��װ

<!-- TOC depthFrom:2 depthTo:3 -->

- [��װ](#��װ)
- [����](#����)
- [�ű�](#�ű�)

<!-- /TOC -->

## ��װ

��װ�������£�

��1�����ز���ѹ������

����������ص�ַ��https://redis.io/download ��ѡ����ʵİ汾���ء�

��ѡ����������ȶ��汾 4.0.8��http://download.redis.io/releases/redis-4.0.8.tar.gz

�Ҹ���ϲ������ڣ�`/opt/redis`

```
wget -O /opt/redis/redis-4.0.8.tar.gz http://download.redis.io/releases/redis-4.0.8.tar.gz
cd /opt/redis
tar zxvf redis-4.0.8.tar.gz
```

��2�����밲װ

ִ���������

```
cd /opt/redis/redis-4.0.8
make
```

## ����

**���� redis ����**

```
cd /opt/redis/redis-4.0.8/src
./redis-server
```

**���� redis �ͻ���**

```
cd /opt/redis/redis-4.0.8/src
./redis-cli
```

## �ű�

�������ְ�װ��ʽ���Ҷ�д�˽ű�ȥִ�У�

| [��װ�ű�](https://github.com/dunwu/linux-tutorial/tree/master/codes/linux/soft) |
