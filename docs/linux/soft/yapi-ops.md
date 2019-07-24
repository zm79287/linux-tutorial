# YApi ��ά

> [YApi](https://github.com/YMFE/yapi) ��һ���ɱ��ز���ġ���ͨǰ��˼� QA �ġ����ӻ��Ľӿڹ���ƽ̨��
>
> ����Ŀ�����ڼ�¼ svn �İ�װ�����á�ʹ�á�

<div align="center"><img src="https://gitee.com/turnon/images/raw/master/snap/1562814562978.png"/></div>

<!-- TOC depthFrom:2 depthTo:3 -->

- [1. ��ͨ����](#1-��ͨ����)
    - [1.1. ����Ҫ��](#11-����Ҫ��)
    - [1.2. ����](#12-����)
    - [1.3. ����](#13-����)
- [2. Docker ����](#2-docker-����)
    - [2.1. ����Ҫ��](#21-����Ҫ��)
    - [2.2. ����](#22-����)
- [3. �ο�����](#3-�ο�����)

<!-- /TOC -->

## 1. ��ͨ����

### 1.1. ����Ҫ��

- nodejs��7.6+)
- mongodb��2.6+��
- git

### 1.2. ����

#### ��ʽһ. ���ӻ�����[�Ƽ�]

ִ�� yapi server �������ӻ��������������Ӧ�����ú͵����ʼ���𣬾������������վ�Ĳ��𡣲������֮�󣬿ɰ�����ʾ��Ϣ��ִ�� node/{��վ·��/server/app.js} ���������������������ָ�� url, �����¼�������ղ����õĹ���Ա���䣬Ĭ������(ymfe.org) ��¼ϵͳ��Ĭ��������ڸ��������޸ģ���

```bash
$ npm install -g yapi-cli --registry https://registry.npm.taobao.org
$ yapi server
```

#### ��ʽ��. �����в���

��� github ѹ���ļ��޷����أ�����Ҫ����һЩ����ķ��������ɳ��Դ˷���

```bash
mkdir yapi
cd yapi
git clone https://github.com/YMFE/yapi.git vendors //�������� zip ����ѹ�� vendors Ŀ¼��clone �����ֿ��� 140+ M������ͨ�� `git clone --depth=1 https://github.com/YMFE/yapi.git vendors` ������٣���� 10+ M��
cp vendors/config_example.json ./config.json //������ɺ����޸��������
cd vendors
npm install --production --registry https://registry.npm.taobao.org
npm run install-server //��װ������ʼ�����ݿ������͹���Ա�˺ţ�����Ա�˺������� config.json ����
node server/app.js //����������������� 127.0.0.1:{config.json���õĶ˿�}���������л��и�����Ĺ��̣������ĵȺ�
```

��װ���Ŀ¼�ṹ���£�

```
|-- config.json
|-- init.lock
|-- log
`-- vendors
    |-- CHANGELOG.md
    |-- LICENSE
    |-- README.md
    |-- client
    |-- common
    |-- config_example.json
    |-- doc
    |-- exts
    |-- nodemon.json
    |-- npm-debug.log
    |-- package.json
    |-- plugin.json
    |-- server
    |-- static
    |-- test
    |-- webpack.alias.js
    |-- yapi-base-flow.jpg
    |-- ydocfile.js
    `-- ykit.config.js
```

### 1.3. ����

������Ŀ�汾�Ƿǳ����׵ģ����Ҳ���Ӱ�����е���Ŀ���ݣ�ֻ��ͬ�� vendors Ŀ¼�µ�Դ���ļ���

```
cd  {��ĿĿ¼}
yapi ls //�鿴�汾���б�
yapi update //���������°汾
yapi update -v v1.1.0 //������ָ���汾
```

## 2. Docker ����

### 2.1. ����Ҫ��

- ϵͳ��`CentOS 7.4`
- Ӳ��Ҫ��`1 GB RAM minimum`
- ip��`http://192.168.1.121`
- docker version��`17.12.1-ce, build 7390fc6`
- docker-compose version��`1.18.0, build 8dd22a9`

> ���鲿��� http վ�㣬�� chrome �������ȫ���ƣ������ https �ᵼ�²��Թ��������� http վ��ʱ�ļ��ϴ������쳣��--[��Դ](https://yapi.ymfe.org/devops.html)

### 2.2. ����

- һ�������˵�ά����<https://github.com/branchzero/yapi-docker>
- ʹ�÷����� - work path��`mkdir -p /opt/git-data` - clone��`cd /opt/git-data && git clone https://github.com/branchzero/yapi-docker.git` - permission��`chmod -R 777 /opt/git-data` - run command��`cd /opt/git-data/yapi-docker && docker-compose up -d` - open chrome��`http://192.168.1.121:3000`
- ��ʼ������Ա�˺�����`admin@admin.com`�����룺`ymfe.org`

## 3. �ο�����

- [�ٷ� Github](https://github.com/YMFE/yapi)
- [����������ʾ](http://yapi.demo.qunar.com/)
- [�ٷ�ʹ���ֲ�](https://hellosean1025.github.io/yapi/index.html)
