## Linux-基本操作-2-权限
![权限](https://upload-images.jianshu.io/upload_images/7563229-77bde0a1577d78cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![对应上面的权限](https://upload-images.jianshu.io/upload_images/7563229-db9d2c95fa66755a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##### 文件的属性：
> d：表示目录
-：表示文件
l：连接文件
b：设备文件，提供存储的接口设备
c：设备文件，提供串行的接口设备--键盘，鼠标。

![查看权限](https://upload-images.jianshu.io/upload_images/7563229-d4af240a28af7124.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 文件的权限：所有者，所属组，其他人
> rwx，读、写、执行，没有权限就是-

- 第一个组rwx：文件所有者的权限
- 第二个组rwx：文件所属组的权限
- 第三个组rwx：文件其他人的权限

##### 目录的权限：
> - r：具有读取目录结构列表的权限，可以查看目录下有哪些文件

> - w：该权限对于目录来说是很大的，
	1、可以在该目录下新建新的文件和目录
	2、可以删除已经存在的文件和目录
	3、将已经存在的文件和目录重命名
	4、移动该目录内的文件和目录的位置

>-  x：是否可以进入该目录
***

> - **chown：**修改文件的拥有者，前提是要有该拥有者
> - chown 拥有者 文件/目录
- -R 递归修改
![修改权限](https://upload-images.jianshu.io/upload_images/7563229-f8e90752d7883060.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![转让权限](https://upload-images.jianshu.io/upload_images/7563229-b99c81ce3eeb0387.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![转让权限成功](https://upload-images.jianshu.io/upload_images/7563229-0100dbb299a5d998.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> - **chgrp：**修改文件所属组，前提是要有该组。
>-  -R 递归修改

> - **chmod：修改拥有者和所属组的权限**
>- 加减法：u/g/o   +/-/=   r/w/x
>- 数字法：r=4，w=2，x=1
  rwx=4+2+1=7
  rw-=4+2=6
  r--=4
  r-x=4+1=5

![原先权限](https://upload-images.jianshu.io/upload_images/7563229-bfad515d68414ccf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![追加权限](https://upload-images.jianshu.io/upload_images/7563229-f76ca46c5d01139c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
