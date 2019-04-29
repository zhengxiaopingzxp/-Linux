##### 实验准备
- 1、已完成DNS解析
>www.zxpzxp.cn
>mail.zxpzxp.cn

![](https://upload-images.jianshu.io/upload_images/7563229-0f3cbeaee27369fe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 2、已准备两个域名的SSL证书
> www.zxpzxp.cn
> mail.zxpzxp.cn

 ![](https://upload-images.jianshu.io/upload_images/7563229-30312039a44df094.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/7563229-7562d46caf9f1482.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
#####二、快速安装Lamp+wordpress
- 1．安装LAMP

![](https://upload-images.jianshu.io/upload_images/7563229-ee6a3c2d09114311.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> [root@centos7 ~]# yum install httpd  php  mariadb-server –y

- 2．安装php链接数据库的扩展程序包

> [root@centos7 ~]# yum install php-mysql
- 3．安装支持多字节字符串扩展的程序包

> [root@centos7 ~]# yum install php-mbstring -y

- 4．安装支持多加密扩展的程序包
> [root@centos7 ~]# yum install php-mcrypt –y

- 5．启动数据库服务

![](https://upload-images.jianshu.io/upload_images/7563229-0bf9d860adfbc2c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
[root@centos7 ~]# systemctl start mariadb.service
- 6．设置数据库root密码

> [root@centos7 ~]# mysqladmin -u root password 'centos'

- 7．启动WEB服务

![](https://upload-images.jianshu.io/upload_images/7563229-23b37b44e64bbf0d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> [root@centos7 ~]# systemctl start httpd.service

- 8．上传phpmyadmin并解压

![](https://upload-images.jianshu.io/upload_images/7563229-0b8c61796c1e8483.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/7563229-2a82aac9dd777d3a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> phpMyAdmin-4.0.10-all-languages.tar 到apache的DocumentRoot目录（/var/www/html）中.

![](https://upload-images.jianshu.io/upload_images/7563229-e423b1b97670bbae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> tar –xf  phpMyAdmin-4.0.10-all-languages.tar.gz

- 9．创建两个不同的wordpress数据库

 > wordpress       wordpress 1

![](https://upload-images.jianshu.io/upload_images/7563229-e7856138ff9471a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 10．上传wordpress到/var/www/目录，并配置wp-config.php
-  11.复制两个wordpress

> cp -r wordpress wordpress1
![](https://upload-images.jianshu.io/upload_images/7563229-662f322ef8b3dceb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 或者使用软连接
> ln -s wordpress wordpress1

![](https://upload-images.jianshu.io/upload_images/7563229-98ce9b982ee109c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 四、在httpd目录中新建ssl子目录，并将证书文件拷入其中
![](https://upload-images.jianshu.io/upload_images/7563229-1682df4f9cedcd8c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> /etc/httpd/ssl目录下

![](https://upload-images.jianshu.io/upload_images/7563229-4678aecba38c72f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
#### 五、搭建Linux虚拟主机

        相关知识：
> Apache服务器可利用虚拟主机功能在一台服务器上设置多个Web站点，Apache支持两种类型的虚拟主机：基于IP地址的虚拟主机和基于域名的虚拟主机。基于IP地址的各虚拟主机使用同一IP地址的不同端口或不同域名，或者是使用不同的IP地址。

###### 用户可直接使用不同的域名来访问此类虚拟主机。操作步骤如下：
- 1．在/etc/httpd/conf.d/目录下创建四个文件
![](https://upload-images.jianshu.io/upload_images/7563229-b83cbb796aaa4e5b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> （1） [<u>www.</u><u>zxpzxp</u><u>.cn</u>](http://www.zxpzxp.cn)（ vhost.conf 和vhosts.conf 两个文件）

> （2） Mail.zxpzxp.cn(vh.conf和vhs.conf)

######①vhost.conf
> <VirtualHost *:80>
DocumentRoot "/var/www/html/wordpress"
ServerName  www.zxpzxp.cn
	<Directory "/var/www/html /wordpress">
	AllowOverride None
	Require all granted
	</Directory>
</VirtualHost>


##### ②vhosts.conf
> <VirtualHost *:443>
DocumentRoot "/var/www/html/wordpress"
ServerName  www.zxpzxp.cn
	<Directory "/var/www/html/wordpress">
	AllowOverride None
	Require all granted
	</Directory>
SSLEngine on
SSLCertificateFile /etc/httpd/ssl/2_www.zxpzxp.cn.crt
SSLCertificateKeyFile /etc/httpd/ssl/3_www. zxpzxp.cn.key
SSLCertificateChainFile /etc/httpd/ssl/1_root_bundle.crt
</VirtualHost>

##### ③ vh.conf
> <VirtualHost *:80>
DocumentRoot "/var/www/html/wordpress1"
ServerName  mail. zxpzxp.cn
	<Directory "/var/www/html/wordpress1">
	AllowOverride None
	Require all granted
	</Directory>
</VirtualHost>

###### ④vhs.conf
> <VirtualHost *:443>
DocumentRoot "/var/www/html/wordpress1"
ServerName  mail. zxpzxp.cn
	<Directory "/var/www/html/wordpress1">
	AllowOverride None
	Require all granted
	</Directory>
SSLEngine on
SSLCertificateFile /etc/httpd/ssl/2_mail. zxpzxp.cn.crt
SSLCertificateKeyFile /etc/httpd/ssl/3_mail. zxpzxp.cn.key
SSLCertificateChainFile /etc/httpd/ssl/1_root_bundle.crt
</VirtualHost>

#### 六、加密网站测试结果
> https://www.zxpzxp.cn
 ![](https://upload-images.jianshu.io/upload_images/7563229-6f3be671885a8ce7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> https://mail.zxpzxp.cn
![](https://upload-images.jianshu.io/upload_images/7563229-ee8575228fca9c33.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

