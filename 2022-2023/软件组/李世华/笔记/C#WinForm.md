# WinForm窗体设计开发

*前言，这不是教程，这是备忘录*

## 一、WinForm窗体设计

### 窗体及其属性

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829094320788.png" alt="image-20230829094320788" style="zoom:50%;" />

#### 变量名<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829094352622.png" alt="image-20230829094352622" style="zoom:50%;" />

*变量名用于在脚本中进行控制*

#### 背景色与背景图片!<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829094538035.png" alt="image-20230829094538035" style="zoom:50%;" />

#### 左上角图标：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829094653978.png" alt="image-20230829094653978" style="zoom:50%;" />

#### 控件文本：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829094805454.png" alt="image-20230829094805454" style="zoom:50%;" />

#### 开始位置：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829094857645.png" alt="image-20230829094857645" style="zoom:50%;" />

*此处我设置为了居中*

#### 是否允许最大化或最小化：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829095044964.png" alt="image-20230829095044964" style="zoom:50%;" />

> 相应的，按钮也可以设置变量名和文本内容

---

### 事件驱动机制

#### 通过控件进行一个按钮的点击操作

使用工具箱创建一个按钮

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829095623881.png" alt="image-20230829095623881" style="zoom:50%;" />



选中按钮，点击属性旁边的**事件**<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829095432546.png" alt="image-20230829095432546" style="zoom:50%;" />

找到我们常用的**Click**事件，并双击<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829095702954.png" alt="image-20230829095702954" style="zoom:50%;" />

此时会在脚本中显示出这样一个函数

如果不需要该函数，不能直接删除，而是要在原来的事件Click按钮中右键Click然后点击重置<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829095928370.png" alt="image-20230829095928370" style="zoom:50%;" />

#### 通过脚本操作按钮的点击事件

首先我们需要重命名各个按钮的变量名，从而方便我们的操作，在这里我们都重命名为<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829100345436.png" alt="image-20230829100345436" style="zoom:50%;" />

作为Button变量，它们拥有事件，即事件是它们的成员，它们拥有此委托，因此可以使用成员符号找出Click事件，并将函数或委托或事件添加到它们的CIick事件<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829101135103.png" alt="image-20230829101135103" style="zoom:50%;" />

#### 事件相应的公共方法

上文我们看到，如果要添加到Click事件，那么函数的签名要符合类似这种形式:![image-20230829101408480](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829101408480.png)

​	即必须是与其同一类型的委托才可以添加到Click事件，那么问题来了，这些参数有什么含义呢？

`sender` 表示“事件源的对象”，即是谁触发了这个事件，在这里是Button对象，因此可以强转为Button对象  

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829101749486.png" alt="image-20230829101749486" style="zoom:50%;" />

在强转为Button对象之后，我们就可以获取原来按钮的数据，而无需为每个按钮重复编写设置对应数据的Click事件

关于EventArgs e，来自文心一言的回答：

> **EventArgs e是一个参数，它包含事件数据。在事件处理程序中，e参数提供了一种方式来获取与事件相关的额外信息。**例如，在鼠标点击事件中，EventArgs e会包含鼠标的位置、按下和释放的信息。在一些事件中，比如取消事件，EventArgs会派生一个CancelEventArgs类，它添加了一个简单的布尔属性，这样处理事件的代码可以取消事件。
>
> **在一些情况下，EventArgs也可能是Empty，表示没有与事件相关的进一步信息。**例如，在Windows Forms应用程序中，按钮的Click事件就只会传递一个EventArgs参数，而且这个参数并不包含任何额外信息。在这种情况下，我们并不会直接使用这个EventArgs参数。

---

### 消息框的使用

*注：此处是对MessageBox类的静态函数的运用*

MessageBox显示消息窗口（也称为对话框），向用户显示消息。 这是一个模式窗口，可阻止应用程序中的其他操作，直到用户将其关闭

MessageBox.Show有好几个重载，它的完全体为：
`MessageBox.Show(框内容,框标题,框按钮,框图标)`

#### 无标题

```C#
         MessageBox.Show("请输入学员姓名");
```

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829103239564.png" alt="image-20230829103239564" style="zoom:50%;" />

#### 有标题

```C#
 MessageBox.Show("请输入学员姓名", "验证失败");
```

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829103311475.png" alt="image-20230829103311475" style="zoom:50%;" />

