# Linux 常用命令学习

## 1.which 命令

命令格式：`which` 可执行文件名称

命令作用：`which`指令会在`PATH`变量指定的路径中，搜索某个系统命令的位置，并且返回第一个搜索结果

#### 3．命令参数

- `-n` -　指定文件名长度，指定的长度必须大于或等于所有文件中最长的文件名。
- `-p` - 与`-n`参数相同，但此处的包括了文件的路径。
- `-w` - 指定输出时栏位的宽度。
- `-V` - 显示版本信息

查看PATH路径 `echo $PATH`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426143006233.png" alt="image-20230426143006233" style="zoom:80%;" />

#### 命令示范

- 查找文件、显示命令路径

  <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426143325698.png" alt="image-20230426143325698" style="zoom:50%;" />

- 找出 adduser 这个命令<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426143406795.png" alt="image-20230426143406795" style="zoom:50%;" />

---

## 2. whereis 命令

`whereis`命令只能用于程序名的搜索，而且只搜索二进制文件(参数-b)、man说明文件(参数-m)和源代码文件(参数-s)。如果省略参数，则返回所有信息。

> 和`find`相比，`whereis`查找的速度非常快，这是因为linux系统会将 系统内的所有文件都记录在一个数据库文件中，当使用`whereis`和下面即将介绍的`locate`时，会从数据库中查找数据，而不是像`find`命令那样，通 过遍历硬盘来查找，效率自然会很高。
> 但是该数据库文件并不是实时更新，默认情况下时一星期更新一次，因此，在用`whereis`和`locate` 查找文件时，有时会找到已经被删除的数据，或者刚刚建立文件，却无法查找到，原因就是因为数据库文件没有被更新。 

命令格式：`whereis [-bmsu] [BMS 目录名 -f ] 文件名`

#### 命令参数

- -bmsu类参数
- - `-b` - 定位可执行文件。
  - `-m` - 定位帮助文件。
  - `-s` - 定位源代码文件。
  - `-u` - 搜索默认路径下除可执行文件、源代码文件、帮助文件以外的其它文件。

- `-B` - 指定搜索可执行文件的路径。
- `-M` - 指定搜索帮助文件的路径。
- `-S` - 指定搜索源代码文件的路径

#### 命令示范：

- 找到bash文件相关的文件<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426151636401.png" alt="image-20230426151636401" style="zoom:50%;" />

- 只将二进制文件查找出来<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426151857087.png" alt="image-20230426151857087" style="zoom:50%;" />

---

## 3. locate命令

> `locate` 让使用者可以很快速的搜寻档案系统内是否有指定的档案。其方法是先建立一个包括系统内所有档案名称及路径的数据库，之后当寻找时就只需查询这个数据库，而不必实际深入档案系统之中了。在一般的 distribution 之中，数据库的建立都被放在 crontab 中自动执行。

命令格式：`Locate [选择参数] [样式]`

`locate`命令可以在搜寻数据库时快速找到档案，数据库由`updatedb`程序来更新，updatedb是由`cron daemon`周期性建立的，`locate`命令在搜寻数据库时比由整个由硬盘资料来搜寻资料来得快，但较差劲的是`locate`所找到的档案若是最近才建立或 刚更名的，可能会找不到，在内定值中，updatedb每天会跑一次，可以由修改`crontab`来更新设定值。(`etc/crontab`)

#### 命令参数

- `-e` - 将排除在寻找的范围之外。
- `-1` - 如果是`1`。则启动安全模式。在安全模式下，使用者不会看到没有权限无法看到的档案。这会使速度减慢，因为 `locate` 必须至实际的档案系统中取得档案的权限资料。
- `-f` - 将特定的档案系统排除在外，例如没有道理要把 `proc` 档案系统中的档案放在资料库中。
- `-q`  安静模式，不会显示任何错误讯息。
- `-n` 至多显示 `n` 个输出。
- `-r` 使用正规运算式 做寻找的条件。
- `-o` 指定资料库存的名称。
- `-d` 指定资料库的路径
- `-h` 显示辅助讯息
- `-V` 显示程式的版本讯息

