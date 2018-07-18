Forsaken-Mail
==============
A self-hosted disposable mail service.

[Online Demo](http://disposable.dhc-app.com)

### Installation

#### Setting up your DNS correctly

In order to receive emails, your smtp server address should be made available somewhere. Two records should be added to your DNS records. Let us pretend that we want to receive emails at ```*@subdomain.domain.com```:
* First an MX record: ```subdomain.domain.com MX 10 mxsubdomain.domain.com```. This means that the mail server for addresses like ```*@subdomain.domain.com``` will be ```mxsubdomain.domain.com```.
* Then an A record: ```mxsubdomain.domain.com A the.ip.address.of.your.mailin.server```. This tells at which ip address the mail server can be found.

You can fire up Mailin (see next section) and use an [smtp server tester](http://mxtoolbox.com/diagnostic.aspx) to verify that everything is correct.

#### Let's Go
general way:
```
npm install && npm start
```
if you want to run this inside a docker container
```
docker build -t denghongcai/forsaken-mail .
docker run --name forsaken-mail -d -p 25:25 -p 3000:3000 denghongcai/forsaken-mail
```
Open your browser and type in
```
http://localhost:3000
```

Enjoy!

中文部署教程
=====

```
本教程是在CentOS上使用的，如有使用其他系统的，请自行替换相关命令，同时实测Ubuntu一样可以运行本程序。
```

### 前期准备工作

```
#安装git

yum install git -y

#安装node.js

wget https://nodejs.org/download/release/latest/node-v10.3.0-linux-x64.tar.gz

tar --strip-components 1 -xzvf node-v* -C /usr/local

#用下面命令能够返回版本信息则安装成功了

node --version
```

### 下载源码并安装

```
#下载项目源码

git clone https://github.com/lbjlaq/forsaken-mail.gitcd forsaken-mail

#安装项目所需的并启动

npm install && npm start
```

### 如果没报错的，这个时候直接访问自己的ip就可以看到显示正常了。

### 【80端口版】搭建临时邮箱系统forsaken-mail
###后台自动运行

```
npm install -g pm2pm2 start bin/www
pm2 startup

pm2 save
```

### 域名解析

然后把你的域名A记录解析到ip上就可以了。