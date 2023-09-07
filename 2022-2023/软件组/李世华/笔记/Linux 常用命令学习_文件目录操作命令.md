# Linux 常用命令学习

## 1.ls命令（list directory contents)

#### 语法 ls [-alrtAFR] [name...]

列出根目录（/）的文件

![image-20230423184425255](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423184425255.png)

可以和其他参数搭配

![image-20230423184554491](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423184554491.png)

### 常用搭配参数

- ls -a 显示所有文件及目录 (**.** 开头的隐藏文件也会列出)

![image-20230423184031143](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423184031143.png)

- ls -l 以长格式显示当前目录中的文件和目录![image-20230423184827985](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423184827985.png)
- ls -d 只列出目录（不递归列出目录内的文件）（有点奇怪，好像很多地方列出目录只有一个.）（存疑）![image-20230423185005948](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423185005948.png)
- ls -r 倒序显示文件和目录![image-20230423185132434](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423185132434.png)
- ls -t 将按照修改时间排序，最新的文件在最前面。

![image-20230423185219727](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423185219727.png)

- ls -A 在a的基础上不列出 .（当前目录）与 .. （父目录）

![image-20230423185836251](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423185836251.png)

- ls -R 递归显示目录中的所有文件和子目录（非常恐怖，兄弟）

![image-20230423190831285](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423190831285.png)

---

## 2.cd命令 changeDirectory

使用格式：cd [dirName]（c盘d盘在mnt，牢记啊）

![image-20230423191044473](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423191044473.png)

- cd ~ 跳回到自己的home目录

![image-20230423191254211](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423191254211.png)

- cd .. 跳回到前一层

![image-20230423191428511](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423191428511.png)

- cd ../..跳回到目录的前两层![image-20230423191538069](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423191538069.png)

---

## 3.pwd命令（print working directory）

*执行 pwd 指令可立刻得知目前所在的工作目录的绝对路径名称*

语法：pwd [--help][--version]

![image-20230423192247328](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423192247328.png)-L 目录连接链接时，输出连接路径
-P 输出物理路径（好像没体现出区别来)

---

## 4.mkdir命令（make directory）

*该命令用于创建目录*

语法：mkdir [选项] 名称                             -p 确保目录名称存在，不存在的就建一个

当然可以直接mkdir一个

![image-20230423193051983](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423193051983.png)

- mkdir -v 文件名   //每次创建都显示创建信息![image-20230423193938741](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423193938741.png)

- mkdir -m  权限数字 文件名 //创建时设定文件权限![image-20230423194233077](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423194233077.png)

示例为所有用户可读写的权限

---

*关于权限信息*

*权限可以用数字表示，其中 `4` 表示读取权限，`2` 表示写入权限，`1` 表示执行权限。这些数字可以相加以表示多种权限。例如，`7`（即 `4 + 2 + 1`）表示读取、写入和执行权限。*

*因此，当使用 `chmod` 命令更改权限时，可以使用三位数字来表示所有者、所属组和其他用户的权限。例如，要将目录 `test3中` 的所有者权限更改为读取、写入和执行，所属组权限更改为读取和执行，其他用户权限更改为只读，则可以使用以下命令：`chmod 754 test3中`*

---

## 5.rm命令（remove）

*`rm`是一个危险的命令，使用的时候要特别当心*

格式 `rm 选项 文件`

- -f 强制删除，不给出提示(force)
- -i 交互式确认 （interactive）（y即是确认）
- -r -R,删除列出的全部目录与子目录
- -v 详细显示进行的步骤

#### 删除任何.txt文件，并且删除前逐一询问 rm -i *.txt

![image-20230423195825398](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423195825398.png)

#### 删除以 “新开头的文件”   rm 新*（*是通配符）

![image-20230423201324804](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423201324804.png)

---

## 6.rmdir 命令

从一个目录中删除一个或多个子目录项，删除某目录时也必须具有对其父目录的写权限。

*该命令的功能是删除空目录，一个目录被删除之前必须是空的*

`- p`递归删除目录dirname，当子目录删除后其父目录为空时，也一同被删除。如果整个路径被删除或者由于某种原因保留部分路径，则系统在标准输出上显示相应的信息

#### 展示一下，使用-p删除一个空目录使得父目录为空后也一并删除的操作

首先我们看到这里是ooo下有一个空目录this![image-20230423213015603](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423213015603.png)

