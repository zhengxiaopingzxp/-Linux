# FTP服务器配置
**1、通过YUM（是一个软件仓库）安装VSFTP**
> 使用**yum install vsftpd -y命令**

![安装.png](https://upload-images.jianshu.io/upload_images/7563229-2c8b14e888213b47.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**2、查看端口状态：**

![查看状态.png](https://upload-images.jianshu.io/upload_images/7563229-99cdf2650c517780.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**3、修改FTP服务配置文件（/etc/vsftpd/vsftpd.conf）:不允许匿名用户登录**
> /etc/vsftpd/vsftpd.conf

![修改文件.png](https://upload-images.jianshu.io/upload_images/7563229-cb99f4472fe2df22.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 4、将 anonymous_enable 改掉
![修改.png](https://upload-images.jianshu.io/upload_images/7563229-12eaf33dd880d051.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**5、重启FTP服务：service restart vsftpd :**
> service restart vsftpd

![重启服务.png](https://upload-images.jianshu.io/upload_images/7563229-1cca3d084a36bf98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**6、创建** **FTP** **用户：（并设置密码）**
![创建用户.png](https://upload-images.jianshu.io/upload_images/7563229-62bf0e3d777bb0cf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**7、查找端口：**
> netstat -nltp

![查找端口.png](https://upload-images.jianshu.io/upload_images/7563229-f0b790be659711df.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**8、限制用户只能通过** **FTP** **访问服务器，而不能直接登录服务器：**

> **usermod -s /sbin/nologin wx2017**


**9、为用户分配主目录**

![分配主目录.png](https://upload-images.jianshu.io/upload_images/7563229-2a885c90fedf7282.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![分配主目录（1）.png](https://upload-images.jianshu.io/upload_images/7563229-809378671cf211a2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**10、创建登录欢迎文件：**

> **echo "Welcome to use FTP service." > /data/ftp/welcome.txt**

**(1)设置访问权限：**

> **chmod a-w /data/ftp && chmod 777 -R /data/ftp/pub**

**(2)设置为用户的主目录：**

> **usermod -d /data/ftp wx2017**

![设置主目录.png](https://upload-images.jianshu.io/upload_images/7563229-c26d2ce506fd3029.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**11、成功上传文件：**（这里需要下载一个软件："FlashFXP 5"，这个就是上传文件的必备工具。）

![上传文件.png](https://upload-images.jianshu.io/upload_images/7563229-92b8fa8d1fd62e78.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
