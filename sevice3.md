## Linux-基本操作-3进程和服务（2）
### 周期性计划作业--cron
- cron:是一个进程。可以让linux周期性的执行某一命令。
- crontab是一个命令，可以设置linux周期性的执行某一命令。
     
       -u  ：设置某一个用户的周期性工作—root权限；
	   -e  ：编辑 crontab 的工作内容
	  -l  ：查阅 crontab 的工作内容
	  -r  ：移除所有的 crontab 的工作内容，若仅要移除一项，请用 -e 去编辑
![例子说明](https://upload-images.jianshu.io/upload_images/7563229-b605d223aefcdf3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### crontab的格式讲解
- 一行代表一个任务
     > minute   hour   day   month   week   command

- minute： 表示分钟，可以是从0到59之间的任何整数。
- hour：表示小时，可以是从0到23之间的任何整数。
- day：表示日期，可以是从1到31之间的任何整数。
- month：表示月份，可以是从1到12之间的任何整数。
- week：表示星期几，可以是从0到7之间的任何整数，这里的0或7代表星期日。
- command：要执行的命令，可以是系统命令，也可以是自己编写的脚本文件。

![格式讲解](https://upload-images.jianshu.io/upload_images/7563229-294417d8bc1004c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![格式讲解1](https://upload-images.jianshu.io/upload_images/7563229-23e959e8f61b50bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![例子说明1](https://upload-images.jianshu.io/upload_images/7563229-0d75affeb591194c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###/etc/crontab配置文件讲解
![文件讲解png](https://upload-images.jianshu.io/upload_images/7563229-2acd8e6410553764.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 第一行SHELL变量指定了系统要使用哪个shell，这里是bash。
- 第二行PATH变量指定了系统执行命令的路径。
- 第三行MAILTO变量指定了crond的任务执行信息将通过电子邮件发送给root用户，如果MAILTO变量的值为空，则表示不发送任务执行信息给用户。
### 输入输出重定向
  -   “ > file ”	 //标准输出重定向到文件—覆盖
- “>>file ” //标准输出重定向到文件—追加
- “ 2>” //标准错误重定向到文件—覆盖		
- “ 2>>”//标准错误重定向到文件—追加
- “ 2>/dev/null” //标准错误重定向到回收站
- “ &>file”//标准输出和标准错误重定向到文件—覆盖
- “ >>file 2>&1”//标准输出和标准错误重定向到文件—追加
*注：引号“”是不用输入的。*

![定向举](https://upload-images.jianshu.io/upload_images/7563229-af5e31e29da6d3b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 管道符
- 字符：｜。这就是管道符。
> 作用有两个：
>- 1、承上启下：把上一个指令的输出作为下一个指令的输入来执行。
> - 2、搭配grep 字符实现过滤功能。

![管道符](https://upload-images.jianshu.io/upload_images/7563229-57f18f676881f1b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![管道符](https://upload-images.jianshu.io/upload_images/7563229-fe908ea9d40a3ca9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*注：按ctrl + z 便可以停止退出。*
![管道符1](https://upload-images.jianshu.io/upload_images/7563229-2c808c15283a70c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 正则表达式和通配符
- 在linux中，有通配符和正则表达式，这是两个不同的概念
> 通配符：它是由shell解析，并且一般用于匹配文件名。如：ls

> 正则表达式：是一个字符匹配标准，可以匹配文本中的内容
- 一些命令工具按此标准实现字符匹配，常用于支持正则表达式的工具，如grep，sed等。一般用于匹配文件中的内容。
#### 常用的通配符
   > - *：匹配任意多个字符
>- ?：匹配任意一个字符
>- [...]：匹配中括号内出现的任意一个字符
>- [!...]：不匹配中括号内出现的任意一个字符.
#### 正则表达式
- **字符匹配**
> .：匹配任意单个字符
*：匹配其前面一个字符出现任意次
?：匹配其前面的字符1次或0次
+：匹配其前面一个字符出现至少一次（在扩展正则表达式中）

 **位置匹配**
- ^：锚定行首
 - $：锚定行尾
-  \<或\b：锚定词首，其后面的任意字符必须作为单词首部出现
- \>或\b：锚定词尾，其前面的任意字符必须作为单词尾部出现
- \B：非单词的开头或结尾
- ^$：空白行
- \ ：通常用于打开或关闭后续字符的特殊含义
![正则表达式](https://upload-images.jianshu.io/upload_images/7563229-72923f557c26b611.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 查找和替换
- grep只能用于查找文件中的内容
- sed可以查找，然后替换或者插入想要的内容
![查找替换](https://upload-images.jianshu.io/upload_images/7563229-226e1f55cce7de39.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

       a ：新增，a的后面可以接字串,而这些字串会在新的一行出现(目前的下一行)；
       d ：删除，因为是删除啊，所以d后面通常不接任何东西的；
       i ： 插入，i的后面可以接字串,而这些字串会在新的一行出现(目前的上一行)；
       p ：列印，亦即将某个选择的资料印出。通常 p 会与参数 sed
       s ：取代，可以直接进行取代的工作！
### 查找语句find
- 用法：find [路径] [命令参数] [表达式]
**参数：**
>-name “文件名”：查找指定名称文件；

>-user 用户名：查找指定用户拥有的文件；

>-group 组名：查找指定组拥有的文件；

>-mtime n：查找在N 天前被修改过的文件；

>-atime n：查找在N 天前被访问过的文件；

![find的用法](https://upload-images.jianshu.io/upload_images/7563229-d76de04e48253d97.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![find的用法1](https://upload-images.jianshu.io/upload_images/7563229-cdeef4ddd388eb25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