#### 在有标题的基础上加入OK 和 Cancel

```C#
  MessageBox.Show("请输入学员姓名", "验证失败",MessageBoxButtons.OKCancel);
```

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829103419165.png" alt="image-20230829103419165" style="zoom:50%;" />

#### 在上面的基础上加上标记

```c#
MessageBox.Show("请输入学员姓名", "验证失败", MessageBoxButtons.OKCancel, MessageBoxIcon.Warning);
```

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829103704717.png" alt="image-20230829103704717" style="zoom:50%;" />

#### 对用户的点击操作进行反馈

**DialogResult类(枚举类型)**
它表示对话框的返回值。当用户关闭对话框时，DialogResult属性将包含一个指示用户如何关闭对话框的值。

```C#
            DialogResult MesResult = MessageBox.Show("请输入学员姓名", "验证失败", MessageBoxButtons.OKCancel, MessageBoxIcon.Warning);
            if(MesResult==DialogResult.Cancel)
            {
                //用户点击取消
                MessageBox.Show("用户取消了操作");
            }
            else if (MesResult==DialogResult.OK)
            {
                //用户点击Ok
                MessageBox.Show("用户继续执行操作");
            }
```

---

---

## 二、项目框架设计

### 登录窗体的设计

#### 外观设置

Text、icon修改为需要的

点击视图，点击工具箱，再点击PictureBox，将PictureBox拉到窗体内

点击PictureBox，右边会出现属性窗口；找到Image，选择需要的图像

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829105711175.png" alt="image-20230829105711175" style="zoom:50%;" />

亦或是点击该箭头：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829105757250.png" alt="image-20230829105757250" style="zoom:50%;" />

当需要调整图像位置与PictureBox进行适应的时候，在属性找到SizeMode（我调整为居中比较好看

）<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829105853946.png" alt="image-20230829105853946" style="zoom:50%;" />

#### 文本框与按钮设置

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829110023453.png" alt="image-20230829110023453" style="zoom:50%;" />

登录账号和登录密码需要选中工具箱的label控件（可以按住ctrl进行拖拽复制）

文本框（登录账号与登录密码的两个空白框）需要选中工具箱的TextBox并自行拖拽设置长度，其中登录密码的框还需要设置为<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829110339753.png" alt="image-20230829110339753" style="zoom:50%;" />

两个按钮就设置图标和文本即可

#### Tab键顺序

打开视图，找到Tab键顺序，标注输入时文本框的顺序

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829111407251.png" alt="image-20230829111407251" style="zoom:50%;" />

完成后再点击一次 “Tab键顺序”

---

### 菜单栏和状态栏的设计方法

#### 菜单栏

菜单栏在工具箱的这里<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829164107789.png" alt="image-20230829164107789" style="zoom:50%;" />

我们选中MenuStrip，然后会在这里有这么一个格子<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829164352071.png" alt="image-20230829164352071" style="zoom:50%;" />

可以往里面输入文本，如果在输入文本之后加上  (&A)  ,则可以定义A为该菜单的快捷键，如下

​	<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829164630365.png" alt="image-20230829164630365" style="zoom:50%;" />

同时也可以点击右键，选中“编辑项”为该选项添加图标<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829164731547.png" alt="image-20230829164731547" style="zoom:50%;" />

如果要作分隔，也可以右键——插入——Separator<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829164830933.png" alt="image-20230829164830933" style="zoom:50%;" />

总效果如图所示

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829165244814.png" alt="image-20230829165244814" style="zoom:50%;" />

#### 状态栏

工具箱——菜单和工具栏——StatusStrips<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829165506085.png" alt="image-20230829165506085" style="zoom:50%;" />

选中左下角的<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829165619730.png" alt="image-20230829165619730" style="zoom:50%;" />

可以点击StatusLabel添加版本信息、用户使用信息和部分标语，类似如下

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829165659126.png" alt="image-20230829165659126" style="zoom:50%;" />

也可以点击DropDownButton，搞一个下拉菜单，类似我这种<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829165930839.png" alt="image-20230829165930839" style="zoom:50%;" />

---

### 项目主窗体的设计

#### 分割窗体

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829200055439.png" alt="image-20230829200055439" style="zoom:50%;" />

像这样将窗体分割成左右两部分，选中工具箱的SplitContainer，创建该控件并拖拽到窗体中

