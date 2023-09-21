## 1.2 同步电路设计

### 1.2.1 触发器

#### 1. 关于时钟信号的解释

时钟信号在数字电路中起着非常重要的作用。它是一种特殊的信号，可以周期性地在两个电平（通常是高电平和低电平）之间切换。这种信号可以用来同步数字电路中的操作，使得这些操作可以在特定的时间点进行。

时钟信号与我们日常生活中的时钟有一定的相似性，都涉及到时间的度量和事件的同步。然而，它们在具体的应用和实现方式上有很大的不同。日常生活中的时钟用来度量时间，并帮助我们安排日常活动。而时钟信号则是数字系统中的一个基本元素，它并不直接度量现实世界中的时间，而是提供一个参考点，使得数字电路中的各种操作可以在正确的时刻进行。

例如，在微处理器中，时钟信号用来控制指令的执行顺序和速度。每一个时钟周期，处理器都会执行一定数量的操作。这就像我们日常生活中的时钟，每过一分钟或一小时，我们就会做一些事情（比如做饭、看电视等）。但是，这两者之间还是有很大的区别。微处理器中的时钟频率通常非常高，可以达到几十甚至几百兆赫兹，而我们日常生活中的时钟则相对较慢，通常以秒、分钟或小时为单位。

> 关于时钟信号的解释：一个常见的时钟信号的例子是微处理器中的时钟信号。微处理器是计算机的核心部件，它需要执行大量的指令。这些指令需要在特定的时间点执行，以确保数据的正确处理和传输。这就是时钟信号发挥作用的地方。
>
> 假设我们有一个运行在1GHz（即109赫兹）频率的微处理器。这意味着每秒钟，时钟信号会在高电平和低电平之间切换109次。我们可以将这个过程想象成一个非常快速的闪烁的灯泡：每当灯泡亮起（即时钟信号为高电平）时，微处理器就会执行一个指令；当灯泡熄灭（即时钟信号为低电平）时，微处理器就会等待下一个指令。
>
> 在这个例子中，时钟信号的上升沿（即从低电平跳变到高电平的瞬间）可能会触发微处理器读取并执行一个新的指令。而下降沿（即从高电平跳变到低电平的瞬间）则标志着当前指令的结束，并准备执行下一个指令。
>
> 通过精确地控制时钟信号，我们可以确保微处理器以正确和一致的速度执行指令，从而实现复杂的计算和数据处理任务。

#### 2. 关于上升沿和下降沿的解释

关于时钟信号的上升沿与下降沿：时钟信号的上升沿和下降沿是数字电路中非常重要的概念。

上升沿：当时钟信号从低电平跳变到高电平的瞬间，我们称之为上升沿。也就是说，它标志着信号的开始。

下降沿：相反，当时钟信号从高电平跳变到低电平的瞬间，我们称之为下降沿。它标志着信号的结束。

在数字电路中，上升沿和下降沿常常被用作触发条件，例如在触发器、计数器等时序逻辑电路中。这些电路在上升沿或下降沿到来时，会根据输入信号的状态进行相应的操作。这样，我们就可以通过控制时钟信号的频率和相位，来精确地控制数字电路的工作过程。

#### 3. 反相器

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230915223055914.png" alt="image-20230915223055914" style="zoom:50%;" />

#### 4. D触发器（重要）

**D触发器，也被称为数据触发器或延迟触发器，是一种具有记忆功能的逻辑电路单元⁵**。它有两个输入端，一个是数据输入端（D），另一个是时钟输入端（CLK）。**在时钟信号的上升沿，D触发器会读取并锁定D端的数据，并在下一个时钟上升沿之前将其输出⁴。在此期间，即使D端的数据发生变化，也不会直接影响到输出⁴。**

D触发器可以用作时序逻辑电路的记忆元件，因为它能够在特定的时钟周期内保持其状态¹。这使得D触发器能够存储一位二进制数据，从而在数字系统和计算机中有着广泛的应用⁵。