我们返沪test界面![image-20230423213044725](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423213044725.png)

然后使用`rmdir -p ooo/this`

![image-20230423213216201](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423213216201.png)

结果就为ooo也被删除了![image-20230423213315695](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230423213315695.png)

---

## 7.mv 命令（move）

可以用来移动文件或者将文件改名(move (rename) files)，是Linux系统下常用的命令，经常用来备份文件或者目录。

格式:`mv [选项] 源文件或目录 目标文件名或目录`

- 当第二个参数类型是**文件**时，`mv`命令完成**文件重命名**，此时，源文件只能有一个(也可以是源目录名)，它将所给的**源文件或目录**重命名为**给定的目标文件名**。 
- 当第二个参数是**已存在的目录名称**时，**源文件**或**目录参数**可以有多个，`mv`命令将各参数指定的**源文件**均移至**目标目录**中。*在跨文件系统移动文件时，`mv`先拷贝，再将原有文件删除，而链至该文件的链接也将丢失。*

#### 命令参数

- `-b`：若需覆盖文件，则覆盖前先行备份。
- `-f` ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖；
- `-i` ：若目标文件 (destination) 已经存在时，就会询问是否覆盖
- `-u` ：若目标文件已经存在，且 source 比较新，才会更新(update)
- `-t`  ： —target-directory=DIRECTORY move all SOURCE arguments into DIRECTORY，即指定mv的目标目录，该选项适用于移动多个源文件到一个目录的情况，此时目标目录在前，源文件在后。

#### 示例

- 给文件/目录改名

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424160752585.png" alt="image-20230424160752585" style="zoom:65%;" />

- 移动文件（使用绝对路径会好一些）

![image-20230424161009451](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424161009451.png)

- 移动一个目录到另一个目录

  ![image-20230424161438525](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424161438525.png)

- 使用绝对路径移动目录

![image-20230424161606262](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424161606262.png)

- 使用  指令-t进行移动，即目录在前，移动文件在后 

![image-20230424163338132](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424163338132.png)

- 移动当前文件夹下的所有文件到上一级目录 `mv * ../`

![image-20230424163509981](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424163509981.png)

- 将当前文件夹的所有文件移动到另一文件夹 `mv * 目标目录`

  ![image-20230424163715916](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424163715916.png)

- 由此衍生，把一个目录的所有文件移动另一个目录去

  ![image-20230424164047726](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424164047726.png)

---

## 8. touch命令

*linux中的**touch**命令不常用，一般用来修改文件时间戳，或者新建一个不存在的文件。*

格式：`touch 选项 格式`

- `-a`，`--time=atime`，`--time=access`或`--time=use` 只更改存取时间。

- `-c` 或`--no-create`不建立任何文档。

- `-d` 使用指定的日期时间，而非现在的时间。

- `-f` 此参数将忽略不予处理，仅负责解决BSD版本`touch`指令的兼容性问题。

- `-m` 或`--time=mtime`或`--time=modify` 　只更改变动时间。

- `-r` 把指定文档或目录的日期时间，统统设成和参考文档或目录的日期时间相同。

- `-t` 使用指定的日期时间，而非现在的时间。

### 示例

- 创建一个文件（带后缀名）  `touch 文件名1 文件名2 文件名3` ![image-20230424173157625](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424173157625.png)

- 更新时间戳 `touch -r 文件名1 文件名2 ` （以文件名1时间为标准，使文件名2时间与文件名1时间相同）

  ![image-20230424180324277](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424180324277.png)