#### 命令示例

- 查找和pwd相关的所有文件 <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426153552660.png" alt="image-20230426153552660" style="zoom:50%;" />

- 搜索etc目录下所有以sh开头的文件<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426153711148.png" alt="image-20230426153711148" style="zoom:50%;" />

- 搜索etc目录下，所有以i开头的文件<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426153948485.png" alt="image-20230426153948485" style="zoom:50%;" />

----

## 4.find命令

Linux中的**find**命令在目录结构中搜索文件，并执行指定的操作

> Linux下`find`命令提供了相当多的查找条件，功能很强大。由于`find`具有强大的功能，所以它的选项也很多，其中大部分选项都值得我们花时间来了解一下。即使系统中含有网络文件系统( NFS)，`find`命令在该文件系统中同样有效，只要你具有相应的权限。 在运行一个非常消耗资源的`find`命令时，很多人都倾向于把它放在后台执行，因为遍历一个大的文件系统可能会花费很长的时间(这里是指30G字节以上的文件系统)。

命令格式： `find pathname -options [-print -exec -ok ...]`（options为命令选项，后者为命令参数）

#### 命令参数

- `pathname` - find命令所查找的目录路径。例如用.来表示当前目录，用/来表示系统根目录。 
- `-print` - find命令将匹配的文件输出到标准输出。 
- `-exec` - find命令对匹配的文件执行该参数所给出的shell命令。相应命令的形式为’command’ {  } \;，注意{   }和\；之间的空格。 
- `-ok` - 和`-exec`的作用相同，只不过以一种更为安全的模式来执行该参数所给出的shell命令，在执行每一个命令之前，都会给出提示，让用户来确定是否执行。

#### 命令选项

- `-name`   按照文件名查找文件。
- `-perm`   按照文件权限来查找文件。
- `-user`   按照文件属主来查找文件。
- `-group`  按照文件所属的组来查找文件。
- `-mtime -n +n`  按照文件的更改时间来查找文件， - n表示文件更改时间距现在n天以内，+ n表示文件更改时间距现在n天以前。`find`命令还有`-atime`和`-ctime` 选项，但它们都和`-m time`选项。
- `-nogroup`  查找无有效所属组的文件，即该文件所属的组在`/etc/groups`中不存在。
- `-nouser`   查找无有效属主的文件，即该文件的属主在`/etc/passwd`中不存在。
- `-newer file1 ! file2`  查找更改时间比文件`file1`新但比文件`file2`旧的文件。
- `-type`  查找某一类型的文件，诸如：
  - `b` - 块设备文件。
  - `d` - 目录。
  - `c` - 字符设备文件。
  - `p` - 管道文件。
  - `l` - 符号链接文件。
  - `f` - 普通文件。
- `-size n：[c]` 查找文件长度为`n`块的文件，带有`c`时表示文件长度以字节计。`-depth`：在查找文件时，首先查找当前目录中的文件，然后再在其子目录中查找。
- `-fstype`：查找位于某一类型文件系统中的文件，这些文件系统类型通常可以在配置文件`/etc/fstab`中找到，该配置文件中包含了本系统中有关文件系统的信息。
- `-mount`：在查找文件时不跨越文件系统`mount`点。
- `-prune`  使用这一选项可以使`find`命令不在当前指定的目录中查找，如果同时使用`-depth`选项，那么`-prune`将被`find`命令忽略。
- `-follow`：如果find命令遇到符号链接文件，就跟踪至链接所指向的文件。
- `-cpio`：对匹配的文件使用`cpio`命令，将这些文件备份到磁带设备中。

另外,下面三个的区别:

- `-amin n`   查找系统中最后`N`分钟访问的文件
- -`atime n`  查找系统中最后`n*24`小时访问的文件
- `-cmin n`   查找系统中最后`N`分钟被改变文件状态的文件
- `-ctime n`  查找系统中最后`n*24`小时被改变文件状态的文件
- `-mmin n`   查找系统中最后`N`分钟被改变文件数据的文件
- `-mtime n`  查找系统中最后`n*24`小时被改变文件数据的文件

