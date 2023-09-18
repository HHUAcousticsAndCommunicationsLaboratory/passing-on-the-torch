# 4.复合类型

## 4.1 数组

![image-20230908203036944](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230908203036944.png)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910112459038.png" alt="image-20230910112459038" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910112725978.png" alt="image-20230910112725978" style="zoom:50%;" />

## 4.2 字符串

字符数组与字符串的关系



<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910152313131.png" alt="image-20230910152313131" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910155949620.png" alt="image-20230910155949620" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910160045370.png" alt="image-20230910160045370" style="zoom:50%;" />

字符串常量和字符常量的关系（记住，”string“表示的是字符串所在的内存位置）

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910160256621.png" alt="image-20230910160256621" style="zoom:50%;" />

字符串的拼接

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910160619999.png" alt="image-20230910160619999" style="zoom:50%;" />

验证：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910161530304.png" alt="image-20230910161530304" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910161641906.png" alt="image-20230910161641906" style="zoom:50%;" />

strlen是读到空字符之后就会停止，并且不将空字符计入在内（即后面的所有字符都将不计入）

字符串的输入：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910162236699.png" alt="image-20230910162236699" style="zoom:50%;" />

也就是说，对于包含空格的目标，cin只能读到前面的那一个

**每次读取一行的字符串输入**

`cin.getline`

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910162640774.png" alt="image-20230910162640774" style="zoom:50%;" />

> cin.getline(c, 20);//一共有19个字符，那么需要留出19+1个字符空间，其中一个为归零符号,即数组本身要有20个字符的空间，它读取19个字符，将最后一个字符（换行符）放入

**关于getline的一个特性**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910163347757.png" alt="image-20230910163347757" style="zoom:50%;" />

同时，注意一点，cin是读到空格、换行符、制表符等格子之后，就不读了，并且它不会将其录取

**关于cin.get()**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910183537387.png" alt="image-20230910183537387" style="zoom:50%;" />