- 指定时间戳 `touch -t 时间序列 文件名`

  ![image-20230424181108750](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424181108750.png) 

  ---

  *关于时间序列*

  `-t`  time 使用指定的时间值 time 作为指定文件相应时间戳记的新值。此处的 time 规定为如下形式的十进制数:

  [[CC]YY]MMDDhhmm[.SS]

  CCYY年份，不写则默认为今年（不写CC默认区间为1969到2068）

  MM为月数，DD为天将把年数CCYY限定在`1969--2068`之内．`MM`为月数，`DD`为天数，`hh` 为小时数(几点)，`mm`为分钟数，`SS`为秒数． 

  此处秒的设定范围是`0--61`，这样可以处理闰秒．这些数字组成的时间是环境变量TZ指定的时区中的一个时间。由于系统的限制，早于1970年1月1日的时间是错误的。 

  ---

  ## 9.cat命令

  `cat`命令的用途是连接文件或标准输入并打印。

  cat命令的几个功能

  1. 一次显示整个文件:`cat filename`

  2. 从键盘创建一个文件:`cat > filename` 只能创建新文件,不能编辑已有文件.

  3. 将几个文件合并为一个文件:`cat file1 file2 > file`
     命令参数：

  - `-A`, `--show-all`   等价于 `-vET`
  - `-b`, `--number-nonblank`    对非空输出行编号
  - `-e`                       等价于 `-vE`
  - `-E`, `--show-ends`          在每行结束处显示`$`
  - `-n`, `--number`     对输出的所有行编号,由1开始对所有输出的行数编号
  - `-s`, `--squeeze-blank`  有连续两行以上的空白行，就代换为一行的空白行 
  - `-t`                       与 `-vT` 等价
  - `-T`, `--show-tabs`          将跳格字符显示为 `^I`
  - `-u`                       (被忽略)
  - `-v`, `--show-nonprinting`   使用 `^` 和 `M-` 引用，除了 `LFD` 和 `TAB` 之外

#### 使用示例

- `cat 文件名`(展示文件内的信息)![image-20230424191331847](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424191331847.png)

- ` cat -n 文件1 文件2` 把文件一、二的内容合并并加上行号，然后输出到屏幕上<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424192548282.png" alt="image-20230424192548282" style="zoom:50%;" />
-  ` cat 文件1 文件2 > 新文件名` 创建一个文件，并将文件一文件二的内容合并到该新文件<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424194129201.png" alt="image-20230424194129201" style="zoom:50%;" />

-  `cat -b 文件1 文件2 > 新文件名` 在上面的基础上添加序号<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424194239488.png" alt="image-20230424194239488" style="zoom:50%;" />

- 突发奇想，如果用*.txt呢？（是的，这当然且必须可以）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424194714911.png" alt="image-20230424194714911" style="zoom:67%;" />

- 创建文件 并往其中输入信息 `cat >文件名 <<EOF`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424195305566.png" alt="image-20230424195305566" style="zoom:50%;" />

如果文件名是已存在的，则会进行覆盖并重新<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424195446400.png" alt="image-20230424195446400" style="zoom:50%;" />

---

## 10.nl命令 （Number of Lines）

**nl**命令在linux系统中用来计算文件中行号。**nl**可以将输出的文件内容自动的加上行号！其默认的结果与 `cat -n` 有点不太一样， `nl` 可以将行号做比较多的显示设计，包括位数与是否自动补齐 `0` 等等的功能。

格式：`nl 选项 文件`

- `-b`  ：指定行号指定的方式，主要有两种：

- `-b a` ：表示不论是否为空行，也同样列出行号(类似 `cat -n`)；

- `-b t` ：如果有空行，空的那一行不要列出行号(默认值)；

- `-n`  ：列出行号表示的方法，主要有三种：

- `-n ln` ：行号在萤幕的最左方显示；

- `-n rn` ：行号在自己栏位的最右方显示，且不加 0 ；

- `-n rz` ：行号在自己栏位的最右方显示，且加 0 ；

- `-w` ：行号栏位的占用的位数。

- `-p` 在逻辑定界符处不重新开始计算。

  #### 示例

- 以行号显示文件<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424195806344.png" alt="image-20230424195806344" style="zoom:50%;" />

- `-n ln` ：行号在萤幕的最左方显示<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424200948666.png" alt="image-20230424200948666" style="zoom:50%;" />

- `-n rn` ：行号在自己栏位的最右方显示，且不加 0 <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424201139221.png" alt="image-20230424201139221" style="zoom:50%;" />

- `-n rz` ：行号在自己栏位的最右方显示，且加 0 <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424201211434.png" alt="image-20230424201211434" style="zoom:50%;" />

- `-n rz -w 3`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424201251922.png" alt="image-20230424201251922" style="zoom:50%;" />

---

## 11.more命令

`more`命令，功能类似 `cat` ，`cat`命令是整个文件的内容从上到下显示在屏幕上。`more`会以一页一页的显示方便使用者逐页阅读，而最基本的指令就是按空白键(`space`)就往下一页显示，按 `b` 键就会往回(back)一页显示，而且还有搜寻字串的功能 。`more`命令从前向后读取文件，因此在启动时就加载整个文件。 

