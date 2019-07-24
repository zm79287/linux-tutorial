# ZooKeeper ��װ����

> ����Ҫ��JDK6+

<!-- TOC depthFrom:2 depthTo:3 -->

- [���ؽ�ѹ ZooKeeper](#���ؽ�ѹ-zookeeper)
- [���������ļ�](#���������ļ�)
- [���� ZooKeeper ������](#����-zookeeper-������)
- [���� CLI](#����-cli)
- [ֹͣ ZooKeeper ������](#ֹͣ-zookeeper-������)

<!-- /TOC -->

�ڰ�װ ZooKeeper ֮ǰ����ȷ�����ϵͳ����������һ����ϵͳ�����У�

- **���� Linux OS** - ֧�ֿ����Ͳ����ʺ���ʾӦ�ó���
- **Windows OS** - ��֧�ֿ�����
- **Mac OS** - ��֧�ֿ�����

��װ�������£�

## ���ؽ�ѹ ZooKeeper

����ٷ����ص�ַ��http://zookeeper.apache.org/releases.html#download ��ѡ����ʰ汾��

��ѹ�����أ�

```
$ tar -zxf zookeeper-3.4.6.tar.gz
$ cd zookeeper-3.4.6
```

## ���������ļ�

����봴�� `conf/zoo.cfg` �ļ�����������ʱ����ʾ��û�д��ļ���

���γ��ԣ�����ֱ��ʹ�� Kafka �ṩ��ģ�������ļ� `conf/zoo_sample.cfg`��

```
$ cp conf/zoo_sample.cfg conf/zoo.cfg
```

## ���� ZooKeeper ������

ִ����������

```
$ bin/zkServer.sh start
```

ִ�д�������㽫�յ�������Ӧ

```
$ JMX enabled by default
$ Using config: /Users/../zookeeper-3.4.6/bin/../conf/zoo.cfg
$ Starting zookeeper ... STARTED
```

## ���� CLI

������������

```
$ bin/zkCli.sh
```

������������󣬽����ӵ� ZooKeeper ����������Ӧ�õõ�������Ӧ��

```
Connecting to localhost:2181
................
................
................
Welcome to ZooKeeper!
................
................
WATCHER::
WatchedEvent state:SyncConnected type: None path:null
[zk: localhost:2181(CONNECTED) 0]
```

## ֹͣ ZooKeeper ������

���ӷ�������ִ�����в����󣬿���ʹ����������ֹͣ zookeeper ��������

```
$ bin/zkServer.sh stop
```

> ���ڰ�װ���ݲο���[Zookeeper ��װ](https://www.w3cschool.cn/zookeeper/zookeeper_installation.html)

## ��������

- **����**
  - [����ϵͳ����ά�����ܽ�ϵ��](https://github.com/dunwu/OS)
