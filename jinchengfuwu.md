## Linux-基本操作-3进程和服务
#### Linux中的进程
- 进程：已经启动的可执行程序的运行实力
>1、PID：进程的ID（每一个新进程都有一个唯一的PID）
2、PPID：父进程的ID
3、任何一个进程都可以创建一个子进程
4、在redhat 7以上，所有进程的父进程：systemd
5、 在redhat 5,6中，所有进程的父进程：init

- ps 用于显示当前进程状态
常用选项
> -aux：列出所有进程
-ef：列出所有进程
-l：列出和当前用户有关的进程
-u 用户：查看某一用户的进程状态
 top 可以查看实时的进程状态

![查看进程](https://upload-images.jianshu.io/upload_images/7563229-3090534da38229cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


- C、运行中：
> R:该进程正在运行或等待运行
睡眠：
S:正在休眠但是可以被唤醒
D:正在休眠，而且不可以被唤醒，该进程被中断，可能会导致设备的异常状态
K:正在休眠，而且不可以被唤醒，该进程可以被中断。
已停止：
T:进程被停止，但是可以通过其他进程来进行恢复
T:正在被调试的进程
僵停：
Z:子进程在退出时向父进程发出信号，除PID外，所有资源全部释放
X:父进程获取了子进程的结构，子进程可以完全释放，该状态进程中是看不到的

- D、进程优先级
1、< 高优先级
2、n   低优先级3、s   包含子进程4、+   位于后台的进程组
 
- E、ps –aux参数解释
>1、%CPU: 占用的 CPU 使用率 2、%MEM: 占用的记忆体使用率 3、VSZ: 占用的虚拟记忆体大小 4、RSS: 占用的记忆体大小 5、TTY: 终端的次要装置号码 (minor device number of tty) 6、STAT: 该行程的状态
7、START: 行程开始时间 8、TIME: 执行的时间
9、COMMAND:所执行的指令

##### linux中的会话和作业

- 进程：Linux自身运行的独立的程序


     1、交互进程：由一个shell启动的进程，可以再前台运行，也可以在后台运行

	 2、批处理进程：是一个进程序列，和终端没有联系

	3、监控进程（守护进程）：Linux系统启动时，启动的进程，并且在后台运行

- **作业：**一个正在执行的进程，而且作业可以包含一个或多个进程。

> 作业控制：控制正在运行的进程的行为。如：挂起一个进程，等一会在执行。这样用户就可以再多个作业之间切换。



     &：在命令后面使用该符号，可以让命令在后台执行
     jobs：可以查看正在后台运行的作业
    sleep 10000    延迟几秒
	ctrl+c：中断
	ctrl+z：挂起

**案例：**date ; sleep 5 ; date
![延迟](https://upload-images.jianshu.io/upload_images/7563229-9be3f2dc14158364.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片.png](https://upload-images.jianshu.io/upload_images/7563229-635cd476646b541f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

######  jobs：查看当前后台的作业状态

> -l：除了列出作业号外，同时列出PID
>- -r：列出仅仅在后台运行的作业
>- -s：列出仅仅在后台暂停的作业

![jobs命令](https://upload-images.jianshu.io/upload_images/7563229-1a984b3c1be8308e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### linux中的会话和作业（2）

>- fg：将后台的命令调到前台来继续执行，不能放回后台了
		%作业编号
>- bg：将后台暂停的命令继续执行
		 %作业编号
>- ps –j 显示当前作业进程信息
>- TGID：线程组ID号
>- SID：会话ID号

![图片.png](https://upload-images.jianshu.io/upload_images/7563229-12b0a3b20b2faf77.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### Linux中断进程
- **信号：**传递给Linux进程的操作
> kill –l 显示可以传递给Linux进程的所有信号

- **常用：**



    kill -9 PID  杀死一个进程—强制
    kill -15 PID 正常的方式终止一个进程
    kill -2  可以control+c的操作是一样的
##### 控制服务和守护进程(1)
- systemd：是所有进程的父进程（Linux内核3.0以上版本）
- systemctl：用户管理各种类型的- systemd对象，这些对象称为：单元
> 常用的单元：.service（服务单元）.socket（套接字）.path（路径单元）

    ssh：是一个协议		sshd：是一个进程：用于链接访问（用于客户端和服务端的访问）

- **systemctl status sshd.service 显示中有几个关键字:**
![systemctl](https://upload-images.jianshu.io/upload_images/7563229-987a79666efc107a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> - loaded：单元配置文件以处理
>- active（running）：正在运行
 >- active（exited）：配置成功
 >- active（waiting）：运行中，但正在等待事件		
 >- inactive：不在运行	enable：开机自启动
 >- disabled：开机不自启	static：无法启动，但可以通过某一个已经启动的单元来启动

##### 控制服务和守护进程(2)

    start：在系统中启动一项服务
    stop：等待程序需处理完毕后再stop。
    restart：直接关闭程序 在开启
    reload：重新加载配置文件，进程暂停，然后把配置文件加载进去后，继续执行后续操作。进程的PID不会发生改变
    enable：设置开机自启
    disable：关闭开机自启
    status：查看某一单元的状态

![控制](https://upload-images.jianshu.io/upload_images/7563229-36e13d292e46a504.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)