> [在C++中，`cin`对象维护了一个输入队列，用于接收输入数据](https://zhuanlan.zhihu.com/p/641441221)[1](https://zhuanlan.zhihu.com/p/641441221)[。当你从键盘输入数据时，这些数据首先被放入输入队列中。然后，当你使用`cin`的成员函数（如`>>`操作符或`get()`函数）从`cin`中提取数据时，它会从输入队列中读取数据并赋值给目标变量](https://zhuanlan.zhihu.com/p/641441221)[1](https://zhuanlan.zhihu.com/p/641441221)。
>
> [当你使用`cin.get(name, ArSize)`读取一行文本时，它会读取到行尾的换行符，但并不会读取并丢弃这个换行符，而是将其留在输入队列中](https://www.zhihu.com/question/62687799)[2](https://www.zhihu.com/question/62687799)[。这意味着，如果你连续两次调用`get()`函数，第二次调用时看到的第一个字符就是这个换行符](https://www.zhihu.com/question/62687799)[2](https://www.zhihu.com/question/62687799)[。因此，第二次调用`get()`函数会立即停止读取，因为它认为已经到达了行尾](https://www.zhihu.com/question/62687799)[2](https://www.zhihu.com/question/62687799)。
>
> [所以，在这里，“换行符将留在输入队列中”是指换行符仍然存在于输入队列中，并没有被读取并丢弃。如果你想要连续两次调用`get()`函数并正确地读取两行文本，你需要在两次调用之间使用一个额外的`get()`函数来读取并丢弃这个换行符](https://www.zhihu.com/question/62687799)[2](https://www.zhihu.com/question/62687799)

**空行和其他问题**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910184819407.png" alt="image-20230910184819407" style="zoom:50%;" />

> [这段话的意思是，当你使用`getline()`或`get()`函数读取空行时，它们的行为可能会有所不同。在早期的实现中，当`getline()`或`get()`读取空行时，下一条输入语句将从前一条`getline()`或`get()`结束读取的位置开始读取。但是，在当前的实现中，当`get()`（而不是`getline()`）读取空行后，它将设置失效位（`failbit`），这意味着接下来的输入将被阻断。但是，你可以使用`cin.clear()`命令来恢复输入](https://juejin.cn/post/7033677795540598815)[1](https://juejin.cn/post/7033677795540598815)。
>
> 例如，假设你有以下代码：
>
> ```cpp
> 	char a[100]{};
> 	cin.get(a,100);
> 
> 	char c[100]{};
> 	cin.get(c, 100);
> 
> 
> 	char b[100]{};
> 	cin.get(b, 100);
> 
> 	scanf_s("%s", b);
> 	cout << "C为：" << c << endl;
> 	cout << "B为：" << b << endl;
> 	cout << "A为：" << a << endl;
> ```
>
> [如果你在键盘上输入一个空行并按下回车键，则在早期的实现中，程序将输出一个空行。但是，在当前的实现中，由于`get()`函数读取空行后设置了失效位，因此接下来的输入将被阻断(即这里的所有输出都将没有有结果)，程序将不会输出任何内容。如果你想要恢复输入，可以在调用`get()`函数之后使用`cin.clear()`命令来清除失效位](https://juejin.cn/post/7033677795540598815)[1](https://juejin.cn/post/7033677795540598815)。

后面我使用，发现还是不行

```C++
	char a[100]{};
	cin.get(a,100);
	cin.clear();

	char c[100]{};
	cin.get(c, 100);
	cin.clear();

	char b[100]{};
	cin.get(b, 100);
	cin.clear();

	cout << "C为：" << c << endl;
	cout << "B为：" << b << endl;
	cout << "A为：" << a << endl;
```

然后修正为：

>这段代码中的问题可能在于`cin.get()`函数的使用。`cin.get()`函数会读取输入直到遇到换行符，但是它不会从输入流中删除这个换行符。所以，如果你连续调用`cin.get()`，第二次调用会立即遇到前一次留下的换行符，然后立即停止读取。
>
>在你的代码中，你在每次调用`cin.get()`后都调用了`cin.clear()`。这个函数会清除输入流的错误状态，但是它不会删除任何未读取的字符。所以，如果`cin.get()`遇到了一个换行符并停止读取，那么这个换行符会留在输入流中，等待下一次输入操作。
>
>解决这个问题的一种方法是在每次调用`cin.get()`后，使用`cin.ignore()`函数来忽略剩余的字符，直到遇到下一个换行符。例如：
>
>```cpp
>char a[100]{};
>cin.get(a, 100);
>cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
>
>char c[100]{};
>cin.get(c, 100);
>cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
>
>char b[100]{};
>cin.get(b, 100);
>cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
>
>cout << "C为：" << c << endl;
>cout << "B为：" << b << endl;
>cout << "A为：" << a << endl;
>```
>
>这样，每次调用`cin.get()`后，都会清除输入流中的剩余字符，包括换行符。这样就可以确保每次调用`cin.get()`时，都会从新的一行开始读取。希望这个解答能帮助你！

**混合输入字符串和数字**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910192435456.png" alt="image-20230910192435456" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910192647546.png" alt="image-20230910192647546" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910192711531.png" alt="image-20230910192711531" style="zoom:50%;" />

## 4.3 C++ string类

string类的定义隐藏了字符串的数组性质

**C++的字符串初始化**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910193225427.png" alt="image-20230910193225427" style="zoom:50%;" />

**字符串的赋值问题**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910193807066.png" alt="image-20230910193807066" style="zoom:50%;" />

经过验证，也可以把**字符数组赋值给字符串**；但**无法把字符串赋值给字符数组**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910193718097.png" alt="image-20230910193718097" style="zoom:50%;" />

**string类的其他操作**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910194059553.png" alt="image-20230910194059553" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910194134513.png" alt="image-20230910194134513" style="zoom:50%;" />

下面是两种确定字符串中字符数的方法

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910194514428.png" alt="image-20230910194514428" style="zoom:50%;" />

**string类的I/O**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910194645391.png" alt="image-20230910194645391" style="zoom:50%;" />

**其他形式的字符串字面值**

![image-20230910195911878](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910195911878.png)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910200051023.png" alt="image-20230910200051023" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910200317207.png" alt="image-20230910200317207" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910200502101.png" alt="image-20230910200502101" style="zoom:50%;" />

## 4.4 结构

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910201218592.png" alt="image-20230910201218592" style="zoom:50%;" />

### 4.4.1在程序中使用结构

![image-20230910201432944](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910201432944.png)

结构体的初始化

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910201605439.png" alt="image-20230910201605439" style="zoom:50%;" />

那么结构体数组的初始化将基于此，类似于：

```C++
		struct inflatable
	{
		string name;
		float volume;
		float price;
	};

	inflatable a[] = {
		{"hello",11,1},
		{"goode",11,1},
		{"dsfds",1,3}
	}
```

可将每个结构成员看作是相应类型的变量

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910202045551.png" alt="image-20230910202045551" style="zoom:50%;" />

### 4.4.2 结构的初始化

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910202129726.png" alt="image-20230910202129726" style="zoom:50%;" />

### 4.4.4 其他结构属性

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910202606426.png" alt="image-20230910202606426" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910203420258.png" alt="image-20230910203420258" style="zoom:50%;" />

经过测试发现，数组的这种赋值是值赋值而不是引用赋值（指针赋值）

即，在赋值之后，A，B之间的数组成员不会相互影响，类似于C#的深拷贝

(C++11特性除外)，但C++结构的特性更多。例如，与C结构不同，C++结构除了成员变量之外，还可以
有成员函数。但这些高级特性通常被用于类中，而不是结构中，因此将在讨论类的时候(从第10章开始)

### 4.4.6 结构体中的位字段

![image-20230910203953613](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230910203953613.png)

> `unsigned int : 4;` 这一行定义了一个占用4位但没有名称的位字段。这四个位不会被使用，但会占据空间，从而使得后面的 `goodIn` 和 `goodTorgle` 字段在内存中的位置向后偏移4位。这样就创建了一个4位的间距。

在某些情况下，创建这样的间距是有必要的。这主要出现在以下两种情况：

1. **数据对齐**：在某些硬件和操作系统中，特定类型的数据需要在内存中以特定的边界对齐。例如，一个4字节的整数可能需要在内存中以4字节的边界对齐。如果你的结构体中的数据没有正确对齐，那么CPU可能需要进行额外的内存访问才能读取或写入这个数据，这会降低程序的性能。
2. **硬件接口**：如果你正在编写一个与特定硬件设备通信的程序，那么你可能需要创建一个与设备寄存器布局完全匹配的数据结构。在这种情况下，你可能需要插入一些未使用的位来确保数据结构中的其他字段与硬件寄存器中的相应字段对齐。

然而，在大多数情况下，你并不需要手动插入这样的间距。编译器通常会自动处理数据对齐问题，并且除非你正在进行底层编程，否则你通常不需要关心硬件寄存器布局。

## 4.5 共用体

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911192245192.png" alt="image-20230911192245192" style="zoom:50%;" />

## 4.6 枚举

![image-20230911192553859](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911192553859.png)

![image-20230911192604722](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911192604722.png)

怎么理解这个枚举呢？用C#里面最简单的一个东西去理解

```C#
DialogResult a= DialogResult.Ok;
```

DialogResult就是那个类型，OK就是符号常量

```C++
//C++	
enum DialogResult {
		OK,
		Cancel
	};

	DialogResult a = OK;
```

**枚举的一些特殊属性**

![image-20230911193203788](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911193203788.png)

![image-20230911193255690](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911193255690.png)

![image-20230911193412701](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911193412701.png)

```C++
//换句话说，当枚举类型与整形进行运算时，会优先转化为整形，那么结果就是整形而不是枚举，无法赋值
//但可以运算完成后转为枚举

	enum DialogResult {
		OK,
		Cancel
	};

	DialogResult a = OK;
	a = (DialogResult)(OK + 1);
```

### 4.6.1 枚举

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911194103057.png" alt="image-20230911194103057" style="zoom:50%;" />

### 4.6.2 枚举的取值范围

![image-20230911194719767](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911194719767.png)

## 4.7 指针和自由存储空间

指针是-一个变量, 其存储的是值的地址，而不是值本身。

当你试图打印一个指针或者一个内存地址时，C++默认会以16进制的形式进行输出。

![image-20230911200442214](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911200442214.png)

![image-20230911200643763](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911200643763.png)

### 4.7.1 声明和初始化指针

![image-20230911200754279](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911200754279.png)

![image-20230911200938107](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911200938107.png)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911201203785.png" alt="image-20230911201203785" style="zoom:50%;" />

```C++
	int ap = 11;
	int* p = &ap;

	char as = 's';
	char* s = &as;

	struct ALL
	{
		int a;
	};
	ALL b = { 11 };
	ALL* a = &b;

	cout << sizeof(a)<<endl;//8
	cout << sizeof(p)<<endl;//8
	cout << sizeof(s)<<endl;//8
//因此我们发现指针长度都是8
```

### 4.7.2 指针的危险

**这个必须注意！**

![image-20230911202311170](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911202311170.png)

**这句话有些绕，我给大伙总结一下**

**简单来讲，定义指针变量之后，该指针变量的放在哪里（即指针变量自身所在的地址位置）是已经确定的了**

**然而！指针变量所指向的目标是没有确定的!**

**这时候的指针变量是处于乱指状态，是很危险的！**

**如果这时候你贸然修改指针变量所指向的那块地址的值，是绝对会发生报错的！**

**就像这里的代码示例，fellow指针自身的地址已经被分配了，这是毫无疑问的，但fellow的值是一个未知地址，**

**第二行代码就是在给这个未知地址修改值！**

![image-20230911203004051](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911203004051.png)

### 4.7.3 指针和数字

![image-20230911203115483](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911203115483.png)

![image-20230911203140501](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911203140501.png)

### 4.7.4 使用new来分配内存

分配一个未命名的内存，这很重要！

![image-20230911203314431](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911203314431.png)

![image-20230911203416538](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911203416538.png)

![image-20230911214042891](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911214042891.png)

![image-20230911214217757](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911214217757.png)

### 4.7.5 使用delete释放内存

**很重要**

![image-20230911214623780](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911214623780.png)

![image-20230911214731969](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911214731969.png)

### 4.7.6 使用new 来创建动态数组

 ![image-20230911215140608](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911215140608.png)

![image-20230911215057628](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911215057628.png)

**使用new创建动态数组**

![image-20230911225321674](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230911225321674.png)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912112903926.png" alt="image-20230912112903926" style="zoom:50%;" />

**使用动态数组**

![image-20230912113337342](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912113337342.png)

指针与数组名的区别：

![image-20230912113805640](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912113805640.png)

## 4.8 指针、数组和指针算术

![image-20230912114027994](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912114027994.png)

![image-20230912125024665](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912125024665.png)

整个数组的地址与第一个元素的地址

![image-20230912212712148](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912212712148.png)

```c++
short(*d)[10] = &b; //又在故弄玄虚，d是二级指针，**d是数组第一个元素
```

我理解了，这里的 &tell所指的整个数组的地址，和二维数组中（例如`e[10][10]`）中的`e[10]`是同一个东西

关于动态数组那里可能还没说明白

![image-20230912215315436](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912215315436.png)

如果不是因为这个动态数组，那么p[1]的值不应该为乱码值

这意味着，当new int[10]却只使用了4个值的时候，则代表剩余6个值都没有被使用并且将被回收

### 4.8.3 指针和字符串

![image-20230912220009176](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230912220009176.png)

即便这个字符的地址是一个指针变量

```c++
	char p[10] = "1234789";
	char* d = p;
	cout << d;
```

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914153435683.png" alt="image-20230914153435683" style="zoom:67%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914153604555.png" alt="image-20230914153604555" style="zoom:50%;" />

### 4.8.4 使用new创建动态结构

前言：

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914153855994.png" alt="image-20230914153855994" style="zoom: 50%;" />

这里的new与C#的类似，只不过C#一直对类使用new，实际上就是对类的对象进行内存的分配

这里是为指针分配内存

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914154423754.png" alt="image-20230914154423754" style="zoom:60%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914155714844.png" alt="image-20230914155714844" style="zoom:67%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914164044225.png" alt="image-20230914164044225" style="zoom:60%;" />

**自动存储**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914164946073.png" alt="image-20230914164946073" style="zoom:67%;" />

**静态存储**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914165056319.png" alt="image-20230914165056319" style="zoom:67%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914180037364.png" alt="image-20230914180037364" style="zoom:50%;" />

## 4.10 数组的替代品

### 4.10.1 模板类vector

![image-20230914181451216](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914181451216.png)

### 4.10.2 模板类array

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914183142133.png" alt="image-20230914183142133" style="zoom:67%;" />

### 4.10.3 比较数组、vector 对象和array对象

![image-20230914184126231](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914184126231.png)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230914185300481.png" alt="image-20230914185300481" style="zoom:50%;" />

同时也注意到，vector对象也可赋值给另一个vector对象

牺牲一定的效率换取安全性是很有助于开发提升效率的，至少不会错了找不到在哪

----

----

# 5 循环和关系表达式

