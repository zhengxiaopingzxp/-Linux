## Linux用户账户管理
- UID和GID：Linux看的
- id : 查看当前登入用户的UID和GID

- 当我们使用ls –l的时候，系统会根据/etc/passwd和/etc/group文件的内容，找到UID和GID对应的名称，进行显示

> /etc/passwd ：记录了Linux上所有的账号

> /etc/shadow：记录了账户对应的密码

> /etc/group：记录了所有的组

##### /etc/passwd
![用户账户](https://upload-images.jianshu.io/upload_images/7563229-5321c5e1d251a166.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- zxp9：用户名

- X：早期这个部分放的是用户登入密码，现在密码放入了/etc/shadow中了

- UID：0表示系统管理员，1-999保留给系统使用的ID，1000以上给一般使用者

- GID：0表示系统管理员，1-999保留给系统使用的ID，1000以上给一般使用者
- /home/zxp9：用户家目录，用登入时，所在的目录

- /bin/bash：用户在登入的时候，是否可以使用shell，如果不能使用shell，则会显示**/sbin/nologin**
##### /etc/shadow
![shadow](https://upload-images.jianshu.io/upload_images/7563229-1e7d6ccd18c6ddd0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- Root：用户名
- 密码不能改修改的天数：0表示随时可以修改
![group](https://upload-images.jianshu.io/upload_images/7563229-ea79550e0bf30b96.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- zhengxiaoping:组名
- X：组密码，一般不需要
- 1000：GID
- 附属组:这些文件不建议直接进行修改，建议使用命令进行修改。
##### Linux用户创建-useradd
- A、 useradd
> -u：设置UID
-g：设置主要组
-G：设置要附属组
-c：设置用户说明
-d：指定用户家目录
-s：指定用户shell
-e：账号失效日期，格式为：YYYY-MM-DD
-f：指定密码是否失效，0表示立刻失效，1表示永不失效

![创建用户](https://upload-images.jianshu.io/upload_images/7563229-3ca8d926b7993515.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- B、使用了useradd后，会默认做以下几个操作
>1、在/etc/passwd下建立相关的资料
2、在/etc/shadow下写入密码的相关的参数
3、在/etc/group中写入和账号名一样的组
4、在/home下创建用户的家目录

>**id命令:**显示用户的uid和gid

- C、passwd 用户名 //所有人都可以通过该命令来修改自己的密码
>-l：锁住该账号，在/etc/shadow中放密码的位置加个！
-u：解锁
-S：显示账号的密码参数
-n：接天数，设置多久可以不修改密码
-x：接天数，设置多久内必须修改密码
-w：接天数，设置密码过期前警告天数
-i：接天数，设置密码失效天数

![显示账号的密码参数
](https://upload-images.jianshu.io/upload_images/7563229-40d3e8f2d955d973.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### Linux用户创建-chage
- chage 可以修改和密码有关的时间参数
>-l：查看一个账户和密码有关的时间参数
-d：YYYY-MM-DD，修改最近一次更改密码的时间
-E： YYYY-MM-DD，修改账号的失效时间
-I：天数，设置密码几天后失效
-m：天数，设置密码至少保留几天
-M：天数，设置密码多久后，需要更新
-W：天数，设置密码过期前警告时间

![change的使用](https://upload-images.jianshu.io/upload_images/7563229-24234e478bfefaac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### Linux用户创建-usermod
- usermod可以对用户账户的信息进行细微的修改。
> -c：账号说明
-d：修改家目录
-g：修改主要组
-G：修改附属组
-a：与-G一起用，增加附属组
-l：修改用户名
-u：修改UID
-L：冻结账号
-U：解冻

![创建文件](https://upload-images.jianshu.io/upload_images/7563229-02bc3864c323c26b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##### 删除一个用户-userdel
- 要彻底的删除一个账号，比较麻烦
> 1、删除/etc/passwd;/etc/shadow文件中的内容
2、删除/etc/group;/etc/gshadow
3、删除/home/username;/var/spool/mail/username
4、删除该用户曾经来该Liunx中创建的文件
	find进行搜索，先搜索，在使用userdel
-r   连同家目录和邮箱一起删除