由于该控件比较小，如果要找到该控件的属性，可以从下拉框找：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829200320438.png" alt="image-20230829200320438" style="zoom:50%;" />

该控件会将窗体分割为两部分。此时拉伸窗口会导致比例发生变化。由于我们的左窗体无需变化，因此我们选中splitContainer控件（或在下拉框找到），然后做下图操作：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829200700021.png" alt="image-20230829200700021" style="zoom:50%;" />

#### 设置日历

工具栏——MonthCalendar控件（这玩意好像没法修改大小）

#### 批量设置按钮的Image

工具栏——组件——ImageList，此时它会出现在左下框，点击小箭头

> 组件这种东西它不会在用户面前显示出来但是会在我们制作组件的时候显示

![image-20230829203007274](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829203007274.png)

点击选择图像，然后添加即可

这时候再点击按钮，找到属性，找到ImageList，将我们的ImageList改为我们创建的，然后就可以在ImageIndex里面自选了

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230829203335412.png" alt="image-20230829203335412" style="zoom:50%;" />

#### 设置背景图片与文字设置

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230830165505422.png" alt="image-20230830165505422" style="zoom:50%;" />

都是现成的工具，没什么叫教程，文字是文本框，背景就是随便拿张图片嗯套上去

---

### 添加新学员的窗口设计

大概成品

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230830170206300.png" alt="image-20230830170206300" style="zoom:50%;" />

#### 使用GroupBox控件

工具箱——容器

GroupBox控件为其他控件提供可以识别的分组，并且相较于Panel控件，它可以显示标题（但Panel控件拥有滑动条）



#### 互斥控件——性别RadioButtom

RadioButton控件是Windows窗体的一种控件，用于提供由两个或多个互斥选项组成的选项集。这意味着在同一组内只能选择一个单选按钮。（这里的组就是GroupBox，即处于同一个GroupBox中，只能选中一个单选按钮）

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230830185244070.png" alt="image-20230830185244070" style="zoom:75%;" />

#### 可供选择的下拉列表ComboBox

效果如图

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230830185358082.png" alt="image-20230830185358082" style="zoom:50%;" />

选择工具箱的公共控件——ComboBox，右键属性——Items——<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230830185624118.png" alt="image-20230830185624118" style="zoom:50%;" />

---

### 子窗体嵌入父容器

#### 初实验

效果：点击按钮时弹出窗口

选中指定按钮——找到事件Click并双击，然后找到函数并在里面输入

```C#
private void button1_Click(object sender, EventArgs e)
{
    FrmAddStudent frmSon = new FrmAddStudent();//创建一个子窗体对象
	frmSon.Show();
}
```

#### 再实验

效果：嵌入窗体

```C#
private void button1_Click(object sender, EventArgs e)
{
            FrmAddStudent frmSon = new FrmAddStudent();//创建一个子窗体对象
            //要使一个窗体变为子窗体的必要工作
            frmSon.TopLevel = false;//将子窗体设置为非顶级控件
            frmSon.WindowState = FormWindowState.Maximized;//将窗体设置为最大化显示
            frmSon.FormBorderStyle = FormBorderStyle.None;//去掉窗体的边框
            frmSon.Parent = MainFormSplitCounter.Panel2;//指定窗体所显示的容器
            frmSon.Show();
}
```

并在子窗体的关闭窗口那里的按钮的Click的事件<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230830231414925.png" alt="image-20230830231414925" style="zoom:50%;" />

```C#
        private void btnCloseButton_Click(object sender, EventArgs e)
        {
            this.Close();
        }
```

缺点：当我连续点击多个窗口的时候，这些窗口是叠加在父容器中的，这意味着我要点击很多次关闭窗口才能清空父容器

#### 完美版本

修正了版本2，每次点击窗口都会将之前的所有子窗体关闭，这样一来即便是点击多个子窗体创建，也只需要关闭一次即可

```C#
private void button1_Click(object sender, EventArgs e)
{
            //首先判断当前容器是否已经存在窗体
            //容器中所有控件继承自Control类
            //只要是容器，都有Controls这个集合
            foreach (Control control in MainFormSplitCounter.Panel2.Controls)
            {
                if (control is Form)
                {
                    ((Form)control).Close();
                }
            }
    
            FrmAddStudent frmSon = new FrmAddStudent();//创建一个子窗体对象
            //要使一个窗体变为子窗体的必要工作
            frmSon.TopLevel = false;//将子窗体设置为非顶级控件
            frmSon.WindowState = FormWindowState.Maximized;//将窗体设置为最大化显示
            frmSon.FormBorderStyle = FormBorderStyle.None;//去掉窗体的边框
            frmSon.Parent = MainFormSplitCounter.Panel2;//指定窗体所显示的容器
            frmSon.Show();
}
```