#### 使用实例 

- 查找指定时间内修改过的文件 `find 指定查找路径 -atime -2`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426161534532.png" alt="image-20230426161534532" style="zoom:50%;" />

- 根据关键字查找 `find 指定查找路径 -name 文件名`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426161854282.png" alt="image-20230426161854282" style="zoom:50%;" />

- 按照目录或文件的权限来查找文件`find 文件查找路径 -perm 777`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426161947335.png" alt="image-20230426161947335" style="zoom:50%;" />

- 按类型查找指定文件名 `find 指定查找目录 -type f -name “文件名”`（可以不使用-name）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426162359747.png" alt="image-20230426162359747" style="zoom:50%;" />

- 查找当前所有目录并排序`find 指定路径 -type d | sort`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426162620915.png" alt="image-20230426162620915" style="zoom:50%;" />

- 按大小查找文件 `find 查找路径 -size -10c -print`（-代表小于10个字节，+代表大于10个字节，-print输出到屏幕上）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426162934548.png" alt="image-20230426162934548" style="zoom:50%;" />

---

## 4.find—exec参数

**find**是很常用的一个Linux命令，但是一般查找出来的并不仅仅是看看而已，还会有进一步的操作，这个时候`exec`的作用就显现出来了。
`exec`解释：

- `-exec`  参数后面跟的是`command`命令，它的终止是以;为结束标志的，所以这句命令后面的分号是不可缺少的，考虑到各个系统中分号会有不同的意义，所以前面加反斜杠。
  `{}`花括号代表前面`find`查找出来的文件名。

命令格式 `find 文件路径 选项  -exec 其他命令 {} \;`

> 在使用`find`时，只要把想要的操作写在一个文件里，就可以用`exec`来配合`find`查找，很方便的。在有些操作系统中只允许`-exec`选项执行诸如`ls`或`ls -l`这样的命令。大多数用户使用这一选项是为了查找旧文件并删除它们。建议在真正执行`rm`命令删除文件之前，最好先用ls命令看一下，确认它们是所要删除的文件。 `exec`选项后面跟随着所要执行的命令或脚本，然后是一对`{ }`，一个空格和一个`\`，最后是一个分号。为了使用exec选项，必须要同时使用print选项。如果验证一下find命令，会发现该命令只输出从当前路径起的相对路径及文件名。

#### 使用实例 

- ls -l命令放在find命令的-exec选项中（示例为找到名有test的文件并详细罗列）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426164603381.png" alt="image-20230426164603381" style="zoom:50%;" />

- 在目录中查找更改时间在n日以前的文件并删除它们（太危险了，不做演示）
- 使用less查看当前目录的所有txt文件（有很多，请按狂按q退出）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426165000785.png" alt="image-20230426165000785" style="zoom:70%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230426165046209.png" alt="image-20230426165046209" style="zoom:33%;" />

---

## 4.find -xargs参数

> `find`命令把匹配到的文件传递给`xargs`命令，而`xargs`命令每次只获取一部分文件而不是全部，不像`-exec`选项那样。这样它可以先处理最先获取的一部分文件，然后是下一批，并如此继续下去。 

在Linux中，find命令可以用于查找文件，而-exec和xargs参数都可以用于在找到文件后执行命令。-exec参数会为每个匹配的文件执行一次命令，而xargs会将所有匹配的文件作为参数传递给一次命令。如果要执行的命令需要多个参数，则必须使用xargs。如果要执行的命令只需要一个参数，则可以使用-exec或xargs。使用-exec参数时，必须在命令行中指定要执行的命令，而使用xargs时，必须将要执行的命令放在管道中。

### 使用示例

- 查找系统中的每一个普通文件，然后使用xargs命令来测试它们分别属于哪类文件(`find . -type f -print | xargs file`)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230428144705477.png" alt="image-20230428144705477" style="zoom:50%;" />

(非常长，但是看得出来是一下子全部放出来的)
