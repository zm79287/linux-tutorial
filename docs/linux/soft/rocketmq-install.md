# RocketMQ ��װ����

<!-- TOC depthFrom:2 depthTo:3 -->

- [����Ҫ��](#����Ҫ��)
- [���ؽ�ѹ](#���ؽ�ѹ)
- [���� Name Server](#����-name-server)
- [���� Broker](#����-broker)
- [�շ���Ϣ](#�շ���Ϣ)
- [�رշ�����](#�رշ�����)
- [FAQ](#faq)
    - [connect to <172.17.0.1:10909> failed](#connect-to-172170110909-failed)
- [�ο�����](#�ο�����)

<!-- /TOC -->

## ����Ҫ��

- �Ƽ� 64 λ����ϵͳ��Linux/Unix/Mac
- 64bit JDK 1.8+
- Maven 3.2.x
- Git

## ���ؽ�ѹ

����ٷ����ص�ַ��https://rocketmq.apache.org/dowloading/releases/��ѡ����ʰ汾

����ѡ�� binary �汾��

��ѹ�����أ�

```bash
> unzip rocketmq-all-4.2.0-source-release.zip
> cd rocketmq-all-4.2.0/
```

## ���� Name Server

```bash
> nohup sh bin/mqnamesrv &
> tail -f ~/logs/rocketmqlogs/namesrv.log
The Name Server boot success...
```

## ���� Broker

```bash
> nohup sh bin/mqbroker -n localhost:9876 -c conf/broker.conf &
> tail -f ~/logs/rocketmqlogs/broker.log
The broker[%s, 172.30.30.233:10911] boot success...
```

## �շ���Ϣ

ִ���շ���Ϣ����֮ǰ��������߿ͻ���������������λ�á��� RocketMQ ���ж��ַ�����ʵ�����Ŀ�ġ��������ʹ����򵥵ķ����������û������� `NAMESRV_ADDR` ��

```bash
> export NAMESRV_ADDR=localhost:9876
> sh bin/tools.sh org.apache.rocketmq.example.quickstart.Producer
SendResult [sendStatus=SEND_OK, msgId= ...

> sh bin/tools.sh org.apache.rocketmq.example.quickstart.Consumer
ConsumeMessageThread_%d Receive New Messages: [MessageExt...
```

## �رշ�����

```bash
> sh bin/mqshutdown broker
The mqbroker(36695) is running...
Send shutdown request to mqbroker(36695) OK

> sh bin/mqshutdown namesrv
The mqnamesrv(36664) is running...
Send shutdown request to mqnamesrv(36664) OK
```

## FAQ

### connect to <172.17.0.1:10909> failed

�����������߿ͻ������� RocketMQ ʱ����

```java
org.apache.rocketmq.remoting.exception.RemotingConnectException: connect to <172.17.0.1:10909> failed
    at org.apache.rocketmq.remoting.netty.NettyRemotingClient.invokeSync(NettyRemotingClient.java:357)
    at org.apache.rocketmq.client.impl.MQClientAPIImpl.sendMessageSync(MQClientAPIImpl.java:343)
    at org.apache.rocketmq.client.impl.MQClientAPIImpl.sendMessage(MQClientAPIImpl.java:327)
    at org.apache.rocketmq.client.impl.MQClientAPIImpl.sendMessage(MQClientAPIImpl.java:290)
    at org.apache.rocketmq.client.impl.producer.DefaultMQProducerImpl.sendKernelImpl(DefaultMQProducerImpl.java:688)
    at org.apache.rocketmq.client.impl.producer.DefaultMQProducerImpl.sendSelectImpl(DefaultMQProducerImpl.java:901)
    at org.apache.rocketmq.client.impl.producer.DefaultMQProducerImpl.send(DefaultMQProducerImpl.java:878)
    at org.apache.rocketmq.client.impl.producer.DefaultMQProducerImpl.send(DefaultMQProducerImpl.java:873)
    at org.apache.rocketmq.client.producer.DefaultMQProducer.send(DefaultMQProducer.java:369)
    at com.emrubik.uc.mdm.sync.utils.MdmInit.sendMessage(MdmInit.java:62)
    at com.emrubik.uc.mdm.sync.utils.MdmInit.main(MdmInit.java:2149)
```

ԭ��RocketMQ ������������ϣ����� ip Ϊ 10.10.30.63���������һ�� docker0 ������ip Ϊ 172.17.0.1��RocketMQ broker ����ʱĬ��ʹ���� docker0 �����������߿ͻ����޷����� 172.17.0.1������������⡣

�������

��1���ɵ� docker0 �������޸���������

��2��ͣ�� broker���޸� broker �����ļ������� broker��

�޸� conf/broker.conf������������ָ������ broker �� IP��

```
namesrvAddr = 10.10.30.63:9876
brokerIP1 = 10.10.30.63
```

����ʱ��Ҫָ�������ļ�

```bash
nohup sh bin/mqbroker -n localhost:9876 -c conf/broker.conf &
```

## ��������

- **����**
  - [����ϵͳ����ά�����ܽ�ϵ��](https://github.com/dunwu/OS)
- **����**
  - [RocketMQ �ٷ��ĵ�](http://rocketmq.apache.org/docs/quick-start/)
  - [RocketMQ ����ٿ�](http://laciagin.me/2017/12/07/RocketMQ%E6%90%AD%E5%BB%BA%E5%8F%8A%E5%88%A8%E5%9D%91/)