#### 面向对象的完美版本

我们意识到一点，首先是关闭窗口的，这个可以进行复用

还有将一个窗体设计为子窗体的大部分代码也可以进行复用

因此我们可以将关闭窗口的部分设为一个函数，然后将设计子窗体的部分也封装成一个函数

则如下

**关闭窗口的函数**

```C#
  private void ClosePreForm(Control MainForm)//清除当前控件所包含的窗体
        {
            foreach (Control control in MainForm.Controls)
            {
                if (control is Form)
                {
                    ((Form)control).Close();
                }
            }
        }//这里我们传入的参数是，我们想要清理的父窗体，在执行完成后，父窗体内的所有窗体都会被关掉
```

**将窗体设计为子窗体的函数**

```C#
private void MakeThisSonForm(Form frmSon,Control frmFather)//传入一个子窗体与一个父窗体
        {
            //要使一个窗体变为子窗体的必要工作
            frmSon.TopLevel = false;//将子窗体设置为非顶级控件
            frmSon.WindowState = FormWindowState.Maximized;//将窗体设置为最大化显示
            frmSon.FormBorderStyle = FormBorderStyle.None;//去掉窗体的边框
            frmSon.Parent = frmFather;//指定窗体所显示的容器
          
            frmSon.Show();
        }
```

**最后在点击函数中如此调用**

```C#
 private void button1_Click(object sender, EventArgs e)
        {
            ClosePreForm(MainFormSplitCounter.Panel2);
            MakeThisSonForm(new FrmAddStudent(),MainFormSplitCounter.Panel2);
        }
```

---

### 学员信息管理窗体的设计

大概是这个样子

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230831202335558.png" alt="image-20230831202335558" style="zoom:50%;" />

新东西大概只有那个框体，也就是**DataGridView**

> `DataGridView` 控件提供一种以表格格式显示数据的功能强大且灵活的方法。 可以使用 `DataGridView` 控件来显示少量数据的只读视图，或者可以缩放该控件以显示大型数据集的可编辑视图。
>
> 可以使用多种方法扩展 `DataGridView` 控件，以便将自定义行为置入你的应用程序中。 例如，可以以编程方式指定自己的排序算法，并且可以创建自己的单元格类型。 可以通过在多个属性之间进行选择来轻松地自定义 `DataGridView` 控件的外观。 许多数据存储类型均可用作数据源，或者，`DataGridView` 控件可以在不绑定任何数据源的情况下进行操作。
>
> 来自微软文档的解释

对于此，我们直接上链接：[DataGridView 控件 - Windows Forms .NET Framework | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/desktop/winforms/controls/datagridview-control-windows-forms?view=netframeworkdesktop-4.8)

一般来说，在放置之后，它会出现这样的情况：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230831202947468.png" alt="image-20230831202947468" style="zoom:50%;" />

这时候我们需要将这三个启用全部取消，然后再设置合适的背景颜色，之后编辑的时候需要点击这个![image-20230831203508328](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230831203508328.png)

从而进行数据的导入<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230831203535133.png" alt="image-20230831203535133" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230831204140373.png" alt="image-20230831204140373" style="zoom:50%;" />

再完成以后再找到这个玩意的属性——EnableHeadersVisualStyles调整为False

这样就可以编辑这个栏的很多东西了（开启个性化！）

---

### 自学 如何由登录窗体进入主界面

> 此乃本人探索而来

首先，登录窗体在登录完成后应该是要关掉的对吧

其次，我们找到最初的Program.cs 发现我们写的是Application.Run()

最后，经过了解，`Application.Run` 方法用于启动应用程序消息循环并处理用户输入，而窗体类的 `Show` 方法仅用于显示窗体。

所以在一开始我的做法是，在Program.cs运行Application.Run(登录窗体)，然后在登录窗体的Click函数中写主窗体.Show，最后再关闭登录窗体。**但这个是错误的，因为在登录窗体关闭后，这一条程序线就消失了，主窗体会随着登录窗体一同消失**

