# Linux 常用命令

## 1.tar 命令 打包解压

> 首先要弄清两个概念：打包和压缩。打包是指将一大堆文件或目录变成一个总的文件；压缩则是将一个大的文件

Linux下最常用的打包程序就是`tar`了，使用`tar`程序打出来的包我们常称为`tar`包，`tar`包文件的命令通常都是以`.tar`结尾的。生成`tar`包后，就可以用其它的程序来进行压缩 

命令格式 `tar[必要参数][选择参数][文件]`

#### 命令参数

必要参数有如下：

- `-A` 新增压缩文件到已存在的压缩
- `-B` 设置区块大小
- `-c` 建立新的压缩文件
- `-d` 记录文件的差别
- `-r` 添加文件到已经压缩的文件
- `-u` 添加改变了和现有的文件到已经存在的压缩文件
- `-x` 从压缩的文件中提取文件
- `-t` 显示压缩文件的内容
- `-z` 支持gzip解压文件
- `-j` 支持bzip2解压文件
- `-Z` 支持compress解压文件
- `-v` 显示操作过程
- `-l` 文件系统边界设置
- `-k` 保留原有文件不覆盖
- `-m` 保留文件不被覆盖
- `-W` 确认压缩文件的正确性

**可选参数如下：**

- `-b` 设置区块数目
- `-C` 切换到指定目录
- `-f` 指定压缩文件
- `--help` 显示帮助信息
- `--version` 显示版本信息

#### 常见解压/压缩命令

- **tar文件格式**
  解包：`tar xvf FileName.tar`
  打包：`tar cvf FileName.tar DirName`
  (注：`tar`是打包，不是压缩！)
- **.gz文件格式**
  解压1：`gunzip FileName.gz`
  解压2：`gzip -d FileName.gz`
  压缩：`gzip FileName`
- **.tar.gz 和 .tgz**
  解压：`tar zxvf FileName.tar.gz`
  压缩：`tar zcvf FileName.tar.gz DirName`
- **.bz2文件格式**
  解压1：`bzip2 -d FileName.bz2`
  解压2：`bunzip2 FileName.bz2`
  压缩： `bzip2 -z FileName`
- **.tar.bz2文件格式**
  解压：`tar jxvf FileName.tar.bz2`
  压缩：`tar jcvf FileName.tar.bz2 DirName`
- **.bz文件格式**
  解压1：`bzip2 -d FileName.bz`
  解压2：`bunzip2 FileName.bz`
  压缩：未知
- **.tar.bz文件格式**
  解压：tar jxvf FileName.tar.bz
  压缩：未知
- **.Z文件格式**
  解压：uncompress FileName.Z
  压缩：compress FileName
- **.tar.Z文件格式**
  解压：tar Zxvf FileName.tar.Z
  压缩：tar Zcvf FileName.tar.Z DirName
- **.zip文件格式**
  解压：unzip FileName.zip
  压缩：zip FileName.zip DirName
- **.rar**
  解压：rar x FileName.rar
  压缩：rar a FileName.rar DirName

#### 示例 

- 将文件全部压缩为tar包 `tar -cvf  目标文件.tar 源文件123`（可用-z支持gzip解压|可用-j支持bzip2解压文件）(c建立新的压缩文件,v显示操作过程,f指定压缩文件)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425174236260.png" alt="image-20230425174236260" style="zoom:50%;" />

- 查阅上述 tar包内有哪些文件  `tar -ztvf 打包文件`（t显示压缩文件的内容）

![image-20230425175714559](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425175714559.png)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425175725063.png" alt="image-20230425175725063" style="zoom:45%;" />

- 将tar包解包 `tar -zxvf 文件名` （x为从压缩的文件中提取文件）

  ![image-20230425181326440](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425181326440.png)

- 只将 /tar 内的 部分文件解压出来 `tar -zxvf 文件名 文件名中的文件`![image-20230425181608072](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425181608072.png)

## 2.gzip命令

`gzip`是在Linux系统中经常使用的一个对文件进行压缩和解压缩的命令，既方便又好用。`gzip`不仅可以用来压缩大的、较少使用的文件以节省磁盘空间，还可以和`tar`命令一起构成Linux操作系统中比较流行的压缩文件格式。  

> 据统计，`gzip`命令对文本文件有`60%～70%`的压缩率。 

命令格式：`gzip 参数 文件或目录`

#### 命令参数

- `-a`或`--ascii` 　使用ASCII文字模式。 
- `-c`或`--stdout`或`--to-stdout` 　把压缩后的文件输出到标准输出设备，不去更动原始文件。 
- `-d`或`--decompress`或`----uncompress` 　解开压缩文件。 
- `-f`或`--force` 　强行压缩文件。不理会文件名称或硬连接是否存在以及该文件是否为符号连接。 
- `-h`或`--help` 　在线帮助。 
- `-l`或`--list` 　列出压缩文件的相关信息。 
- `-L`或`--license` 　显示版本与版权信息。 
- `-n`或`--no-name` 　压缩文件时，不保存原来的文件名称及时间戳记。 
- `-N`或`--name` 　压缩文件时，保存原来的文件名称及时间戳记。 
- `-q`或`--quiet` 　不显示警告信息。 
- `-r`或`--recursive` 　递归处理，将指定目录下的所有文件及子目录一并处理。 
- `-S`<压缩字尾字符串>或`----suffix`<压缩字尾字符串> 　更改压缩字尾字符串。 
- `-t`或`--test` 　测试压缩文件是否正确无误。 
- `-v`或`--verbose` 　显示指令执行过程。 
- `-V`或`--version` 　显示版本信息。 
- `-num` 用指定的数字`num`调整压缩的速度，`-1`或`--fast`表示最快压缩方法(低压缩比)，`-9`或`--best`表示最慢压缩方法(高压缩比)。系统缺省值为`6`。

#### 使用实例

- 把test4目录下的每个文件压缩成.gz文件（居然会忽略文件夹）![image-20230425184451349](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425184451349.png)

- 解压文件并列出详细信息 `gzip -dv *`(d是解压缩文件，v是显示指令执行过程)<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425184743477.png" alt="image-20230425184743477" style="zoom:50%;" />

- 详细显示例1中每个压缩的文件的信息，并不解压 `gzip -l *`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425185113455.png" alt="image-20230425185113455" style="zoom:50%;" />

- 压缩一个tar备份文件，此时压缩文件的扩展名为.tar.gz     

  指令：`gzip -r log.tar` （-r 递归处理，将指定目录下的所有文件及子目录一并处理。）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425185449481.png" alt="image-20230425185449481" style="zoom:50%;" />

- 递归的压缩目录 

  指令：`gzip -rv 目录`

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425185846029.png" alt="image-20230425185846029" style="zoom:50%;" />

（我压缩了当前目录，由于是递归压缩，即每个目录下的都被压缩了）

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425185926661.png" alt="image-20230425185926661" style="zoom:50%;" />

- 递归的解压缩<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425190159550.png" alt="image-20230425190159550" style="zoom:45%;" />
