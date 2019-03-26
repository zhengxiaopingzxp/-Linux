## SSL证书的安装
### 证书申请
[<u>https://cloud.tencent.com/document/product/400/4142#ManualVerification</u>](#ManualVerification)
### 证书安装
- LAMP的ssl的证书的安装
>  yum -y install mod_ssl 

![](https://upload-images.jianshu.io/upload_images/7563229-cefaf2632cebcdd1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/7563229-08645aa7a76cb6ef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/7563229-27451cffd9d21032.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 配置 /etc/httpd/conf.d/ssl.conf
### 打开隐藏的配置文件，修改为自己的ssl证书。
- 首先要将自己的证书下载，并放在C盘
![下载证书](https://upload-images.jianshu.io/upload_images/7563229-bf853658186c24c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![位置图](https://upload-images.jianshu.io/upload_images/7563229-7a206e2c182ea3a5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 在putty里，开始修改文件：
![修改文件](https://upload-images.jianshu.io/upload_images/7563229-9d4d919f25a26f0d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 按照位置图（即你下载的证书里面的文件名，对照修改  **ssl.conf**  文件）
![](https://upload-images.jianshu.io/upload_images/7563229-d7cf5526e18dd7a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/7563229-a5c834bd42f6f5d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 上传文件：
![](https://upload-images.jianshu.io/upload_images/7563229-8e11072c576b9c6a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/7563229-926ea3e2c469fba2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###分别将证书上传
![](https://upload-images.jianshu.io/upload_images/7563229-5dde206b86f76081.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 重启httpd：上传个人简历。
![](https://upload-images.jianshu.io/upload_images/7563229-520bf20908d1d806.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
