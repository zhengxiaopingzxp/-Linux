# CentOS 7.3下phpMyAdmin安装部署
> phpMyAdmin 是一个用PHP编写的软件工具，可以通过web方式控制和操作MySQL数据库。通过phpMyAdmin 可以完全对数据库进行操作，例如建立、复制和删除数据等等。如果使用合适的工具，MySQL数据库的管理就会变得相当简单。应用 MySQL 命令行方式需要对 MySQL 知识非常熟悉，对SQL语言也是同样的道理。不仅如此，如果数据库的访问量很大，列表中数据的读取就会相当困难。
- 当前出现很多GUI MySQL客户程序，其中最为出色的是基于 Web 的phpMyAdmin 工具。这是一种 MySQL数据库前台的基于PHP的工具。
PhpMyAdmin 的缺点是必须安装在 Web 服务器中，所以如果没有合适的访问权限，其它用户有可能损害到 SQL 数据。
### 安装环境
- 在同一台主机上部署LAMP
> Linux（ [CentOS](https://www.linuxidc.com/topicnews.aspx?tid=14 "CentOS") 7.3 ） 、Apache（httpd2.4）、MariaDB（5.5）、PHP（5.4）

#### 源码包下载
- 在官网[http://www.phpmyadmin.net/](http://www.phpmyadmin.net/)下载phpMyAdmin源码包phpMyAdmin-4.0.10.20-all-languages.tar

### 安装软件
> （1）安装LAMP[root@centos7 ~]# yum install httpd  php  mariadb-server –y
> （2）安装php链接数据库的扩展程序包[root@centos7 ~]# yum install php-mysql
> （3）安装支持多字节字符串扩展的程序包[root@centos7 ~]# yum install php-mbstring -y
> （4）安装支持多加密扩展的程序包[root@centos7 ~]# yum install php-mcrypt –y

![1.png](https://upload-images.jianshu.io/upload_images/7563229-818a7c0aa1af3f16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### phpmyadmin配置
- 将phpMyAdmin-4.0.10-all-languages.ta上传到服务器
> /var/www/html

![2.png](https://upload-images.jianshu.io/upload_images/7563229-0aaaafe20ec6f9ee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### （1）解压文件
- 解压phpMyAdmin-4.0.10-all-languages.tar 到apache的DocumentRoot目录（/var/www/html）中
[root@centos7 ~]# tar -xf phpMyAdmin-4.0.10-all-languages.tar.gz  -C /var/www/html/
> tar -xf phpMyAdmin-4.0.10-all-languages.tar.gz  -C /var/www/html/

![3.png](https://upload-images.jianshu.io/upload_images/7563229-69246b5b9c36f146.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

######（2）复制phpmyadmin的简单配置文件config.sample.inc.php，作为默认配置文件
- [root@centos7 ~]# cp  –a   /var/www/html/phpMyAdmin-4.0.10-all-languages/config.sample.inc.php  /var/www/html/phpMyAdmin-4.0.10-all-languages/config.inc.php
>  cp  –a   /var/www/html/phpMyAdmin-4.0.10-all-languages/config.sample.inc.php  /var/www/html/phpMyAdmin-4.0.10-all-languages/config.inc.php

![4.png](https://upload-images.jianshu.io/upload_images/7563229-50d39c916f7559eb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

######（3）编辑配置文件config.inc.php

- [root@centos7 ~]# vim /var/www/html/phpMyAdmin-4.0.10-all-languages/config.inc.php

![5.png](https://upload-images.jianshu.io/upload_images/7563229-75f459605c9f7200.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![6.png](https://upload-images.jianshu.io/upload_images/7563229-d7512cf1a76f6616.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

######（4）创建软链接
- [root@centos7 ~]# ln -s /var/www/html/phpMyAdmin-4.0.10-all-languages/  /var/www/html/pma
![7.png](https://upload-images.jianshu.io/upload_images/7563229-729c05df256643aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 数据库MariaDB配置
######（1）启动数据库服务
- [root@centos7 ~]# systemctl start mariadb.service
######（2）设置数据库root密码
- [root@centos7 ~]# mysqladmin -u root password 'centos'
![8.png](https://upload-images.jianshu.io/upload_images/7563229-3ce096396de6a40b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 启动WEB服务
- [root@centos7 ~]# systemctl start httpd.service
![9.png](https://upload-images.jianshu.io/upload_images/7563229-ac0225df68e619b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 测试
######（1）在浏览器输入[*http://182.254.192.28/pma/*](http://182.254.192.28/pma/)  
![10.png](https://upload-images.jianshu.io/upload_images/7563229-ac53394c65f542da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### （2）用root用户登录
![11.png](https://upload-images.jianshu.io/upload_images/7563229-cb9c05d302917397.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 安装证书：yum install mod_ssl openssl
![12.png](https://upload-images.jianshu.io/upload_images/7563229-7c63e7f42712d5d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


###### 安装好后，/etc/httpd/conf.d/下应该有ssl.conf
![13.png](https://upload-images.jianshu.io/upload_images/7563229-ad34051c4b248a05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### Wordpress成功搭建
![14.png](https://upload-images.jianshu.io/upload_images/7563229-d6f33127c9df0dd8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
