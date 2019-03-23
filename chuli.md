## Linux文件处理
#### Linux文件处理命令（记住：是文件哦~）
> ~：当前登录用户所在目录（家目录）
> *#*：超级用户的提示符
> $：普通用户的提示符

###### 查询目录中的内容：ls
- (ls 一般和下面的常见命令搭配使用，比如 ls-l 就是查看文件的具体信息。)
- 下面的常见命令也可以两个一起使用。比如 ls- la ls-lh
![常见命令.png](https://upload-images.jianshu.io/upload_images/7563229-67a4aa3a4543a285.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- **例子**
![查看文件.png](https://upload-images.jianshu.io/upload_images/7563229-5b42b251ae31f9de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> tmp表示临时文件，一般做实验或者自己练习的时候就可以在这个目录下进行。


###### 切换所在目录：cd 
![路径的切换](https://upload-images.jianshu.io/upload_images/7563229-ff3a1891bdfea8c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 【1】相对路径：参照当前所在目录，进行查找。如：cd ../usr/local/src
 - 【2】绝对路径：从根目录开始指定，逐级递归查找（在任何目录下都能进入指定位置）
 如：cd /etc/sysconfig/network-scripts/
***

#### Linux目录处理命令：（这里是目录的了）
> ###### 知识的补充：
> 创建一个新的文件：touch
> 创建一个新的目录：mkdir
> 删除空目录：rmdir 
- 复制文件：cp 
- 移动文件：mv
- 删除文件：rm  （后面加上 **-f** 表示强制删除）
- 创建目录：cp -r
- 移动目录：mv
- 删除目录：rm（后面加上 **-rf**  表示强制迭代删除，即可以删除目录中的目录中的文件。）

![文件处理命令.png](https://upload-images.jianshu.io/upload_images/7563229-cc56168c0d2ed3aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Linux链接命令(ln)
*注：此部分是借鉴转载作者[Fighting_001](https://www.jianshu.com/p/b11033d70cc7)，若有侵权，立删*
###### A硬链接`    （格式）ln [源文件] [目标文件]`

> 同一存储分区位置同一个程序文件，创建了多个硬链接文件（平级），拥有相同的i节点编号、block块，数据块中保存有源文件的文件名、i节点编号、实际的文件数据，这些硬链接都指向该程序文件。

①修改任一硬链接文件的其中的内容，其他的相应硬链接的内容也同步变化
②删除or改名其中的任一硬链接文件，其他平级的硬链接文件并不会受影响
③通过i节点编号，可识别判断平级的不同硬链接文件（拥有相同的i节点）
④不能跨分区、不能针对目录使用

如：ln AAA/001.txt BBB/001_hard.txt

![image](//upload-images.jianshu.io/upload_images/4866277-37194a8c9ca4692f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650/format/webp)

##### B软链接                      `ln -s [源文件] [目标文件]`

> 类似快捷方式，软链接拥有属于自己不同的i节点、Block块，但其数据块中只保存有源文件的文件名、i节点编号，并没有实际的文件数据。

①软链接文件权限都为：rwxrwxrwx（实际权限由源文件权限决定）
②修改任一软链接文件，其他的对应的软链接文件都会改变
③若删除源文件，则软链接就不能使用
④若创建软链接，则需要写绝对路径，否则可能跨目录操作会报错，创建软链接后所指向的源文件会出现红色背景的标识（硬链接无此限制）

![文件](https://upload-images.jianshu.io/upload_images/7563229-77f9d4e8f7a9c969.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