此外，D触发器还有许多不同的类型，比如带有异步复位、同步复位或使能端的D触发器¹。这些类型的D触发器在实际应用中可以满足不同的需求。例如，带有异步复位或置位功能的D触发器可以在任何时候立即将输出清零或置一¹；而带有同步清零功能的D触发器则只有在清零输入信号有效，并且时钟信号的有效边沿（如上升沿）到来时，才能将触发器清零¹；带有使能端的D触发器则可以通过控制使能信号来决定是否响应时钟信号¹。这些特性使得D触发器在实际应用中具有很大的灵活性。

Source: Conversation with Bing, 9/15/2023
(1) D触发器 (D-FF)详解_timerring的博客-CSDN博客. https://blog.csdn.net/m0_52316372/article/details/128879627.
(2) 时序电路——DFF再理解 - 知乎. https://zhuanlan.zhihu.com/p/372453668.
(3) D触发器 (D-FF)详解 - 知乎. https://zhuanlan.zhihu.com/p/603383032.
(4) 触发器(filp-flop)和触发器(trigger)有什么区别？ - 知乎. https://www.zhihu.com/question/431351553.
(5) フリップフロップ回路とは？種類とそれぞれの動作をわかり .... https://analogista.jp/flipflop/.

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230915223336260.png" alt="image-20230915223336260" style="zoom: 33%;" />

D触发器可以用作时序逻辑电路的记忆元件，是因为它可以在每个时钟周期内，保存一位二进制数据。你可以把它想象成一个小盒子，里面有一个开关。**当时钟信号上升时，盒子的门会打开，让你看到开关的状态是0还是1。这就是D触发器的输出。**当时钟信号下降时，盒子的门会关闭，不让你看到开关的状态。**这时，你可以用一个按钮来改变开关的状态，这就是D触发器的输入。但是，无论你怎么按按钮，都不会影响盒子的输出**，直到下一个时钟信号上升时，盒子的门再次打开。这样，**D触发器就能够在每个时钟周期内，保持一位二进制数据的状态**，直到下一个时钟周期开始。这就是为什么D触发器可以用作时序逻辑电路的记忆元件的原因。

#### 5. CMOS下DFF工艺

