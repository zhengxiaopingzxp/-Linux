## linux查看文件的几种方法
#### linux有几种方法可以查看文件：
#### 查看文件-cat
> - A ：整合命令-vET

![查看文件.png](https://upload-images.jianshu.io/upload_images/7563229-2561e7af4aa75b41.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> - b：列出行号，但是空白行不标志行号

![查看列数.png](https://upload-images.jianshu.io/upload_images/7563229-3a1a17027cbb8335.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


>- E：将结尾的断行字符（$）显示出来
>- n：列出行号，空白行也会标志行号
>- T：将tab按键以^I显示
>- v：列出一些看不来的特殊字符

#### 查看文件-nl
>##### -b:
> - ba //无论是否有空行，都列出行号
> - bt //如果有空行，则不列出行号（默认）

![用nl查看文件](https://upload-images.jianshu.io/upload_images/7563229-925f00ee81e1b387.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>##### -n:
> - nln //行号在屏幕最左方
>- nrn //行号在屏幕最右方，前面不加0
>- nrz //行号在屏幕最右方，前面加0

![用nl查看文件](https://upload-images.jianshu.io/upload_images/7563229-5c89f4239ad3309e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


>  **-w：**缩进多少位


#### 查看文件-more
> more（一页一页翻动）
 空格：向下翻一页
 回车：向下翻一行
/字符串：所搜
:f：立刻显示文件名和行数
b：翻到第一页
q：离开

![more查看文件](https://upload-images.jianshu.io/upload_images/7563229-400166c9726df24f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 查看文件-less

> less（一页一页翻动）
空格：向下翻动一页
pagedown：向下翻动一页
pageup：向上翻动一页
n：重复前一个搜索
N：反方向重复前一个搜索
q：退出

#### 查看文件
- **head,tail：**显示文件头或尾几行
- **-n：**指定显示几行。默认是10行

- **日志文件：**/var/log/messages。我们只需要看尾部的最新的几行即可

- **wc：**显示文件的行数，数字，字节
- **-c：**只显示字节
- **-w：**只显示字数。一个字被定义为由空白、空格或换行字符分隔的字符串。
- **-l：**只显示行

![image.png](https://upload-images.jianshu.io/upload_images/7563229-2508c2a949583e5a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
#### 知识的补充：
###### Vim编辑器
![编辑器命令](https://upload-images.jianshu.io/upload_images/7563229-d9cfd32d2e34aae3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