命令格式：`more [-dlfpcsu ] [-num ] [+/ pattern] [+ linenum] [file ... ]`

*第一个参数 是填 后6个命令参数；第二个则是 -n,第三个则是 -- 第四个则是+n 第五个是文件名*

#### 命令参数

- `+n`      从笫n行开始显示
- `-n`       定义屏幕大小为`n`行
- `+/pattern` 在每个档案显示前搜寻该字串(pattern)，然后从该字串前两行之后开始显示  
- `-c`       从顶部清屏，然后显示
- `-d`       提示“Press space to continue，’q’ to quit(按空格键继续，按q键退出)”，禁用响铃功能
- `-l`        忽略`Ctrl+l`(换页)字符
- `-p`       通过清除窗口而不是滚屏来对文件进行换页，与-c选项相似
- `-s`       把连续的多个空行显示为一行
- `-u`       把文件内容中的下画线去掉 

#### 操作命令

- `Enter`    向下`n`行，需要定义。默认为`1`行
- `Ctrl+F`   向下滚动一屏
- 空格键  向下滚动一屏
- `Ctrl+B`  返回上一屏
- `=`       输出当前行的行号
- `：f`     输出文件名和当前行的行号
- `V`      调用`vi`编辑器
- `!` 命令, 调用Shell，并执行命令
- `q`   退出more

#### 操作示例（好像只能操作txt的文件）

- more文件

![image-20230424203527008](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424203527008.png)

- more +3 文件 （从第三行开始展示）
- `more +/字串 文件名 ` 从文件中查找第一个出现”`零号`“字符串的行，并从该处前两行开始显示输出

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424204642858.png" alt="image-20230424204642858" style="zoom:50%;" />

- `more -n 文件名`设定每行显示行数![image-20230424205132083](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424205132083.png)

- 列一个目录下的文件，由于内容太多，所以应该学会用more来分页显示。这得和管道 | 结合起来
  命令：

  ```shell
  ls -l  | more -5
  ```

  <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230424205440642.png" alt="image-20230424205440642" style="zoom:50%;" />

---

## 12.less 命令

格式`less 参数 文件`

`less` 与 `more` 类似，但使用 `less` 可以随意浏览文件，而 `more` 仅能向前移动，却不能向后移动，而且 `less` 在查看之前不会加载整个文件。

#### 命令参数

- -b <缓冲区大小> 设置缓冲区的大小

- -e  当文件显示结束后，自动离

- -f  强迫打开特殊文件，例如外围设备代号、目录和二进制文件

- -g  只标志最后搜索的关键词

- -i  忽略搜索时的大小写

- -m  显示类似more命令的百分比

- -N  显示每行的行号

- -o <文件名> 将less 输出的内容在指定文件中保存起来

- -Q  不使用警告音

- -s  显示连续空行为一行

- -S  行过长时间将超出部分舍弃

- -x <数字> 将“tab”键显示为规定的数字空格

- /字符串：向下搜索“字符串”的功能

- ?字符串：向上搜索“字符串”的功能n：重复前一个搜索(与 / 或 ? 有关)

- N：反向重复前一个搜索(与 / 或 ? 有关)

- b  向后翻一

- d  向后翻半页

- h  显示帮助界面

- Q  退出less 命令

- u  向前滚动半页

- y  向前滚动一行

- 空格键 滚动一行

- 回车键 滚动一页

- [pagedown]： 向下翻动一页

- [pageup]：   向上翻动一页

  

#### 示例

- 查看当前文件`less 文件名`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425115022014.png" alt="image-20230425115022014" style="zoom:40%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425115048518.png" alt="image-20230425115048518" style="zoom:50%;" />

但退出后是这样的

- `ps`查看进程信息并通过`less`分页显示

  `ps -ef |less`指令

  <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425120357374.png" alt="image-20230425120357374" style="zoom:50%;" />

- 查看命令历史使用记录并通过`less`分页显示
  命令：

  ```shell
  history | less
  ```

  <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425120251304.png" alt="image-20230425120251304" style="zoom:50%;" />

- 浏览多个文件 `less 文件名1 文件名2` 

---

## 13.head命令

用来显示开头或结尾某个数量的文字区块，`head` 用来显示文件的开头至标准输出中

格式：`head 参数 文件`

#### 命令参数

- `-q` 隐藏文件名
- `-v` 显示文件名
- `-c`<字节> 显示字节数
- `-n`<行数> 显示的行数

