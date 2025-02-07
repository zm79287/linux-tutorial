---
title: Elastic ?????? Logstash ????
date: 2017-12-26
categories:
- javatool
tags:
- java
- javatool
- log
- elastic
---

# Elastic ?????? Logstash ????

> ?????? Elastic ???????ELK???? Logstash ??��?
>
> ???????? Elastic ?????????��????????��???[Elastic ??????????????](https://github.com/dunwu/JavaStack/blob/master/docs/javatool/elastic/elastic-quickstart.md)

## ???

Logstash ?????????????????????????????????

### ????

Logstash ?? Elasticsearch  ?????????????

Logstash ??????????????????????????????????????��???????��?????��????Logstash ?????��??? 200 ????��????

### ???????

Logstash ?????????????`input` ?? `output` ????????????`filter`??

???????????????? Logstash ??????????????��????? > ?????? > ?????

<br><div align="center"><img src="https://www.elastic.co/guide/en/logstash/current/static/images/basic_logstash_pipeline.png"/></div><br>

- input ??????????????????
- filter ??????????????????????????
- output ??????????????

???????��????��???????????????????????????Logstash ??????????????��???????????????????????????????????????????????????????��?

???��??????????????????

## ????

### ???????

- **`logstash.yml`**??logstash ????????????????
- **`jvm.options`**??logstash ?? JVM ?????????
- **`startup.options`** (Linux)???????????????? `/usr/share/logstash/bin` ????????????????????????????????????? Logstash ????????????????????????????????��?????? `startup.options` ???????????????????????�????????????????????��


### logstash.yml ??????

?????????????????????��???https://www.elastic.co/guide/en/logstash/current/logstash-settings-file.html

| ????                         | ????                                       | ????                                      |
| -------------------------- | ---------------------------------------- | ---------------------------------------- |
| `node.name`                | ?????                                      | ????????????                                   |
| `path.data`                | Logstash???????????�ʦ�?????????????                | `LOGSTASH_HOME/data`                     |
| `pipeline.workers`         | ????��????????????????��??????????????????????????????????CPU��????????????????????????????????????????? | Number of the host??s CPU cores           |
| `pipeline.batch.size`      | ??????��????????????????????????????????????????????????????????????��??????��???????????????????�D???????????????????????? `LS_HEAP_SIZE` ????????��?????????????JVM???��?? | `125`                                    |
| `pipeline.batch.delay`     | ?????????????????????????????��?????��?????????????????????????????????????????? | `5`                                      |
| `pipeline.unsafe_shutdown` | ????????true?????????????????inflight????????????Logstash?????????????????????Logstash????????????????��?????????????????????????????????????????????????? | `false`                                  |
| `path.config`              | ???????Logstash????��??????????????????????????????????????????????��???? | Platform-specific. See [[dir-layout\]](https://github.com/elastic/logstash/blob/6.1/docs/static/settings-file.asciidoc#dir-layout). |
| `config.string`            | ??????????????????????????????????????????????????           | None                                     |
| `config.test_and_exit`     | ?????true???????????????��??????????????????????��?????grok?????????? Logstash????????��???????????????????????????log.level??debug?????????Logstash???????????????????????????????????� | `false`                                  |
| `config.reload.automatic`  | ?????true????????????????????????????????????????????��???????????SIGHUP???????????? | `false`                                  |
| `config.reload.interval`   | Logstash ??????????????????????                  | `3s`                                     |
| `config.debug`             | ?????true?????????????????????????????????????????????`log.level??debug`?????��?????????????�ʦ�?????????????????????????????????????????????????????????? | `false`                                  |
| `config.support_escapes`   | ???????true?????????????????????????????                | `false`                                  |
| `modules`                  | ???????????????????????????YAML???��?                | None                                     |
| `http.host`                | ????                                     | `"127.0.0.1"`                            |
| `http.port`                | ????                                     | `9600`                                   |
| `log.level`                | ?????????��???fatal > error > warn > info > debug > trace | `info`                                   |
| `log.format`               | ????????json ??JSON ??????? plain ???????         | `plain`                                  |
| `path.logs`                | Logstash ?????????����??                       | `LOGSTASH_HOME/logs`                     |
| `path.plugins`             | ???????????????????????????????????????????????��????         |                                          |

## ????

### ??????

????????????? logstash ?????????

```
bin/logstash [options]
```

???? [options] ?????????????????? Logstash ??��??????��????

????????????????�ʦ�???????? Logstash ?????????`logstash.yml`???��????????????????????????????

> **?**
>
> ??????????????????��??????????????? logstash ?????��?????????????????��??
>
> ????????????????????????????? logstash ???��??????????????
>
> ```
> bin/logstash -f logstash.conf
> ```
> ????????????????��?????????��???https://www.elastic.co/guide/en/logstash/current/running-logstash-command-line.html
>

### ???????

?????????????logstash ??????? `bin/logstash -f logstash.conf` ??????????????��?????????????????????`logstash.yml`???��????��?

????????????????????????????????��?????

#### ?????????

????????????��????????????? Logstash ???????????????? input ??filter??output???? logstash ??????????????????????

```
input {}

filter {}

output {}
```

> ??????????????????????????????��?????????????????????????????????????��???????????????

#### ???????

????????????????????????????????��?

?????????????????????????????????

```
input {
  file {
    path => "/var/log/messages"
    type => "syslog"
  }

  file {
    path => "/var/log/apache/access.log"
    type => "apache"
  }
}
```

???????????????????????????????��??? [Input Plugins](https://www.elastic.co/guide/en/logstash/current/input-plugins.html), [Output Plugins](https://www.elastic.co/guide/en/logstash/current/output-plugins.html), [Filter Plugins](https://www.elastic.co/guide/en/logstash/current/filter-plugins.html), ?? [Codec Plugins](https://www.elastic.co/guide/en/logstash/current/codec-plugins.html) ??

#### ?????

?????????????????????????????????????��??????��??????????????????????

- Array

```
  users => [ {id => 1, name => bob}, {id => 2, name => jane} ]
```

- Lists

```
  path => [ "/var/log/messages", "/var/log/*.log" ]
  uris => [ "http://elastic.co", "http://example.net" ]
```

- Boolean

```
  ssl_enable => true
```

- Bytes

```
  my_bytes => "1113"   # 1113 bytes
  my_bytes => "10MiB"  # 10485760 bytes
  my_bytes => "100kib" # 102400 bytes
  my_bytes => "180 mb" # 180000000 bytes
```

- Codec

```
  codec => "json"
```

- Hash

```
match => {
  "field1" => "value1"
  "field2" => "value2"
  ...
}
```

- Number

```
  port => 33
```

- Password

```
  my_password => "password"
```

- URI

```
  my_uri => "http://foo:bar@example.net"
```

- Path

```
  my_path => "/tmp/logstash"
```

- String


- ??????

## ???

### input

> Logstash ????????????? ?????????????????????????????????????????????????????????????????????Web ??��?????��??????? AWS ???????????

#### ???? input ???

- **file**????????????????????????UNIX???? `tail -0F` ???
- **syslog??**?????????????514??????????????????????RFC3164??????��???
- **redis??**??redis??????????????redis?????redis?��? Redis?????????????Logstash????��???????????????????Logstash???????????Logstash???????
- **beats??**??????Filebeat??????????

?????????????[Input Plugins](https://www.elastic.co/guide/en/logstash/current/input-plugins.html)

### filter

> ????????Logstash????��??��????��?????????????????????????????????????????????????��?????

#### ???? filter ???

- **grok??**???????????????? Grok????Logstash?��????????????????????????????????????
- **mutate??**???????????????????????????????????????�I?????????��???��?

- **drop??**???????????????????????????

- **clone??**???????????????????????????????��?

- **geoip??**????��?IP????????��???????????????Kibana???????????????


?????????????[Filter Plugins](https://www.elastic.co/guide/en/logstash/current/filter-plugins.html)

### output

> ?????Logstash?????????��????????????????????????????????????????????????????????��?

#### ???? output ???

- **elasticsearch??**????????????? Elasticsearch???????????
- **file??**?????????��???????????
- **graphite??**????????????? graphite????????��?????????��???????? http://graphite.readthedocs.io/en/latest/????
- **statsd??**????????????? statsd ??????????????????????????????????????????UDP?????????????????????????????????

?????????????[Output Plugins](https://www.elastic.co/guide/en/logstash/current/output-plugins.html)

### codec

??????????????????

#### ???? codec ???

- **json??**??JSON???????????��???????
- **multiline??**????????????????java????????????????????????????

???????????[Codec Plugins](https://www.elastic.co/guide/en/logstash/current/codec-plugins.html)

## ??

???????????? Logstash ???????????????????????????????��????????��?????

### ????????????

> stdin input ?????????????????????????? input ????????????????????
>

**???**

??1?????? `logstash-input-stdin.conf` ??

```
input { stdin { } }
output {
  elasticsearch { hosts => ["localhost:9200"] }
  stdout { codec => rubydebug }
}
```

?????????????��???https://www.elastic.co/guide/en/logstash/current/plugins-inputs-stdin.html

??2????? logstash????? `-f` ?????????????????

```
bin/logstash -f logstash-input-stdin.conf
```

### ???? logback ???

> elk ??????? Java ????????? log4j2 ????????? logback ?? log4j??
>
> ????? logback + logstash ????????? [logstash-logback-encoder](https://github.com/logstash/logstash-logback-encoder) ??[logstash-logback-encoder](https://github.com/logstash/logstash-logback-encoder) ???? UDP / TCP / ??????????????????? logstash??
>
> ??????????? log4j ??????????????????????????????? jar ?????��??????? log4j ??logback ????????? jar ????????????��????????????[?? Java ????????????](https://github.com/dunwu/JavaStack/blob/master/docs/javalib/java-log.md) ??

#### TCP ???

1. logstash ????

   ??1?????? `logstash-input-tcp.conf` ??

```
input {
tcp {
  port => 9251
  codec => json_lines
  mode => server
}
}
output {
 elasticsearch { hosts => ["localhost:9200"] }
 stdout { codec => rubydebug }
}
```

   ?????????????��???https://www.elastic.co/guide/en/logstash/current/plugins-inputs-tcp.html

   ??2????? logstash????? `-f` ?????????????????`bin/logstash -f logstash-input-udp.conf`


2. java ???????

   ??1???? Java ???? pom.xml ?????? jar ????

```xml
<dependency>
 <groupId>net.logstash.logback</groupId>
 <artifactId>logstash-logback-encoder</artifactId>
 <version>4.11</version>
</dependency>

<!-- logback ?????? -->
<dependency>
 <groupId>ch.qos.logback</groupId>
 <artifactId>logback-core</artifactId>
 <version>1.2.3</version>
</dependency>
<dependency>
 <groupId>ch.qos.logback</groupId>
 <artifactId>logback-classic</artifactId>
 <version>1.2.3</version>
</dependency>
<dependency>
 <groupId>ch.qos.logback</groupId>
 <artifactId>logback-access</artifactId>
 <version>1.2.3</version>
</dependency>
```

   ??2????????? logback.xml ????? appender

```xml
<appender name="ELK-TCP" class="net.logstash.logback.appender.LogstashTcpSocketAppender">
 <!--
 destination ?? logstash ????? host:port??
 ????? logstash ???????????????????????? logstash
 -->
 <destination>192.168.28.32:9251</destination>
 <encoder charset="UTF-8" class="net.logstash.logback.encoder.LogstashEncoder"/>
</appender>
<logger name="io.github.dunwu.spring" level="TRACE" additivity="false">
 <appender-ref ref="ELK-TCP" />
</logger>
```

   ??3?????????????? logback ???????? ?????????????????��???????????????[?? Java ????????????](https://github.com/dunwu/JavaStack/blob/master/docs/javalib/java-log.md) ??

   **?????**[???logback.xml](https://github.com/dunwu/JavaStack/blob/master/codes/javatool/src/main/resources/logback.xml)

#### UDP ???

UDP ?? TCP ????��?????��??

1. logstash ????

   ??1?????? `logstash-input-udp.conf` ??

```
input {
udp {
  port => 9250
  codec => json
}
}
output {
 elasticsearch { hosts => ["localhost:9200"] }
 stdout { codec => rubydebug }
}
```

   ?????????????��???https://www.elastic.co/guide/en/logstash/current/plugins-inputs-udp.html

   ??2????? logstash????? `-f` ?????????????????`bin/logstash -f logstash-input-udp.conf`


2. java ???????

   ??1???? Java ???? pom.xml ?????? jar ????

   ?? **TCP ???** ????��???????????????????

   ??2????????? logback.xml ????? appender

 ```xml
 <appender name="ELK-UDP" class="net.logstash.logback.appender.LogstashSocketAppender">
   <host>192.168.28.32</host>
   <port>9250</port>
 </appender>
 <logger name="io.github.dunwu.spring" level="TRACE" additivity="false">
   <appender-ref ref="ELK-UDP" />
 </logger>
 ```

   ??3?????????????? logback ???????? ?????????????????��???????????????[?? Java ????????????](https://github.com/dunwu/JavaStack/blob/master/docs/javalib/java-log.md) ??

   **?????**[???logback.xml](https://github.com/dunwu/JavaStack/blob/master/codes/javatool/src/main/resources/logback.xml)

### ???????

> ?? Java Web ???????????��????????????? Tomcat ??Nginx ??Mysql ?????��?????????????????????????????????��?????????????????????????????? logback ????????????????? logstash??
>
> ??��????��???????????????????? logstash ?? file input ?????
>
> ??????????????????????????????????????????????? logstash ??

**???**

logstash ????

??1?????? `logstash-input-file.conf` ??

```
input {
	file {
		path => ["/var/log/nginx/access.log"]
		type => "nginx-access-log"
		start_position => "beginning"
	}
}

output {
	if [type] == "nginx-access-log" {
		elasticsearch {
			hosts => ["localhost:9200"]
			index => "nginx-access-log"
		}
	}
}
```

??2????? logstash????? `-f` ?????????????????`bin/logstash -f logstash-input-file.conf`

?????????????��???https://www.elastic.co/guide/en/logstash/current/plugins-inputs-file.html

## ��????

### ????????????

?????? logstash ??��?????????????????????????????????????????????

```
# cd xxx ???? logstash ???????? bin ??
logstash -f logstash.conf
```

?????? logstash ?????? linux ???????????? nohup ???????????????????????????????????????????????????��?

**???? startup.sh**

```
nohup ./logstash -f logstash.conf >> nohup.out 2>&1 &
```

????????????��????????????? ps -ef | grep logstash ??????????????kill ???????????????��????????????????

**???? shutdown.sh**

???????????????????????��?

```
PID=`ps -ef | grep logstash | awk '{ print $2}' | head -n 1`
kill -9 ${PID}
```

## ????

- [Logstash ??????](https://www.elastic.co/guide/en/logstash/current/index.html)
- [logstash-logback-encoder](https://github.com/logstash/logstash-logback-encoder)
- [ELK Stack??????](https://github.com/chenryn/logstash-best-practice-cn)
- [ELK??Elasticsearch??Logstash??Kibana???????????](https://github.com/judasn/Linux-Tutorial/blob/master/ELK-Install-And-Settings.md)

## ??????

- [Elastic ?????](https://github.com/dunwu/JavaStack/blob/master/docs/javatool/elastic/README.md)
- [JavaStack](https://github.com/dunwu/JavaStack)
