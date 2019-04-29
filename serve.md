- 1、安装DNS域名系统：
> **yum -y install bind**

- 2、修改主配置文件：
> **vim /etc/named.conf**

![](https://upload-images.jianshu.io/upload_images/7563229-798ca5233a702f9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 3、创建域名
> **vim /etc/named.conf**

![](https://upload-images.jianshu.io/upload_images/7563229-5b4d5bd264e42c1f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 4、创建正向区域数据库文件

![](https://upload-images.jianshu.io/upload_images/7563229-bb49808e626729c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 5、修改正向区域数据库文件
> **vim /var/named/zdnf.com.zone**

[图片上传失败...(image-f6c7b4-1555317887051)]

- 6、重启服务：

![](https://upload-images.jianshu.io/upload_images/7563229-7dadcff40f68f515.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 7.在客户端设置域名服务器的地址
> vim /etc/resolv.conf
nameserver 182.254.192.28  

![](https://upload-images.jianshu.io/upload_images/7563229-9c12360bb83182b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 8. 测试
>（1）先在腾讯云上解析：（添加记录）

![ ](https://upload-images.jianshu.io/upload_images/7563229-d8ae1fb51545d41b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> ①、nslookup dns.zxpzxp.cn

![](https://upload-images.jianshu.io/upload_images/7563229-0c6faf08e98d5d55.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>  ②、nslookup ftp.zxpzxp.cn

![](https://upload-images.jianshu.io/upload_images/7563229-9595832c80d6f382.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>   ③、Nslookup mail.zxpzxp.cn

![](https://upload-images.jianshu.io/upload_images/7563229-be27318dc6ab5c87.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>  ④、nslookup www.zxpzxp.cn

![](https://upload-images.jianshu.io/upload_images/7563229-e8fdc6c8510f824e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