所以正确的做法是，在Program.cs内用ShowDialog显示登录窗体，确定交互结果，然后再用Application.Run运行。而**交互结果**的确认是通过窗体的重要属性**DialogResult**

> [DialogResult属性是一个枚举类型，它表示窗体的返回值。当窗体以模态方式显示时，可以使用ShowDialog方法来显示窗体，并在窗体关闭后检查其DialogResult属性以确定用户如何关闭窗体](https://learn.microsoft.com/zh-cn/dotnet/api/system.windows.window.dialogresult?view=windowsdesktop-7.0)[1](https://learn.microsoft.com/zh-cn/dotnet/api/system.windows.window.dialogresult?view=windowsdesktop-7.0)。

您可以使用这些信息来确定用户是接受了对话框（单击了“确定”按钮），还是取消了对话框（单击了“取消”按钮）。这样，您就可以根据用户的选择执行相应的操作。

> **关于Show和ShowDialog的区别（很重要）**
>
> > show(非模态显示)仅仅是显示出来窗口界面而已,也就是和你执行的结果在同一窗口显示,所显示的窗口可以在后台运行.
> >
> > showDialog(模态显示)是一个对话框窗口界面 ，执行结果以新窗口界面出现，不允许进行后台运行，就是你想编辑什么的时候，非得先关闭showDialog()窗口界面才可以进行其他操作
> >
> > [非模态显示后，可以在弹出窗口和调用窗口之间随意切换。调用窗口调用show方法后，下面的代码可以立即执行。在非模态窗口关闭后，窗口的所有资源被释放，窗口不存在，无法获取窗口的任何信息](https://blog.csdn.net/qq_23062949/article/details/117711827)
> >
> > [模态显示后，弹出窗口阻止调用窗口的所有消息响应。只有在弹出窗口结束后调用窗口才能继续。在模态窗口“关闭”后，可以读取模态窗口中信息，包括窗口的返回状态，窗口子控件的值](https://blog.csdn.net/qq_23062949/article/details/117711827)
>
> 关于ShowDialog的中断代码执行：
>
> ShowDialog方法会中断代码执行。**当您使用ShowDialog方法显示一个窗体时，代码将在该方法处暂停执行，直到用户关闭窗体为止**。在窗体关闭后，代码将从ShowDialog方法处继续执行。
>
> 这就是为什么**ShowDialog方法通常用于显示对话框或需要用户输入的窗体**。您可以使用ShowDialog方法来显示一个窗体，然后在窗体关闭后**检查其DialogResult属性以确定用户如何关闭窗体**，并根据用户的选择执行相应的操作。

所以，我们在主程序的主函数代码是：

```C#
  internal static class Program
    {
        /// <summary>
        ///  The main entry point for the application.
        /// </summary>
        [STAThread]
        static void Main()
        {
            // To customize application configuration such as set high DPI settings or default font,
            // see https://aka.ms/applicationconfiguration.
            ApplicationConfiguration.Initialize();

            FrmUserLogin frmUserLogin = new FrmUserLogin();
            frmUserLogin.ShowDialog();//使用ShowDialog实现模态窗口
            
            //由于ShowDialog会中断代码执行
            if(frmUserLogin.DialogResult==DialogResult.OK)
            {
                Application.Run(new FrmMain());
            }
        }
```

然后，我们在`frmUserLogin`窗体的登录按钮的Click函数中写到

```C#
            //牛逼
            //我在主程序调用登录窗体的显示
            /*
            FrmUserLogin frmUserLogin = new FrmUserLogin();
            frmUserLogin.ShowDialog();
             */
            //当用户点击登录的时候，会跳到这个函数，这时候我们将这个DialogResult状态进行设置
            this.DialogResult= DialogResult.OK;
            this.Close();
            this.Dispose();
            //然后在主程序中检测，如果状态发生了改变，就会建立主窗口
            /*
            if(frmUserLogin.DialogResult==DialogResult.OK)
            {
                Application.Run(new FrmMain());
            }
             */

            //这里厉害的地方在于，在我竭尽脑子想怎么将这里的“点击”传给主函数，告诉主函数这里被点击了
            //它告诉我可以在用户点击之后，直接修改这个窗体的某个属性，然后再将属性的变化告诉主函数，从而使得主函数检测到登录成功
            //主函数检测到登录成功后，就在主程序中运行主窗体
```

**重点**：**DialogResult**、.**ShowDialog**()、Application.Run

---

---

## 三、上位机中的IO操作

**写入文件的几个操作**

1. 创建文件流
2. 创建读写器
3. 进行流式读写
4. 关闭读写器
5. 关闭文件流

*提示：必须先关闭读写器再关闭文件流。如果您先关闭文件流，然后再关闭 `StreamWriter`，则在 `StreamWriter` 尝试刷新缓冲区并关闭文件流时，它将无法访问已经关闭的文件流，从而导致异常。*

#### 覆盖式写入文本文件

```C#
 private void btnWriteInText_Click(object sender, EventArgs e)
 {
     	 //1.创建文件流
         FileStream fileStream = new FileStream(this.text_TargetFilePath.Text, FileMode.Create);//FileMode.Create是创建文件,因此是写入式的
         //2.创建写入器
         StreamWriter writer = new StreamWriter(fileStream, Encoding.Default);
         //3.以流的方式写入数据
         writer.Write(WriterOrReader.Text);//WriteOrReader是一个文本框，里面有文本
         //4.关闭写入器
         writer.Close();
         //5.关闭文件流
         fileStream.Close();

     	 //文件流打开一个文件，并以覆盖写的方式打开
     	 //使用写入器写入数据，那么这时候要写入的数据就放在writer.write()中
     	
         //成功操作后进行提示
         MessageBox.Show("写入文本文件成功！");
}
```



#### 附加式写入文本文件

```C#
private void btnSimulateWritingToTheSystemLog_Click(object sender, EventArgs e)
{
	    //1.创建文件流
            FileStream fileStream = new FileStream(text_TargetFilePath.Text, FileMode.Append);
            //2.创建写入流
            StreamWriter sw = new StreamWriter(fileStream);
            //3.流式写入文件
            sw.WriteLine(DateTime.Now.ToString() + "文件操作正确");
            //4.关闭写入器
            sw.Close();
            //5.关闭文件流
            fileStream.Close();
    
    		//原理同上，只不过是将写入改为了Append
    
            //成功提示
            MessageBox.Show("操作成功");
}
```



#### 读入文本文件

```C#
 private void btnReadFromText_Click(object sender, EventArgs e)
        {
            //1.创建文件流
            FileStream fileStream = new FileStream(this.text_TargetFilePath.Text, FileMode.Open);
            //2.创建读取流
            //如果是自己的文件，则不需要第二个参数；但由于是别人的文件，所以可能会有编码上的问题
            StreamReader sr = new StreamReader(fileStream, Encoding.Default);
            //3.以流的方式读取数据
            this.WriterOrReader.Text = sr.ReadToEnd();
            //4.关闭读取器
            sr.Close();
            //5.关闭文件流
            fileStream.Close();
     		
     
     //StreamReader的对象的ReadToEnd方法会返回字符串
     //而WriterOrReader.Text本来就是一个字符串变量（可以这么说？）
     //所以直接赋值，它就会直接显示在文本框中
     

            //成功操作后进行提示
            MessageBox.Show("读取文本文件成功！");
        }
```



//更详细介绍如下

> [`FileStream` 类是 C# 中用于对文件进行读取和写入操作的类。它为文件提供了 `Stream`，既支持同步读写操作，也支持异步读写操作](https://learn.microsoft.com/zh-cn/dotnet/api/system.io.filestream?view=net-7.0)[1](https://learn.microsoft.com/zh-cn/dotnet/api/system.io.filestream?view=net-7.0)。
>
> `FileStream` 类有许多构造函数，它们用于创建 `FileStream` 对象并指定如何打开或创建文件。下面是一些常用的构造函数及其参数的解释：
>
> - `FileStream(String, FileMode)`：使用指定的路径和创建模式初始化 `FileStream` 类的新实例。
> - `FileStream(String, FileMode, FileAccess)`：使用指定的路径、创建模式和读/写权限初始化 `FileStream` 类的新实例。
> - `FileStream(String, FileMode, FileAccess, FileShare)`：使用指定的路径、创建模式、读/写权限和共享权限创建 `FileStream` 类的新实例。
> - `FileStream(String, FileMode, FileAccess, FileShare, Int32)`：用指定的路径、创建模式、读/写及共享权限和缓冲区大小初始化 `FileStream` 类的新实例。
> - `FileStream(String, FileMode, FileAccess, FileShare, Int32, FileOptions)`：使用指定的路径、创建模式、读/写和共享权限、其他 FileStreams 可以具有的对此文件的访问权限、缓冲区大小和附加文件选项初始化 `FileStream` 类的新实例。
>
> 这些构造函数中，第一个参数通常是要打开或创建的文件的路径。第二个参数是一个 `FileMode` 枚举值，它指定操作系统打开文件的方式。第三个参数是一个 `FileAccess` 枚举值，它指定对文件的访问类型（读、写或读写）。第四个参数是一个 `FileShare` 枚举值，它指定文件的共享级别。第五个参数是一个整数，它指定缓冲区大小。第六个参数是一个 `FileOptions` 枚举值，它指定附加文件选项。
>
> 除了构造函数外，`FileStream` 类还有许多常用方法，包括：
>
> - `Read`：从当前流中读取字节块并将数据写入缓冲区。
> - `Write`：将字节块写入当前流。
> - `Seek`：设置当前流中的位置。
> - `Flush`：清除此流的所有缓冲区并使所有缓冲数据写入基础设备。
> - `Close`：关闭当前流并释放与之关联的所有资源（如套接字和文件句柄）。
> - `ReadAsync`：异步地从当前流中读取字节序列，并将流中的位置提升读取的字节数。
> - `WriteAsync`：异步地将字节序列写入当前流，并将流中的当前位置提升写入的字节数。
>
> 这些方法可以用来控制如何从文件中读取数据或向文件中写入数据。例如，您可以使用 `Read` 方法从文件中读取数据，然后使用 `Seek` 方法更改流中的位置。如果您想要确保所有数据都已写入文件，可以使用 `Flush` 方法。



> StreamReader
>
> [`StreamReader` 类是 C# 中用于从流中读取字符的类。它继承自 `TextReader` 类，该类提供了从流中读取字符、块、行或所有内容的方法](https://learn.microsoft.com/en-us/dotnet/api/system.io.streamreader?view=net-7.0)[1](https://learn.microsoft.com/en-us/dotnet/api/system.io.streamreader?view=net-7.0)。
>
> `StreamReader` 类有许多构造函数，它们用于创建 `StreamReader` 对象并指定如何打开或创建文件。下面是一些常用的构造函数及其参数的解释：
>
> - `StreamReader(Stream)`：使用 UTF-8 编码和默认的缓冲区大小，为指定的流初始化 `StreamReader` 类的新实例。
> - `StreamReader(Stream, Encoding)`：使用指定的编码和默认的缓冲区大小，为指定的流初始化 `StreamReader` 类的新实例。
> - `StreamReader(Stream, Encoding, Int32)`：使用指定的编码和缓冲区大小，为指定的流初始化 `StreamReader` 类的新实例。
> - `StreamReader(String)`：使用默认编码和缓冲区大小，为指定的文件初始化 `StreamReader` 类的一个新实例。
> - `StreamReader(String, Boolean)`：使用默认编码和缓冲区大小，为指定的文件初始化 `StreamReader` 类的一个新实例。如果该文件存在，则可以将其覆盖或向其追加。如果该文件不存在，此构造函数将创建一个新文件。
> - `StreamReader(String, Boolean, Encoding)`：使用指定的编码和默认的缓冲区大小，为指定的文件初始化 `StreamReader` 类的一个新实例。如果该文件存在，则可以将其覆盖或向其追加。如果该文件不存在，此构造函数将创建一个新文件。
>
> 这些构造函数中，第一个参数通常是要读取的文件或流。第二个参数通常是要使用的编码。第三个参数通常是要使用的缓冲区大小。
>
> 除了构造函数外，`StreamReader` 类还有许多常用方法，包括：
>
> - `Read`：从当前流中读取下一个字符或下一组字符。
> - `ReadLine`：从当前流中读取一行字符并将数据作为字符串返回。
> - `Peek`：返回下一个可用字符，但不消耗它。
> - `Close`：关闭当前的 `StreamReader` 对象和基础流。
> - `ReadAsync`：异步地从当前流中读取下一个字符或下一组字符。
> - `ReadLineAsync`：异步地从当前流中读取一行字符并将数据作为字符串返回。
>
> 这些方法可以用来控制如何从文件中读取文本。例如，您可以使用 `ReadLine` 方法一行一行地读取文本，然后使用 `Peek` 方法检查是否还有更多文本可供读取。希望这些信息能够帮助您理解 `StreamReader` 类中常用构造函数、方法及其参数。如果您还有其他问题，请随时告诉我。😊

> [`StreamWriter` 类是 C# 中用于将字符写入特定编码的流中的类。它继承自 `TextWriter` 类，该类提供了将对象写入字符串、将字符串写入文件或序列化 XML 的方法](https://learn.microsoft.com/en-us/dotnet/api/system.io.streamwriter?view=net-7.0)[1](https://learn.microsoft.com/en-us/dotnet/api/system.io.streamwriter?view=net-7.0)。
>
> `StreamWriter` 类有许多构造函数，它们用于创建 `StreamWriter` 对象并指定如何打开或创建文件。下面是一些常用的构造函数及其参数的解释：
>
> - `StreamWriter(Stream)`：使用 UTF-8 编码和默认的缓冲区大小，为指定的流初始化 `StreamWriter` 类的新实例。
> - `StreamWriter(Stream, Encoding)`：使用指定的编码和默认的缓冲区大小，为指定的流初始化 `StreamWriter` 类的新实例。
> - `StreamWriter(Stream, Encoding, Int32)`：使用指定的编码和缓冲区大小，为指定的流初始化 `StreamWriter` 类的新实例。
> - `StreamWriter(String)`：使用默认编码和缓冲区大小，为指定的文件初始化 `StreamWriter` 类的一个新实例。
> - `StreamWriter(String, Boolean)`：使用默认编码和缓冲区大小，为指定的文件初始化 `StreamWriter` 类的一个新实例。如果该文件存在，则可以将其覆盖或向其追加。如果该文件不存在，此构造函数将创建一个新文件。
> - `StreamWriter(String, Boolean, Encoding)`：使用指定的编码和默认的缓冲区大小，为指定的文件初始化 `StreamWriter` 类的一个新实例。如果该文件存在，则可以将其覆盖或向其追加。如果该文件不存在，此构造函数将创建一个新文件。
>
> 这些构造函数中，第一个参数通常是要写入的文件或流。第二个参数通常是要使用的编码。第三个参数通常是要使用的缓冲区大小。
>
> 除了构造函数外，`StreamWriter` 类还有许多常用方法，包括：
>
> - `Write`：将字符、字符数组或字符串写入流中。
> - `WriteLine`：将字符、字符数组或字符串写入流中，并在末尾添加换行符。
> - `Flush`：清除所有缓冲区并使所有缓冲数据写入基础流。
> - `Close`：关闭当前的 `StreamWriter` 对象和基础流。
> - `WriteAsync`：异步地将字符、字符数组或字符串写入流中。
> - `WriteLineAsync`：异步地将字符、字符数组或字符串写入流中，并在末尾添加换行符。
>
> 这些方法可以用来控制如何将文本写入文件。例如，您可以使用 `Write` 方法将文本写入文件，然后使用 `Flush` 方法确保所有数据都已写入文件。如果您想要在写入文本时自动添加换行符，可以使用 `WriteLine` 方法。希望这些信息能够帮助您理解 `StreamWriter` 类中常用构造函数、方法及其参数。

### 对文件目录的操作——显示指定目录下的文件/文件夹/文件与文件夹

```C#
using System.IO
public void Show(object sender, EventArgs e)
{
    string [] files = Directory.GetDirectories(文件路径);
    
    //清空显示控件的内容
    TextBox.Clear();
    
    
      foreach (string file in files)
            {
                WriterOrReader.Text += file + "\r\n";//在Windows上运行的TextBox能够显示的换行必须由两个字符组成：carriage return & line feed
            }
}
//如果只想显示文件而不包含文件夹，用GetFiles
//如果只想显示文件夹，就像我这样
//如果都想显示，则GetFileSystemEntries

```

### 对文件目录的操作——创建与删除文件、目录

```C#
public void CreateOrDelete()
{
    //删除
    DirectoryInfo dir  = new DirectoryInfo(指定文件路径);
    //如果目录为空，则使用这个
    dir.Delete();//如果目录不为空，会引发IOException，可用try。。。catch进行捕获并进行第二步骤
    //如果不为空，则
    dir.Delete(true);
    
    //创建
    Directory.CreateDirectory(指定文件路径);
        //https://learn.microsoft.com/zh-cn/dotnet/api/system.io.directoryinfo.createsubdirectory?view=net-7.0#system-io-directoryinfo-createsubdirectory(system-string)
}
```

