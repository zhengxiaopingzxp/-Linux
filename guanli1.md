### Linux-基本操作-3进程和服务（1）
#### 分析和存储日志
- 日志：用于系统审核和故障排除---*Liunx中的“黑匣子”*
- 日志文件都是保存在/var/log目录中的在RedHat 7中，系统日志消息由两个服务负责处理。他们是systemd-journald和rsyslogd。

      /var/log/messages		//大多数系统日志消息记录的日志

      /var/log/secure		//安全和身份验证的消息和错误日志

      /var/log/maillog		//与邮件服务器相关的日志

      /var/log/cron		//与定期执行任务相关的日志文件

      /var/log/boot/log		//记录和系统启动有关的日志
![log](https://upload-images.jianshu.io/upload_images/7563229-bd3effe091e49bdd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 许多程序使用syslog协议将事件记录到系统。每一个日志都会根据消息类型和严重性分类
![日志](https://upload-images.jianshu.io/upload_images/7563229-795591d8df1ec4c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##### 日志分析
- 大多数日志由四个部分组成
>1、记录在日志的时间
2、发送该日志的主机
3、发送该日志消息的程序或进程
4、发送的实际消息
##### 日志监控
    tail –f /var/log/secure	//显示最后10行，如果有新的内容加入，那么会继续输出
#### 打包和压缩
     打包程序：tar
   
>-  c：创建文档；
  > - t：列出存档内容；
   >-  x：提取存档；**即解压文件**
  >-   f filename：要操作的存档的文件名；
   >-  v：详细信息

![打包](https://upload-images.jianshu.io/upload_images/7563229-54a1b6603be29787.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![打包成功](https://upload-images.jianshu.io/upload_images/7563229-ee866ab50f984e35.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**注意：**
>1、选项前不用加-
2、创建之前请检查有木有重名文件（覆盖且不提示）
3、要使tar可以打包选定的文件，执行tar命令的用户必须要能够读取这些文件

###### tar支持三种不同压缩方式：
- 1、gzip：压缩速度最快，历史最久，应用最广泛；
![压缩](https://upload-images.jianshu.io/upload_images/7563229-bf79fdbed902ccfb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![压缩1](https://upload-images.jianshu.io/upload_images/7563229-8d2bb9526f01fc33.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 2、 bzip2：压缩成的存档文件小，可用性不如gzip；
- 3、xz ：最新的方式，提供最佳的压缩率。

- 实际环境中3种情况都可能遇到，所以要创建不一样格式的归档文件就有自己的选项。

      z用于gzip压缩：filename.tar.gz
      j用于bzip2压缩：filename.tar.bz2
      J用于xz压缩：filename.tar.xz
![压缩2](https://upload-images.jianshu.io/upload_images/7563229-04333bf7b8a6c5be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![压缩大小对比](https://upload-images.jianshu.io/upload_images/7563229-9adb0ce93c399a65.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**解压文件：**

     tar xf 文件名 （比如：zxpzxpzxp.tar.bz2）
- 这里我先删除了我之前创建的文件：zxpzxpzxp.tar
![删除文件](https://upload-images.jianshu.io/upload_images/7563229-c01ac783f475bc05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片.png](https://upload-images.jianshu.io/upload_images/7563229-e39a82209e59fc88.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 再输入解压文件的命令：
![解压文件](https://upload-images.jianshu.io/upload_images/7563229-f10382ff490327f8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![解压成功](https://upload-images.jianshu.io/upload_images/7563229-9ec9b54333af87b9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
