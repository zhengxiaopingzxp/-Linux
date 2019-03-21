# CentOS 7.3下phpMyAdmin安装部署
Linux（ CentOS 7.3 ） 、Apache（httpd2.4）、MariaDB（5.5）、PHP（5.4）
主机IP：181.254.192.28
###  1、安装软件
 ![]()
#### （1）安装LAMP
[root@centos7 ~]# yum install httpd  php  mariadb-server –y

#### （2）安装php链接数据库的扩展程序包
[root@centos7 ~]# yum install php-mysql
#### （3）安装支持多字节字符串扩展的程序包
[root@centos7 ~]# yum install php-mbstring -y
#### （4）安装支持多加密扩展的程序包
[root@centos7 ~]# yum install php-mcrypt –y
### 2 phpmyadmin配置

将phpMyAdmin-4.0.10-all-languages.ta上传到服务器
 
#### （1）解压文件
解压phpMyAdmin-4.0.10-all-languages.tar 到apache的DocumentRoot目录（/var/www/html）中
[root@centos7 ~]# tar -xf phpMyAdmin-4.0.10-all-languages.tar.gz  -C /var/www/html/
 
#### （2）复制phpmyadmin的简单配置文件config.sample.inc.php，作为默认配置文件
[root@centos7 ~]# cp  –a   /var/www/html/phpMyAdmin-4.0.10-all-languages/config.sample.inc.php  /var/www/html/phpMyAdmin-4.0.10-all-languages/config.inc.php
 
#### （3）编辑配置文件config.inc.php
[root@centos7 ~]# vim /var/www/html/phpMyAdmin-4.0.10-all-languages/config.inc.php
 
 
#### （4）创建软链接
[root@centos7 ~]# ln -s /var/www/html/phpMyAdmin-4.0.10-all-languages/  /var/www/html/pma
 
### 3 数据库MariaDB配置
#### （1）启动数据库服务
[root@centos7 ~]# systemctl start mariadb.service
#### （2）设置数据库root密码
[root@centos7 ~]# mysqladmin -u root password 'centos'

 ### 4启动WEB服务
[root@centos7 ~]# systemctl start httpd.service
 
### 5 测试
#### （1）在浏览器输入http://182.254.192.28/pma/ 
 
#### （2）用root用户登录
  部署完成










安装证书：yum install mod_ssl openssl

 
 
安装好后，/etc/httpd/conf.d/下应该有ssl.conf

 

Wordpress成功搭建
 



