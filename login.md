### Linux服务器的密码登录方式

#### 1、SSH密钥（口令）登录

######  生成密钥：[<u>https://console.cloud.tencent.com/cvm/sshkey</u>](https://console.cloud.tencent.com/cvm/sshkey)

![生成秘钥](https://upload-images.jianshu.io/upload_images/7563229-fcb41f51e2082de9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 2、SSH密钥登录：
![登录](https://upload-images.jianshu.io/upload_images/7563229-68c5da0943aba778.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 3、SSH密钥（非对称）登录
- （1）要先登陆：PuTTYPortable.exe（整个过程要准备两个PuTTYPortable.exe，一个作为客户机登陆，一个是用来登陆自己的服务器）
![登录PUTTY](https://upload-images.jianshu.io/upload_images/7563229-d4efd94c87840e16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- （2）登陆客户机生成密钥对：
ssh-keygen  -t   rsa        并为进入的文件设置key（设定是zxp）
![登录客户机](https://upload-images.jianshu.io/upload_images/7563229-38d26ce31ea520e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### 4、上传公钥到服务器：
> scp  zxp.pub   root@182.254.192.28:/root（这里的IP地址是自己的）

![](https://upload-images.jianshu.io/upload_images/7563229-1000e287ca79776f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 5、查看文件：
![](https://upload-images.jianshu.io/upload_images/7563229-c6610c06a23586b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 6、登陆自己的服务器（此时需要自己再打开一次PuTTYPortable.exe）
###### 7、更改认证文件名：

![更改名字](https://upload-images.jianshu.io/upload_images/7563229-a9d621702b7f3faa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 8、修改权限：
![修改权限](https://upload-images.jianshu.io/upload_images/7563229-3994ee72acc3bae2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 9\修改配置文件 ：
![修改配置文件](https://upload-images.jianshu.io/upload_images/7563229-663edc111260d326.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 10、如以下命列：
![](https://upload-images.jianshu.io/upload_images/7563229-f032a441c890b4a2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![修改文件内容](https://upload-images.jianshu.io/upload_images/7563229-e4144f3e98fa7a5d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![修改文件内容1](https://upload-images.jianshu.io/upload_images/7563229-f753905f17954c1e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![修改文件内容2](https://upload-images.jianshu.io/upload_images/7563229-fe9714b34484fc15.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![修改文件内容3](https://upload-images.jianshu.io/upload_images/7563229-ddc2f3db1e088ad7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 11、重启服务器：
![重启服务](https://upload-images.jianshu.io/upload_images/7563229-12045284d36cfb22.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 12、用客户机登录到对方的服务器：

![](https://upload-images.jianshu.io/upload_images/7563229-2db0e8b5dd372695.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 13、更改完之后，已经设定了禁止使用密码验证登陆了，所以想要重新在window下登录时，只能选择另一个软件Xshell，然后把对方的私钥下载并保存在本地。
>  13（1）、首先登录客户机，找到密钥的位置（目前是在root下）

![](https://upload-images.jianshu.io/upload_images/7563229-d9eabe34dcb96e8a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 13（2）使用SSH Secure File Transfer Client 将密钥拷贝到桌面：

![图片.png](https://upload-images.jianshu.io/upload_images/7563229-e0729da858cb6c93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 14、然后打开Xshell，新建会话：
![图片.png](https://upload-images.jianshu.io/upload_images/7563229-8eee6905c42bf06b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 15、选择用户身份验证：
![](https://upload-images.jianshu.io/upload_images/7563229-0036873c9d8fc7e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 16、以上步骤完成后再双击自己新建的会话，便可以直接进入：
![](https://upload-images.jianshu.io/upload_images/7563229-67901981e5a27ec7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
