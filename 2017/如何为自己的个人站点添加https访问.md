# 如何为自己的个人站点添加https访问

很早之前在搭建这个博客的时候就使用了免费的https证书访问，当然申请的是 `Let's Encrypt` 的，这个证书有3个月的有效期，3个月之后就失效了。前两天突然访问的时候就发现证书无效了，弄了一两个小时才OK，所以把这个过程记录下来，给有需要的朋友参考。

以前是用的是一种手动方式来搭建https，今天要介绍了是使用`certbot`自动获取证书，并实现脚本自动两个月之后更新证书

## 第一步 下载certbot

第一步很简单，直接从github上下载`certbot`

```bash
git clone https://github.com/certbot/certbot
```

进入其目录，你也可以执行命令来查看其提供的功能

```bash
cd certbot
./certbot-auto --help
```

## 第二步 生成免费证书

直接执行下面的命令：

```bash
./certbot-auto certonly --webroot --agree-tos -v -t --email 邮箱地址 -w 网站根目录 -d 网站域名
```

我的是这样的：

```bash
./certbot-auto certonly --webroot --agree-tos -v -t --email kaindy7633@gmail.com -w /home/www/todever -d www.todever.com
```

**注意** 这里会自动生成一个文件夹：`/.well-known/acme-challenge`，默认生成到 `/网站根目录/.well-known/acme-challenge`，然后 shell 脚本会对应的访问 `网站域名/.well-known/acme-challenge` 是否存在来确定你对网站的所属权

比如：我的域名是 `www.todever.com` 那我就得保证域名下面的 `.well-known/acme-challenge/` 目录是可访问的

如果返回正常就确认了你对这个网站的所有权，就能顺利生成，完成后这个目录会被清空

## 第三步 获取证书

如果这面的 `shell` 执行完毕后显示如下信息：

```bash
- Congratulations! Your certificate and chain have been saved at
/etc/letsencrypt/live/网站域名/fullchain.pem
...
```

恭喜你，已完成一大半工作啦...

## 第四步 生成 `dhparams`

使用 `openssl` 工具生成 `dhparams`，这个过程时间可能会有点长

```bash
openssl dhparam -out /etc/ssl/certs/dhparams.pem 2048
```

你也可以随意指定生成目录，当然，后面配置 `nginx` 的时候会用到这个目录

## 第五步 配置 `Nginx`

打开 `nginx server` 配置文件加入如下设置：

```bash
ssl on;
ssl_certificate /etc/letsencrypt/live/网站域名/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/网站域名/privkey.pem;
ssl_dhparam /etc/ssl/certs/dhparams.pem;
ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
ssl_ciphers HIGH:!aNULL:!MD5;
```

接着重启Nginx就好了

```bash
systemctl restart nginx.service
```

## 第六步 强制跳转 `https`

`https` 默认是监听 `443` 端口的，没开启 `https` 访问的话一般默认是 `80` 端口。如果你确定网站 `80` 端口上的站点都支持 `https` 的话加入下面的配件可以自动重定向到 https

```bash
server {
    listen       80;
    server_name  todever.com www.todever.com;

    rewrite ^(.*)$  https://$host$1 permanent;
}
```

## 第七步 证书更新

免费证书只有 `90` 天的有效期，到时需要手动更新 `renew`。 我们可以去 `Let’s monitor` 免费注册账号添加域名监控，系统会在证书马上到期时发出提醒邮件，非常方便。收到邮件后去后台执行 `renew` 即可

```bash
./certbot-auto renew
```

## 如何配置自动更新

新建文件 `renew_cert.sh`，写入下面的脚本：

```bash
#!/bin/bash

rm -rf /etc/letsencrypt/live/*.* 
~/certbot/certbot-auto renew && systemctl restart nginx.service
```

如果这里有同名的域名文件夹，`certbot` 会自动创建 `域名+0001` 的其他文件夹，这样我们就需要更改 `nginx` 配置了，所以在生成之前删除原来的

再次说明我的Centos版本是7.1