[在CMOS工艺下，D触发器（DFF）的结构通常由两个主要部分组成：传输门和反相器](https://zhuanlan.zhihu.com/p/406924643)[1](https://zhuanlan.zhihu.com/p/406924643)[。这两个部分共同形成了一个锁存器。然后，通过将两个这样的锁存器按照主从结构连接起来，就形成了完整的D触发器](https://zhuanlan.zhihu.com/p/372453668)[2](https://zhuanlan.zhihu.com/p/372453668)[3](https://zhuanlan.zhihu.com/p/603383032)。

[传输门在CMOS中是一个重要的组件，它可以根据控制信号的状态选择是否传递输入信号](https://zhuanlan.zhihu.com/p/406924643)[1](https://zhuanlan.zhihu.com/p/406924643)[。反相器则是CMOS电路中的基本元素，它可以实现逻辑“非”功能](https://zhuanlan.zhihu.com/p/120863919)[4](https://zhuanlan.zhihu.com/p/120863919)。

[在D触发器中，**第一个锁存器（主锁存器）在时钟信号为高电平时采集输入数据，而第二个锁存器（从锁存器）则在时钟信号为低电平时将采集到的数据输出**](https://zhuanlan.zhihu.com/p/372453668)[2](https://zhuanlan.zhihu.com/p/372453668)[3](https://zhuanlan.zhihu.com/p/603383032)[。这种结构确保了D触发器在一个时钟周期内能够完成数据的采集和输出](https://www.zhihu.com/question/282286149)[5](https://www.zhihu.com/question/282286149)。

[需要注意的是，在CMOS工艺中，每个逻辑门（包括传输门和反相器）都会引入一定的延时](https://www.zhihu.com/question/282286149)[5](https://www.zhihu.com/question/282286149)[。这就是为什么DFF有建立时间和保持时间要求的原因](about:blank#)[5](https://www.zhihu.com/question/282286149)[。建立时间是数据输入必须在时钟信号上升沿到来之前稳定的时间，而保持时间则是数据输入必须在时钟信号上升沿到来之后保持稳定的时间](https://www.zhihu.com/question/282286149)[5](https://www.zhihu.com/question/282286149)。这两个参数对于确保DFF正确工作至关重要。

#### 6. 传输门的原理

[传输门_百度百科 (baidu.com)](https://baike.baidu.com/item/传输门)

![传输门](https://bkimg.cdn.bcebos.com/pic/caef76094b36acaf579f5e477cd98d1001e99c0a?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_auto)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230915225254559.png" alt="image-20230915225254559" style="zoom:50%;" />

简单来讲，就是C端处于低电平——阻隔；C端处于高电平——导通

#### 7. 传输门在DFF中的作用

[在D触发器（DFF）中，传输门的主要作用是根据时钟信号的状态选择是否传递输入信号。在DFF中，传输门通常与反相器一起形成一个锁存器](https://zhuanlan.zhihu.com/p/406924643)[1](https://zhuanlan.zhihu.com/p/406924643)。

[当时钟信号为高电平时，传输门打开，允许输入信号通过并被反相器接收。反相器会对输入信号进行反转，并将反转后的信号输出到下一级的锁存器](https://zhuanlan.zhihu.com/p/406924643)[1](https://zhuanlan.zhihu.com/p/406924643)。

[当时钟信号为低电平时，传输门关闭，阻止输入信号的传递。此时，反相器保持其输出不变，即保持上一次接收到的输入信号的反转值](https://zhuanlan.zhihu.com/p/406924643)[1](https://zhuanlan.zhihu.com/p/406924643)。

[这样，通过前后两级锁存器的协同工作，DFF可以在一个时钟周期内完成数据的采集和输出](https://zhuanlan.zhihu.com/p/372453668)[2](https://zhuanlan.zhihu.com/p/372453668)[。具体来说，第一个锁存器（主锁存器）在时钟信号为高电平时采集输入数据，而第二个锁存器（从锁存器）则在时钟信号为低电平时将采集到的数据输出](https://zhuanlan.zhihu.com/p/372453668)[2](https://zhuanlan.zhihu.com/p/372453668)。

[需要注意的是，在CMOS工艺中，每个逻辑门（包括传输门和反相器）都会引入一定的延时](https://www.zhihu.com/question/282286149)[3](https://www.zhihu.com/question/282286149)[。这就是为什么DFF有建立时间和保持时间要求的原因](about:blank#)[3](https://www.zhihu.com/question/282286149)[。建立时间是数据输入必须在时钟信号上升沿到来之前稳定的时间，而保持时间则是数据输入必须在时钟信号上升沿到来之后保持稳定的时间](https://www.zhihu.com/question/282286149)[3](https://www.zhihu.com/question/282286149)。这两个参数对于确保DFF正确工作至关重要。

> 在书上，我看到CLKP在传输门的C端时，传输门是导通；CLKN在传输门的C端时，传输门是阻断
>
> [CLKN和CLKP是差分时钟信号的负相和正相，它们是一对互补的信号，用来提高时钟信号的抗干扰能力和减少信号摆幅](https://electronics.stackexchange.com/questions/284614/what-communication-protocol-does-this-pinout-match-datap-datan-clkp-clkn-cl)[1](https://electronics.stackexchange.com/questions/284614/what-communication-protocol-does-this-pinout-match-datap-datan-clkp-clkn-cl)[2](https://blog.csdn.net/wanglining1987/article/details/50202615)[3](https://e2echina.ti.com/support/processors/f/processors-forum/49609/6678-clkn-clkp)[。CLKN和CLKP之间的关系是：当CLKN为高电平时，CLKP为低电平；当CLKN为低电平时，CLKP为高电平。](https://blog.csdn.net/wanglining1987/article/details/50202615)

> 在CMOS电路中，传输门由一个n型MOSFET和一个p型MOSFET并联组成。对于n型MOSFET，当栅极电压高于源极电压时，它会导通；对于p型MOSFET，当栅极电压低于源极电压时，它会导通。
>
> 因此，当传输门的控制端（C端）接到CLKP（高电平）时，n型MOSFET导通，p型MOSFET截止，传输门导通；当控制端接到CLKN（低电平）时，n型MOSFET截止，p型MOSFET导通，传输门阻断。
>
> 这样，通过改变CLKP和CLKN的电平状态，可以控制传输门的开关状态，从而实现对输入信号的采集和输出。这是D触发器（DFF）工作的基本原理。

#### 8. DFF原理图与DFF结构

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230916185030793.png" alt="image-20230916185030793" style="zoom:67%;" />

DFF原理结构

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230916185105143.png" alt="image-20230916185105143" style="zoom:75%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230916190712434.png" alt="image-20230916190712434" style="zoom:50%;" />

这段话的意思是说，当我输入高电平的时候，如果信号的输入在传输门关闭之前发生了改变（传输门的关闭有延迟），那么将会把*本该下一次传入的信号*在这次一并输入，就会产生亚稳态，所以需要保持时间约束，让信号的输入D维持一段时间

> 在上沿信号到来的前一刻，如果输入不同的信号，就会产生干扰，就会导致信号不稳定，因为信号要回复正常需要一定时间
>
> 至于保持时间，是考虑到，时钟信号的时钟信号到达之后和传输门关闭之间的时间差。如果在这个时间差之内改变信号，就会导致不稳定的信号在传输门关闭之前混入输出端



### 1.2.3 时序分析

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230921202903508.png" alt="image-20230921202903508" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230921202937165.png" alt="image-20230921202937165" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230921203035590.png" alt="image-20230921203035590" style="zoom:50%;" />

接下来是解释

#### 1.同步逻辑设计

> [同步逻辑设计是指整个设计中只有一个全局时钟](https://bing.com/search?q=同步逻辑设计的定义)[[1]](https://bing.com/search?q=同步逻辑设计的定义)[。在同步逻辑设计中，所有的记忆元素（例如寄存器、RAM甚至锁存器等）都在被同一个时钟信号驱动，那么它们的输出都会同时变化，所以它们对数字电路的影响是同步的](https://zhuanlan.zhihu.com/p/265774015)[[2]](https://zhuanlan.zhihu.com/p/265774015)[。这是因为所有记忆元素都在被同一个时钟信号驱动，那么它们的输出都会同时变化，所以它们对数字电路的影响是同步的](https://zhuanlan.zhihu.com/p/265774015)[[3]](https://zhuanlan.zhihu.com/p/265774015)[。只有时钟脉冲同时到达各记忆元件的时钟端，才能发生预期改变](https://bing.com/search?q=同步逻辑设计的定义)[[4]](https://bing.com/search?q=同步逻辑设计的定义)[。同步逻辑是时钟之间有固定的因果关系](https://bing.com/search?q=同步逻辑设计的定义)[[5]](https://bing.com/search?q=同步逻辑设计的定义)[[6]](https://zhuanlan.zhihu.com/p/265774015)[。这种设计方法有利于静态时序分析](https://blog.csdn.net/qq_57148694/article/details/129788018)[3](https://blog.csdn.net/qq_57148694/article/details/129788018)[，但存在时钟偏斜问题](https://blog.csdn.net/qq_57148694/article/details/129788018)[[7]](https://blog.csdn.net/qq_57148694/article/details/129788018)。

#### 2.时钟偏斜

> [时钟偏斜（Clock Skew）是指同样的时钟产生的多个子时钟信号之间的延时差异](https://zhuanlan.zhihu.com/p/449845451)[1](https://zhuanlan.zhihu.com/p/449845451)[2](https://zh.wikipedia.org/wiki/时钟偏移)[3](https://www.cnblogs.com/zeushuang/archive/2012/07/04/2575849.html)[4](https://blog.csdn.net/u012158332/article/details/102831687)[。它表现的形式是多种多样的，既包含了时钟驱动器的多个输出之间的偏移，也包含了由于PCB走线误差造成的接收端和驱动端时钟信号之间的偏移](https://www.cnblogs.com/zeushuang/archive/2012/07/04/2575849.html)[3](https://www.cnblogs.com/zeushuang/archive/2012/07/04/2575849.html)[4](https://blog.csdn.net/u012158332/article/details/102831687)[。时钟偏斜指的是同一个时钟信号到达两个不同寄存器之间的时间差值，时钟偏斜永远存在，到一定程度就会严重影响电路的时序](https://www.cnblogs.com/zeushuang/archive/2012/07/04/2575849.html)[3](https://www.cnblogs.com/zeushuang/archive/2012/07/04/2575849.html)[4](https://blog.csdn.net/u012158332/article/details/102831687)。
>
> 时钟偏斜（Clock Skew）是指由于芯片中**时钟信号的传播延迟**和**分布不均**，导致不同部分（如逻辑门）之间的**时钟速度**存在差异。当这种延迟和速度差异足够大时，可能会导致数据传输错误或信号同步问题，从而影响电路的正确性和稳定性。
>
> 时钟偏斜分为两种类型：正时钟偏斜（Positive Clock Skew）和负时钟偏斜（Negative Clock Skew）。**当一部分电路的时钟信号比另一部分电路的时钟信号快时，称为正时钟偏斜**；**反之，当一部分电路的时钟信号比另一部分电路的时钟信号慢时，称为负时钟偏斜**。 时钟偏斜会影响**数字电路的性能和稳定性**，因此需要进行控制和管理。常用的方法包括使用**缓冲器（Buffer）**或**驱动器（Driver）**来调整时钟信号的幅度和相位，以及使用差分信号（Differential Signaling）或共模信号（Common Mode Signaling）来传输时钟信号等。/

然而，对FPGA来说，它受到的时钟偏斜较小

原因如下

> [FPGA（现场可编程门阵列）受时钟偏斜影响较小的原因主要是其内部设计和布线策略。在FPGA中，时钟信号通常通过专用的全局时钟网络进行分配，这种网络设计可以最大限度地减少时钟偏斜](https://blog.csdn.net/Reborn_Lee/article/details/84930353)[1](https://blog.csdn.net/Reborn_Lee/article/details/84930353)。
>
> [具体来说，由于时钟网络布线存在传输延迟，因此时钟偏斜是同一个时钟网络上的同一个时钟沿同时作用于源寄存器和目的寄存器时的相位差](https://blog.csdn.net/Reborn_Lee/article/details/84930353)[1](https://blog.csdn.net/Reborn_Lee/article/details/84930353)[。在FPGA中，由于布线资源的延迟是不可预测的，所以时钟网络布线应该使用FPGA提供的专用时钟资源](https://blog.csdn.net/Reborn_Lee/article/details/84930353)[1](https://blog.csdn.net/Reborn_Lee/article/details/84930353)。
>
> [此外，FPGA还采用了一种称为“时钟树”的技术来进一步降低时钟偏斜。简单地说，就是让时钟上“树”，时钟树可以使时钟到达各个寄存器的时钟偏斜最小](https://blog.csdn.net/Reborn_Lee/article/details/84930353)[1](https://blog.csdn.net/Reborn_Lee/article/details/84930353)[。这种设计使得与时钟信号相连的功能子模块的互连线大致等长，从而保障了到达各个寄存器的信号是相同的且不存在大的时钟偏斜](https://blog.csdn.net/Reborn_Lee/article/details/84930353)[1](https://blog.csdn.net/Reborn_Lee/article/details/84930353)。
>
> 因此，通过使用专用的全局时钟网络和采用“时钟树”技术，FPGA能够有效地控制和管理时钟偏斜，从而减少其对电路性能和稳定性的影响。
>
> FPGA的**时钟网络是由其内部时钟源通过缓冲器和分布器**产生的，其时钟偏斜主要受以下因素影响： 
>
> **缓冲器和分布器的性能**：FPGA内部通常包含许多缓冲器和分布器，它们会影响时钟信号的质量和分布。如果缓冲器和分布器的性能不理想，会导致时钟信号的幅度和相位不均匀，从而产生时钟偏斜。 
>
> **电路板的布局和布线**：当FPGA应用于电路板时，电路板的布局和布线会对时钟信号的传播产生影响。如果电路板的布局和布线不合理，会导致时钟信号的传播延迟和分布不均，从而产生时钟偏斜。 
>
> **时钟源的性能**：FPGA的时钟源通常是由石英晶体振荡器或PLL（相位锁定环）产生的。如果时钟源的性能不稳定或存在偏差，会导致时钟信号的质量和稳定性下降，从而产生时钟偏斜。 
>
> 由于FPGA的设计和制造过程中会采取多种措施来控制时钟偏斜，包括**优化缓冲器和分布器的设计、优化电路板的布局和布线、选择高性能的时钟源**等，因此FPGA通常具有相对较小的时钟偏斜。此外，FPGA还支持多种差分信号和共模信号的传输方式，可以进一步提高时钟信号的质量和稳定性。

#### 3.STA与DTA

STA（静态时序分析）和DTA（动态时序分析）都是电路设计中的重要概念，它们用于分析和验证电路的时序性能。下面我将详细解释这两个概念，并比较它们的区别。

[**STA（静态时序分析）**](https://bing.com/search?q=电路中的STA解释)[1](https://bing.com/search?q=电路中的STA解释)[2](https://blog.csdn.net/weixin_43701504/article/details/120922204)：

- [STA是一种在设计芯片的过程中使用的技术，主要用于预测和验证芯片在特定环境下的工作表现](https://bing.com/search?q=电路中的STA解释)[3](https://blog.csdn.net/cy413026/article/details/123667602)。
- [STA通过时序库文件给出的各条时序路径的延迟，来确认在每个触发器（Flip-Flop，简称FF）上是否满足建立/保持时间](https://blog.csdn.net/weixin_43701504/article/details/120922204)[1](https://bing.com/search?q=电路中的STA解释)[2](https://blog.csdn.net/weixin_43701504/article/details/120922204)。
- [STA是把设计划分为一系列时序路径，然后分析各条时序路径的建立、保持时间是否满足](https://blog.csdn.net/cy413026/article/details/123667602)[3](https://blog.csdn.net/cy413026/article/details/123667602)。
- [STA的优点是运算速度快，缺点是不能进行功能验证，并且会报出一些false的错误](https://blog.csdn.net/cy413026/article/details/123667602)[3](https://blog.csdn.net/cy413026/article/details/123667602)。

[**DTA（动态时序分析）**](https://bing.com/search?q=电路中的STA解释)[1](https://bing.com/search?q=电路中的STA解释)[2](https://blog.csdn.net/weixin_43701504/article/details/120922204)：

- [DTA需要给设计灌入激励在仿真的时候加上各元器件的延迟信息，然后分析设计在这些延迟信息下的正确与否](https://blog.csdn.net/weixin_43701504/article/details/120922204)[1](https://bing.com/search?q=电路中的STA解释)[2](https://blog.csdn.net/weixin_43701504/article/details/120922204)。
- [DTA可以进行功能验证以及时序要求](https://bing.com/search?q=电路中的STA解释)[4](http://www.vlsijunction.com/2015/10/sta-vs-dta.html)。
- [DTA需要一组全面的输入向量来检查设计中路径的时序特性](https://bing.com/search?q=电路中的STA解释)[4](http://www.vlsijunction.com/2015/10/sta-vs-dta.html)。

**STA与DTA的区别**：

- **[STA和DTA的主要区别在于分析电路时序时是否有输入激励](https://bing.com/search?q=电路中的STA解释)[1](https://bing.com/search?q=电路中的STA解释)[2](https://blog.csdn.net/weixin_43701504/article/details/120922204)。**
- **[STA只需要考虑最坏情况下的输入，而不需要考虑所有可能的输入组合。因此，STA可以更快地完成，通常用于设计过程中的初步时序检查](https://bing.com/search?q=电路中的STA解释)[3](https://blog.csdn.net/cy413026/article/details/123667602)。**
- [相比之下，DTA需要对所有可能的输入组合进行仿真，这通常需要大量的计算资源和时间](https://bing.com/search?q=电路中的STA解释)[4](http://www.vlsijunction.com/2015/10/sta-vs-dta.html)[。因此，DTA通常在设计完成后进行，以验证设计在所有可能情况下都能正常工作](https://bing.com/search?q=电路中的STA解释)[4](http://www.vlsijunction.com/2015/10/sta-vs-dta.html)。

**为什么STA更适合FPGA？**

[在FPGA中，STA（静态时序分析）和DTA（动态时序分析）都是用来验证数字集成电路时序是否合格的验证方法](https://zhuanlan.zhihu.com/p/345847896)[1](https://zhuanlan.zhihu.com/p/345847896)[2](https://www.synopsys.com/glossary/what-is-static-timing-analysis.html)。

[STA是一种方法，它通过检查所有可能的路径来验证设计的时序性能](https://www.synopsys.com/glossary/what-is-static-timing-analysis.html)[2](https://www.synopsys.com/glossary/what-is-static-timing-analysis.html)[。STA将设计分解为时序路径，计算每条路径上的信号传播延迟，并检查设计内部和输入/输出接口处的时序约束是否存在违规](https://www.synopsys.com/glossary/what-is-static-timing-analysis.html)[2](https://www.synopsys.com/glossary/what-is-static-timing-analysis.html)[。STA的前提是同步逻辑设计，不能分析异步电路](https://zhuanlan.zhihu.com/p/351786400)[3](https://zhuanlan.zhihu.com/p/351786400)[。**STA对所有的时序路径进行错误分析，不需要使用测试向量激活某个路径**](https://zhuanlan.zhihu.com/p/351786400)[3](https://zhuanlan.zhihu.com/p/351786400)[。这使得STA的分析速度比时序仿真工具快几个数量级，克服了动态时序验证的缺陷，适合大规模的电路设计验证](https://zhuanlan.zhihu.com/p/351786400)[3](https://zhuanlan.zhihu.com/p/351786400)[。在同步逻辑情况下，能够达到100%的时序路径覆盖](https://zhuanlan.zhihu.com/p/351786400)[3](https://zhuanlan.zhihu.com/p/351786400)。

[相比之下，DTA则是通过模拟输入刺激向量来确定电路的完整行为。然而，DTA只能检查被一组测试向量敏感化的时序路径，而不能像STA那样检查所有的时序路径](https://www.synopsys.com/glossary/what-is-static-timing-analysis.html)[2](https://www.synopsys.com/glossary/what-is-static-timing-analysis.html)。

[FPGA采用STA主要是因为它可以更快、更全面地进行时序分析。在高速系统中，FPGA的时序约束不仅包括内部时钟约束，还应包括完整的IO时序约束和时序例外约束才能实现PCB板级的时序收敛](https://zhuanlan.zhihu.com/p/345847896)[1](https://zhuanlan.zhihu.com/p/345847896)[4](https://www.cnblogs.com/lifan3a/articles/4385647.html)[。因此，仅有正确的约束才能在快速情况下保证FPGA和外部器件通信正确](https://zhuanlan.zhihu.com/p/345847896)[1](https://zhuanlan.zhihu.com/p/345847896)。

**STA能识别的时序故障**

静态时序分析能够识别的时序故障：**建立时间（Setup）/保持时间（Hold）/恢复时间（Recovery）/移除时间（Removal）**检查；最小跳变和最大跳变；时钟脉冲宽度、时钟畸变（Skew、Jitter）；总线竞争；不受约束的逻辑通道；关键路径；约束冲突等；

**STA的时序路径**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230921231850223.png" alt="image-20230921231850223" style="zoom:33%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230921231903231.png" alt="image-20230921231903231" style="zoom:33%;" />

#### 4.组合逻辑延迟

[在FPGA中，组合逻辑电路的延时主要是指数据从一个触发器（D触发器）的输出端，经过组合逻辑运算后，到达下一个触发器的输入端所需的时间](https://zhuanlan.zhihu.com/p/540137408)[1](https://zhuanlan.zhihu.com/p/540137408)[。这个时间包括了触发器的响应时间（即数据从触发器的输入端传输到输出端所需的时间）和组合逻辑电路的处理时间](https://zhuanlan.zhihu.com/p/418218293)[2](https://zhuanlan.zhihu.com/p/418218293)。

[例如，假设有两个D触发器D1和D2，它们之间有一段组合逻辑电路。当时钟信号的上升沿到来时，D1的输出数据会经过组合逻辑电路处理后输入到D2](https://zhuanlan.zhihu.com/p/540137408)[3](https://bing.com/search?q=FPGA中组合逻辑电路的延时是什么)。这个过程中，数据从D1的输出端到达D2的输入端所需的时间就是组合逻辑电路的延时。

[值得注意的是，FPGA中的延时还包括了走线延时，即数据在物理线路上传输所需的时间](https://zhuanlan.zhihu.com/p/540137408)[4](https://www.zhihu.com/question/36771917)[。在实际应用中，走线延时可能占总延时的60%～70%](https://zhuanlan.zhihu.com/p/540137408)[4](https://www.zhihu.com/question/36771917)。

[总的来说，FPGA中组合逻辑电路的延时是由触发器响应时间、组合逻辑处理时间以及走线延时共同决定的](https://zhuanlan.zhihu.com/p/540137408)[2](https://zhuanlan.zhihu.com/p/418218293)[4](https://www.zhihu.com/question/36771917)[。这个延时对于满足系统性能要求（如建立时间和保持时间）具有重要影响](https://zhuanlan.zhihu.com/p/418218293)[2](https://zhuanlan.zhihu.com/p/418218293)。

> 这里组合逻辑电路所说的处理时间，是实际上就是：
>
> [是的，组合逻辑电路的处理时间在某种程度上类似于CMOS电路的处理时效](https://en.wikipedia.org/wiki/CMOS)[1](https://en.wikipedia.org/wiki/CMOS)[2](https://zhuanlan.zhihu.com/p/595514197)[。在CMOS电路中，处理时效通常是指数据在CMOS电路中传输所需的时间](https://en.wikipedia.org/wiki/CMOS)[1](https://en.wikipedia.org/wiki/CMOS)[。这个时间取决于多个因素，包括电路的设计、晶体管的尺寸、供电电压以及负载电容等](https://en.wikipedia.org/wiki/CMOS)[1](https://en.wikipedia.org/wiki/CMOS)。
>
> [同样，在组合逻辑电路中，处理时间也是指数据在电路中传输所需的时间](https://zhuanlan.zhihu.com/p/595514197)[2](https://zhuanlan.zhihu.com/p/595514197)[。这个时间同样取决于多个因素，包括电路的设计、使用的逻辑门类型（如AND门、OR门等）、逻辑门的数量以及互连线的长度等](https://zhuanlan.zhihu.com/p/595514197)[2](https://zhuanlan.zhihu.com/p/595514197)。
>
> [因此，我们可以说，组合逻辑电路的处理时间和CMOS电路的处理时效都是描述数据在电路中传输所需的时间。但是，具体的计算方法和影响因素可能会有所不同](https://en.wikipedia.org/wiki/CMOS)[1](https://en.wikipedia.org/wiki/CMOS)[2](https://zhuanlan.zhihu.com/p/595514197)。

**至于触发器的响应时间**

[触发器的响应时间，也被称为传输延迟时间（Propagation delay time），是指当时钟有效沿变化后，数据从输入端到输出端的最小时间间隔](https://www.zhihu.com/question/35128735)[1](https://www.zhihu.com/question/35128735)[。这个概念在一些文献中也被称为“从时钟到Q的标准传播延迟。换句话说，它是数据从触发器的输入端传输到输出端所需的时间](https://www.zhihu.com/question/35128735)[2](https://bing.com/search?q=触发器的响应时间是什么)[。这个时间是由触发器的内部结构和工作原理决定的，包括晶体管的开关速度、电路的设计等因素](https://www.zhihu.com/question/35128735)[2](https://bing.com/search?q=触发器的响应时间是什么)[。在实际应用中，触发器的响应时间对于系统性能有重要影响，例如在高速数字系统中，响应时间越短，系统的工作频率就可以越高](https://www.zhihu.com/question/35128735)[2](https://bing.com/search?q=触发器的响应时间是什么)[。因此，在设计数字系统时，选择具有适当响应时间的触发器是非常重要的](https://www.zhihu.com/question/35128735)[2](https://bing.com/search?q=触发器的响应时间是什么)。

#### 5.重新认识建立时间和保持时间概念

[【学习笔记】详解！建立时间和保持时间概念，fpga基础知识。 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/418218293)