#### 示例

- 显示文件的前n行   `head -n 5 文件名`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425122046237.png" alt="image-20230425122046237" style="zoom:50%;" />

- 显示文件的前n个字节 `head -c 20 文件名`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425122203097.png" alt="image-20230425122203097" style="zoom:50%;" />

- 文件的除了最后n个字节以外的内容 `head -c -20 文件名`（注意不是从后显示，因为head只看头，因此负数相当于啥都不看了）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425122340822.png" alt="image-20230425122340822" style="zoom:50%;" />

- 输出文件除了最后n行的全部内容 `head -n -5 文件名`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425122617582.png" alt="image-20230425122617582" style="zoom:50%;" />

---

## 14.tail 命令

`tail[必要参数][选择参数][文件]`

**tail** 命令从指定点开始将文件写到标准输出。使用`tail`命令的`-f`选项可以方便的查阅正在改变的日志文件,`tail -f filename`会把`filename`里最尾部的内容显示在屏幕上,并且不断刷新，以便看到最新的文件内容。 

#### 命令参数

- `-f` 循环读取
- `-q` 不显示处理信息
- `-v` 显示详细的处理信息
- `-c`<数目> 显示的字节数
- `-n`<行数> 显示行数
- `--pid=PID` 与`-f`合用,表示在进程`ID`,`PID`死掉之后结束。
- `-q`, `--quiet`, `--silent` 从不输出给出文件名的首部。
- `-s`, `--sleep-interval=S` 与`-f`合用,表示在每次反复的间隔休眠S秒

#### 使用实例

- 显示文件末尾内容（显示文件最后5行）

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425154943129.png" alt="image-20230425154943129" style="zoom:50%;" />

- 循环查看文件内容<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425155156312.png" alt="image-20230425155156312" style="zoom:50%;" />

> 说明：该指令常用来监控一个档案、或者ping一个远程主机；使用crtl+c可以退出

- 从第5行开始显示文件 `tail -n +5 test.txt`<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425155700345.png" alt="image-20230425155700345" style="zoom:50%;" />

---

## 15. cp命令（copy）

**cp**命令用来复制文件或者目录，是Linux系统中最常用的命令之一。一般情况下，shell会设置一个别名，在命令行下复制文件时，如果目标文件已经存在，就会询问是否覆盖，不管你是否使用`-i`参数。但是如果是在shell脚本中执行`cp`时，没有`-i`参数时不会询问是否覆盖。这说明命令行和shell脚本的执行方式有些不同。 

用法：

```shell
cp [选项]... [-T] 源 目的
或：
cp [选项]... 源... 目录
或：
cp [选项]... -t 目录 源...
```

#### 命令参数

- `-a`, `--archive` - 等于`-dR --preserve=all`，`--backup[=CONTROL`为每个已存在的目标文件创建备份

- `-b` - 类似 `--backup` 但不接受参数 `--copy-contents` 在递归处理是复制特殊文件内容

- `-d` - 等于`--no-dereference --preserve=links`

- `-f`, `--force` - 如果目标文件无法打开则将其移除并重试(当 `-n` 选项 存在时则不需再选此项)

- `-i`, `--interactive` - 覆盖前询问(使前面的 `-n` 选项失效)

- `-H` - 跟随源文件中的命令行符号链接

- `-l`, `--link` - 链接文件而不复制

- `-L`, `--dereference` - 总是跟随符号链接

- `-n`, `--no-clobber` - 不要覆盖已存在的文件(使前面的 -i 选项失效)

- `-P`, `--no-dereference` - 不跟随源文件中的符号链接

- ```
  -p
  ```

   \- 等于

  ```
  --preserve=
  ```

  模式,所有权,时间戳

  ```
  --preserve
  ```

  [=属性列表   保持指定的属性(默认：模式,所有权,时间戳)，如果

  ```
           可能保持附加属性：环境、链接、xattr 等
  ```

- `-R`, `-r`, `--recursive`  复制目录及目录内的所有项目

#### 示例

- 复制单个文件到目标目录，文件在目标文件中不存在 `cp 文件名 目录`![image-20230425161509472](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425161509472.png)

- 复制单个文件到目标目录，文件在目标文件中存在（覆盖式的）（懒得截图了，就是直接覆盖了）
- 复制整个目录的文件到目标目录
- ![image-20230425162441990](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230425162441990.png)
