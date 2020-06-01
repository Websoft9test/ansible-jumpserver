# JumpServer Notes

组件名称：JumpServer  
安装文档：https://jumpserver.readthedocs.io/zh/master/setup_by_fast.html
配置文档：https://jumpserver.readthedocs.io/zh/master/quick_start.html
支持平台： 


## 概要

JumpServer 是全球首款完全开源的堡垒机, 使用 GNU GPL v2.0 开源协议, 是符合 4A 的专业运维审计系统。

## 环境要求

* 程序语言 :   Python / django 
* 应用服务器：
* 数据库：mariadb
* 依赖组件: koko  Guacamole  Redis  
* 代理 :nginx
* 其他：

## 安装说明

官网提供了极速安装脚本
JumpServer 所在机器的 CPU 需要至少 2核
JumpServer 所在机器的内存需要至少 4G

下面基于不同的安装平台，分别进行安装说明。

### CentOS

```shell
 cd /opt
 yum -y install wget git
 git clone --depth=1 https://github.com/jumpserver/setuptools.git
 cd setuptools
 cp config_example.conf config.conf
 vi config.conf

# 安装
 ./jmsctl.sh install

#帮助
./jmsctl.sh -h

ssh -p 2222 用户名@JumpServer IP地址     #命令行登录
```

## 路径

* 程序路径：/opt/jumpserver/jms
* 日志路径：  /opt/jumpserver/logs/jms.logs  和 /opt/jumpserver/logs/jumpserver.logs
* 配置文件路径：  /opt/setuptools/config.conf 和 /opt/jumpserver/config.yml		
* 其他...

## 配置

安装完成后，需要依次完成如下配置

```shell

```

## 账号密码

### 数据库密码

如果有数据库

* 数据库安装方式： 自行安装
* 账号密码:  
  cat /opt/setuptools/config.conf
  db_user=jumpserver
  db_password=bLf4oiEiKwAsT4vsOdQ3M1Xb
  db_name=jumpserver

### 后台账号

如果有后台账号

* 登录地址   http://ip:80
* 账号密码   admin   admin
* 密码修改方案：最好是有命令行修改密码的方案

```shell
#修改或者重置管理员密码
source /opt/py3/bin/activate
cd /opt/jumpserver/apps
python manage.py changepassword  <user_name>

#新建超级用户
 python manage.py createsuperuser --username=user --email=user@domain.com
```

## 服务

本项目安装后自动生成：JumpServer 服务

备注：如果开机没有服务，程序无法运行的情况下，需要自行编写服务

服务的模板如下：

```
[Unit]
Description=Redmine
After=nginx.service
[Service]
Environment=RAILS_ENV=production
Type=simple
WorkingDirectory=/data/wwwroot/redmine
ExecStart=/usr/local/bin/puma -b tcp://127.0.0.1:9292 -e production 
User=redmine
[Install]
WantedBy=multi-user.target
```

## 环境变量

列出需要增加的环境变量以及增加环境变量的命令：无

* 名称 | 路径

## 版本号

通过如下的命令获取主要组件的版本号: 

```
# Check JumpServer version
cat  /opt/setuptools/config.conf  |grep -i version

# Check mysql version
mysql -V

# Check Redis version
rpm -qa |grep redis

# Check Nginx  version
/usr/sbin/nginx -v

```

## 常见问题

#### 有没有管理控制台？

*http:// 公网 IP:80* 即可访问控制台，系统默认存在一个无法通过外网访问的admin/admin账号

#### 本项目需要开启哪些端口？

| item       | port |
| ---------- | ---- |
| JumpServer | 8080 |
| JumpServer | 8070 |
| koko       | 2222 |
| koko       | 5000 |
| Guacamole  | 8081 |
| Nginx      | 80   |
| Redis      | 6379 |
| Mysql      | 3306 |

#### 有没有CLI工具？

无

## 日志

* 2020-04-24 完成CentOS安装研究