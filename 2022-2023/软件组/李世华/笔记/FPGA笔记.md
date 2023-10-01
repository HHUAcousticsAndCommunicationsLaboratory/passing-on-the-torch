# 一. 逻辑电路基础

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

我们重温一下，为什么需要建立时间和保持时间

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230922212252441.png" alt="image-20230922212252441" style="zoom:50%;" />

**建立时间**：[在建立时间内，数据信号确实已经到达了主锁存器](https://www.runoob.com/w3cnote/verilog2-setup-hold-time.html)。如果输入信号发生变化，那么已经到达主锁存器的数据信号可能会受到新的信号的干扰。**建立时间确保了在时钟有效沿（例如上升沿）到来之前，数据输入端信号已经保持稳定一段足够长的时间**。这样，当时钟信号到来时，我们可以确保锁存器内部的数据是稳定和正确的。如果没有足够的建立时间，那么锁存器可能会采样到错误的数据，导致系统运行不稳定

**保持时间：**由于**传输门的关闭会有延迟**，如果在时钟信号到来之后而传输门关闭之前，输入干扰信号，那么这时候干扰信号也会一同进到锁存器中，干扰已经存在的信号。

#### 6.两个触发器相连接

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230922214509107.png" alt="image-20230922214509107" style="zoom:50%;" />

首先我们要理解一个东西，就是D触发器到底是个什么东西。它是**时序逻辑电路的重要组成部分**。那什么是时序？就是**有记忆**。没错，触发器就是记忆器件。怎么记忆的？如果说在一个时钟周期内，所有触发器都在传递一个信号，那还叫记忆吗？因此，每个触发器都在输出自身上一次接到的信号。

- 如图的两个触发器，设依次经过3个时钟周期，分别是T1、T2和T3。
- 那么D1将T2周期内的信号传出给D2的接收端，并且自身接收T3周期内的信号
- 同时，D2将T1周期内的信号（D1传递过来的）传给下一个触发器的接收端，自身接收T2周期内的信号。



**接下来将分析触发器之间的时域关系**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230922224548983.png" alt="image-20230922224548983" style="zoom:65%;" />

> **华为题目：时钟周期为T，触发器D1的建立时间最大为T1max，最小为T1min。组合逻辑电路最大延迟为T2max，最小为T2min。问：触发器D2的建立时间T3和保持时间T4应满足什么条件？**

设以下变量

- `Tco`：触发器的响应时间
- `T1su`：D1的建立时间，范围为(T1min, T1max)
- `Tcomb`：组合逻辑延时（从一个触发器的**输出端**到另一个触发器**输入端**的时间）
- `Tdata`：数据稳定时间（即保持该数据**稳定不变**且持续地输出到**触发器D2的输入端**）
- `T2su`：D2的建立时间
- `T2ho`：D2的保持时间
- `Tclk`：时钟周期

1. 对于D2的建立时间，要求数据保持稳定，因此要有 `Tdata > T2su `

   又因为 `Tdata = Tclk - Tco -Tcomb` ，所以对于`T2su ` ，有 `Tclk - Tco -Tcomb > T2su`

2. 对于D2的保持时间，即`T2ho`，我们要认识到一点，此时D2正准备接收上一次的信号。因此在D2接收完成上一次信号之前（即D-FF的工作状态还没有彻底从 `CLK=0` 切换到 `CLK=1` ），数据还不能到达D2的输入端，否则会造成上一次信号与这次信号的混乱，从而导致数据错误。

   由于 `Tcomb` 时间末端时信号会到达D2的输入端，所以 `T2ho` 必须在那之前结束（即D2必须在那之前就得把状态切换完成）

   所以有  `Tco + Tcomb > T2ho `

### 1.2.4 单相时钟同步电路

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923100722113.png" alt="image-20230923100722113" style="zoom:50%;" />

**解释：**

#### 1. **什么是延迟分析的起点和重点必须基于同一时钟的FF？**

> 在数字电路设计中，触发器（Flip-Flop，FF）的主要作用是存储和传输数据。当时钟信号的一个特定边沿（例如上升沿或下降沿）到达FF时，FF会在其输入端捕获数据，并在下一个时钟周期将数据从其输出端发送出去。
>
> 因此，在进行静态时序分析（STA）时，我们通常将**FF的输出端视为路径的"起点"**，因为这是数据开始传输的地方。同样，我们将另一个F**F的输入端视为路径的"终点"**，因为这是数据结束传输的地方。
>
> 换句话说，**当我们说"起点"和"终点"时，我们实际上是在讨论数据在电路中传输的路径。**这条路径从一个FF的输出端开始，经过一系列逻辑门，然后结束于另一个FF的输入端。**我们通过计算这条路径上的总延迟来验证电路的时序性能。**

#### 2.**为什么这条路径上的总延时不包括FF的传输耗时？**

> 在进行静态时序分析（STA）时，我们通常关注的是FF之间的数据传输路径，这包括从一个FF的输出端到另一个FF的输入端的所有逻辑门和互连线的延迟。这是因为在同步数字系统中，数据在时钟周期内从一个存储元件（如FF）传输到另一个存储元件。
>
> 而FF本身的传输耗时（即数据从FF的输入端到输出端的时间）通常被视为下一个时钟周期的一部分。换句话说，**当时钟信号的一个特定边沿（例如上升沿或下降沿）到达FF时，FF会在其输入端捕获数据，并在下一个时钟周期将数据从其输出端发送出去。因此，FF的传输耗时实际上已经被包含在下一个时钟周期中，而不是当前路径的延迟计算中。**

#### 3. **什么是反相时钟**

> "反相时钟"是一个在数字电路设计中常用的术语，它指的是一个与原始时钟信号相位或边沿方向相反的时钟信号。简单来说，**如果我们有一个时钟信号，它在某个时间点从0变为1（这被称为上升沿），那么反相时钟就是在同一时间点从1变为0（这被称为下降沿）。**
>
> 你可以把它想象成两个人在跑步，一个人在上坡时加速，另一个人在上坡时减速，然后在下坡时加速。这两个人的速度变化是相反的，就像原始时钟和反相时钟的边沿方向是相反的。
>
> 然而，**在进行静态时序分析（STA）时，我们通常只考虑同一边沿（例如上升沿或下降沿）驱动的电路。**这是因为我们希望所有的数据都能在同一时间点被捕获和传输，这样可以简化时序分析和设计过程。因此，尽管反相时钟在某些情况下可能有用，但在大多数情况下，我们都倾向于使用单一的、同相的时钟信号。

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923101554921.png" alt="image-20230923101554921" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923101604808.png" alt="image-20230923101604808" style="zoom:50%;" />

#### 4. **什么是时钟抖动**（时钟偏移已经解释过了）

> [时钟抖动，也被称为"Jitter"，是指在数字电路中，同一时钟信号在相邻周期间时间不一致的现象](https://bing.com/search?q=时钟抖动是什么)[1](https://bing.com/search?q=时钟抖动是什么)[。这种现象通常是由于时钟信号本身在传输过程中的一些偶然和不定的变化所引起的](https://bing.com/search?q=时钟抖动是什么)[1](https://bing.com/search?q=时钟抖动是什么)。
>
> 让我们用一个简单的例子来解释这个概念。假设你有一个非常精确的手表，每秒都会滴答一次。在理想情况下，每个滴答之间的时间间隔应该是完全相同的。但是，如果你仔细观察，可能会发现实际上每个滴答之间的时间间隔并不完全相同。有时候可能会稍微快一点，有时候可能会稍微慢一点。这就是时钟抖动。
>
> [在数字电路中，时钟抖动可能由多种因素引起，包括晶振、锁相环（PLL）电路的偏差、噪声、干扰以及电源变化等](https://bing.com/search?q=时钟抖动是什么)[1](https://bing.com/search?q=时钟抖动是什么)。例如，如果电源电压发生波动，或者电路内部的温度发生变化，都可能影响到时钟信号的稳定性，从而导致时钟抖动。
>
> 需要注意的是，时钟抖动可能会对数字系统的性能产生影响。例如，在高速通信系统中，如果时钟抖动过大，可能会导致数据传输错误。因此，在设计数字电路时，需要采取一些措施来控制和减小时钟抖动。

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923102008467.png" alt="image-20230923102008467" style="zoom:50%;" />

#### 5. 什么是时钟树

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923104059076.png" alt="image-20230923104059076" style="zoom:50%;" />

[时钟树是一个由**许多缓冲单元**（buffer cell）平衡搭建的网状结构，它有一个源点，一般是时钟输入端（clock input port），也有可能是设计内部某一个单元输出脚（cell output pin）。然后就是由一级一级的缓冲单元搭建而成，具体的多少级，根据你的设置以及所使用的单元而定](https://baike.baidu.com/item/时钟树/5475673)[1](https://baike.baidu.com/item/时钟树/5475673)。

[在理想的同步电路中，我们认为同一个时钟域中的所有寄存器的时钟边沿同时到达。**但是在实际的电路中，这是不可能实现的**，因此就需要对时钟域中的时钟信号进行管理，也就是采用时钟树了。**时钟树可以保证时钟域中的寄存器的时钟边沿偏最小，从而保证良好的时序特性**](https://zhuanlan.zhihu.com/p/190240221)[2](https://zhuanlan.zhihu.com/p/190240221)。

[此外，我们知道时钟信号的驱动能力是有限的，若一个时钟域中包含数量较多的FF（Flip-Flop），那么时钟信号是难以独立地做到这么大的扇出（Fan-out）的。**而时钟树则可以通过缓存器（clock buffer）来管理大量的扇出**](https://zhuanlan.zhihu.com/p/190240221)[2](https://zhuanlan.zhihu.com/p/190240221)。

[总结一下，**时钟树并不是用来缩短时钟信号到达各个寄存器的时间，而且保证这些寄存器之间的时间差最小**。这样，如果时钟仅驱动1个FF,那么就没有时间差这个概念了，也就不需要采用时钟树了](https://zhuanlan.zhihu.com/p/190240221)[2](https://zhuanlan.zhihu.com/p/190240221)。所以说，有了时钟树，我们就可以更好地管理和控制电路中各个部分的运行时间，从而提高整体性能。

> 插入小曲：寄存器和DFF的关系
>
> [寄存器是CPU内部的一种非常快速的存储器件，用于暂时存放CPU执行指令和数据的地方](https://baike.baidu.com/item/寄存器/187682)[1](https://baike.baidu.com/item/寄存器/187682)[2](https://zhuanlan.zhihu.com/p/617364302)[。它位于CPU芯片内部，是CPU的一部分。由于寄存器与CPU内部的总线相连，访问速度非常快，通常仅需要一个时钟周期即可完成数据的读取和写入](https://zhuanlan.zhihu.com/p/617364302)[2](https://zhuanlan.zhihu.com/p/617364302)[。寄存器被广泛用于存储CPU执行指令和计算过程中的临时数据，以及保存程序状态等](https://baike.baidu.com/item/寄存器/187682)[1](https://baike.baidu.com/item/寄存器/187682)[2](https://zhuanlan.zhihu.com/p/617364302)。
>
> [D触发器（D Flip-Flop）是一种基本的触发器类型，它具有两个稳定状态，可以用来存储一位二进制信息](https://zhuanlan.zhihu.com/p/603383032)[3](https://zhuanlan.zhihu.com/p/603383032)[。当D触发器接收到一个时钟信号（通常是一个上升沿或下降沿）时，它会将输入端（D端）的状态复制到输出端（Q端）。在下一个时钟信号到来之前，输出端的状态将保持不变](https://zhuanlan.zhihu.com/p/603383032)[3](https://zhuanlan.zhihu.com/p/603383032)。
>
> **寄存器和D触发器之间的关系在于，寄存器通常由多个D触发器级联构成**。每个D触发器可以存储一位二进制信息，因此，例如，一个8位寄存器就会包含8个D触发器。这样，寄存器就可以在每个时钟周期内存储和传输更多的信息

关于时钟树中说到的

> [缓冲单元的工作原理基于以下两个关键元件：振荡器和驱动器](https://www.eefocus.com/baike/481152.html)[3](https://www.eefocus.com/baike/481152.html)[。首先，振荡器会产生一个时钟信号，在时钟周期内通过由管脚控制的开关将电荷积累在输出端上，从而形成时钟信号的矩形波形](https://www.eefocus.com/baike/481152.html)[3](https://www.eefocus.com/baike/481152.html)[。其次，驱动器接收来自振荡器的时钟信号，经过放大电路放大后，将放大后的时钟信号传递给后续的电路系统](https://www.eefocus.com/baike/481152.html)[3](https://www.eefocus.com/baike/481152.html)。

---

## 1.4 FPGA专业术语

### ASIC

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923105952442.png" alt="image-20230923105952442" style="zoom:50%;" />

### ASSP

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110008581.png" alt="image-20230923110008581" style="zoom:50%;" />

### CPLD

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110035123.png" alt="image-20230923110035123" style="zoom:50%;" />

### DLL

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110126072.png" alt="image-20230923110126072" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110248095.png" alt="image-20230923110248095" style="zoom:50%;" />

### DSP

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110611639.png" alt="image-20230923110611639" style="zoom:50%;" />

### EDA

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110726779.png" alt="image-20230923110726779" style="zoom:50%;" />

### EEPROM

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110808471.png" alt="image-20230923110808471" style="zoom:50%;" />

### EPROM

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110841778.png" alt="image-20230923110841778" style="zoom:50%;" />

### FPGA

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110914822.png" alt="image-20230923110914822" style="zoom:50%;" />

### IP

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923110956639.png" alt="image-20230923110956639" style="zoom:50%;" />

### LUT/查找表

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923111237495.png" alt="image-20230923111237495" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923112031094.png" alt="image-20230923112031094" style="zoom:50%;" />

### LVDS

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923112100737.png" alt="image-20230923112100737" style="zoom:50%;" />

### PLD

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923112119200.png" alt="image-20230923112119200" style="zoom:50%;" />

### PLL

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923112305638.png" alt="image-20230923112305638" style="zoom:50%;" />

DLL与PLL对时钟信号的处理的不同，是不是在于，DLL是通过延迟的方式进行的，而PLL则是产生新的相似并符合需要的信号？

> [您的理解是正确的。在集成电路中，**DLL（Delay Locked Loop）**和**PLL（Phase Locked Loop）**都是用于同步信号的电路，但它们的工作原理和应用有所不同](https://zhuanlan.zhihu.com/p/459240199)[1](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)[2](https://zhuanlan.zhihu.com/p/459240199)[3](https://blog.csdn.net/CLL_caicai/article/details/104975930)[4](https://blog.csdn.net/vivid117/article/details/108102272)[5](https://www.cnblogs.com/l20902/p/10610944.html)。
>
> [**DLL**是通过调整信号之间的延迟来同步信号的电路](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)[1](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)[。它基于数字抽样方式，在输入时钟和反馈时钟之间插入延迟，使输入时钟和反馈时钟的上升沿一致来实现的](https://zhuanlan.zhihu.com/p/459240199)[2](https://zhuanlan.zhihu.com/p/459240199)[。DLL主要用于存储器接口应用](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)[1](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)。
>
> [相比之下，**PLL**是通过调整信号的频率和相位来同步信号的电路](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)[1](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)[。它由鉴相器（PD）、环路滤波器（LPF）和压控振荡器（VCO）组成，锁相环的基本配置是将参考信号和可调反馈信号的相位进行比较](https://zhuanlan.zhihu.com/p/459240199)[2](https://zhuanlan.zhihu.com/p/459240199)[。PLL并不是直接对晶振进行倍频，而是将频率稳定的晶振作为基准信号，与PLL内部振荡电路生成的信号分频后进行比较，使PLL输出的信号频率稳定](https://zhuanlan.zhihu.com/p/459240199)[2](https://zhuanlan.zhihu.com/p/459240199)[。PLL用于各种应用，包括频率合成和时钟恢复](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)[1](https://bing.com/search?q=集成电路中+DLL+与+PLL+的区别)。
>
> [总的来说，DLL和PLL都可以实现倍频、分频、占空比调整，但是PLL调节范围更大](https://blog.csdn.net/CLL_caicai/article/details/104975930)[3](https://blog.csdn.net/CLL_caicai/article/details/104975930)[。此外，由于DLL是数字电路，因此对电源噪声不敏感；而由于PLL是模拟电路，因此对电源噪声敏感](https://zhuanlan.zhihu.com/p/459240199)[2](https://zhuanlan.zhihu.com/p/459240199)[3](https://blog.csdn.net/CLL_caicai/article/details/104975930)。

### HDL

[HDL，全称为硬件描述语言（Hardware Description Language），是一种用于描述数字系统硬件的结构和行为的语言](https://www.elecfans.com/bandaoti/eda/202008261280669.html)[1](https://www.elecfans.com/bandaoti/eda/202008261280669.html)[。它以文本形式来表示逻辑电路图、逻辑表达式，还可以表示数字逻辑系统所完成的逻辑功能](https://www.elecfans.com/bandaoti/eda/202008261280669.html)[1](https://www.elecfans.com/bandaoti/eda/202008261280669.html)。

[在世界上，最流行的两种硬件描述语言是Verilog HDL和VHDL，都是在20世纪80年代中期开发出来的](https://www.elecfans.com/bandaoti/eda/202008261280669.html)[1](https://www.elecfans.com/bandaoti/eda/202008261280669.html)。

- **Verilog HDL**：它是一种用于描述、设计和验证复杂的电子系统（包括模拟、数字和混合信号系统）的硬件描述语言。Verilog HDL提供了一种描述数字系统（如微处理器和微控制器）的方法，这种方法既可以在行为级别进行描述，也可以在门级别或开关级别进行描述。
- **VHDL**：全称为VHSIC硬件描述语言（VHSIC Hardware Description Language）。VHSIC是超大规模集成电路（Very High Speed Integrated Circuit）的缩写。VHDL是一种强大的硬件描述语言，用于电子系统的建模和仿真。它不仅可以描述数字电路，还可以描述混合信号电路和模拟电路。

这两种语言都有各自的优点，选择使用哪一种取决于特定的设计需求和个人偏好。

### RTL

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923112841566.png" alt="image-20230923112841566" style="zoom:50%;" />

> [RTL，全称为寄存器传输级（Register Transfer Level），是一种对同步数字电路的抽象模型](https://zh.wikipedia.org/zh-hans/寄存器传输级)[1](https://zh.wikipedia.org/zh-hans/寄存器传输级)[。这种模型是根据数字信号在硬件寄存器、存储器、组合逻辑装置和总线等逻辑单元之间的流动，以及其逻辑代数运作方式来确定的](https://zh.wikipedia.org/zh-hans/寄存器传输级)[1](https://zh.wikipedia.org/zh-hans/寄存器传输级)。
>
> [在RTL级别，我们不关注寄存器和组合逻辑的细节（如使用了多少逻辑门，逻辑门之间的连接拓扑结构等），而是通过描述寄存器到寄存器之间的逻辑功能来描述电路的HDL层次](https://blog.csdn.net/hqzl225411/article/details/117819843)[2](https://blog.csdn.net/hqzl225411/article/details/117819843)[。这意味着，我们在RTL代码中“画”出输入输出端口，各级寄存器，寄存器之间的组合逻辑和前三者之间的连接](https://www.zhihu.com/question/357997056)[3](https://www.zhihu.com/question/357997056)[。对于组合逻辑，只需要软件级描述，将其功能包装在“黑匣子”中即可，无需考虑其门级结构](https://www.zhihu.com/question/357997056)[3](https://www.zhihu.com/question/357997056)。
>
> [RTL级别是比门级更高的抽象层次，使用RTL级语言描述硬件电路一般比门级描述简单高效得多](https://blog.csdn.net/hqzl225411/article/details/117819843)[2](https://blog.csdn.net/hqzl225411/article/details/117819843)[。因此，RTL设计已经成为了数字电路设计的主流方法](https://www.zhihu.com/question/34368978)[4](https://www.zhihu.com/question/34368978)[。然而，随着技术的发展，更高层次的抽象设计方法，如C/C++综合也正在逐步发展并被应用于实践中](https://www.zhihu.com/question/34368978)[4](https://www.zhihu.com/question/34368978)。

> 在这里，“抽象度更高”是指在描述电路时，我们不需要关注电路的具体实现细节，而是关注其功能和行为。
>
> 例如，当我们在寄存器传输级（RTL）描述电路时，**我们只需要知道数据是如何从一个寄存器传输到另一个寄存器的，而不需要知道这个过程中使用了多少逻辑门，这些逻辑门是如何连接的等等**。这就是一种抽象，因为我们忽略了一些细节，只关注了我们感兴趣的部分。
>
> 同样，当我们在更高层次（比如行为级）描述电路时，我们甚至可以**忽略寄存器**的存在，**只需要描述电路的输入和输出之间的关系。这就是更高层次的抽象。**
>
> 总的来说，“抽象度更高”就是说我们在描述电路时，可以忽略更多的实现细节，只关注电路的功能和行为。

> 您的理解是非常准确的。**在编程语言中，"封装"是一种隐藏实现细节，只暴露接口（或者说功能）的方法。**这样，使用者就可以不需要知道具体的实现方式，只需要知道如何使用这个接口就可以了。
>
> 同样，在硬件描述语言中，**我们也可以通过提高抽象层次来隐藏电路的实现细节，只关注电路的功能和行为**。这样，设计师就可以专注于设计电路的整体架构和功能，而不需要关心每一个逻辑门的连接方式。
>
> 所以，**你可以把提高抽象层次看作是硬件设计中的"封装"。这两者都是为了让设计更加简洁、高效和可管理。**

### SERDER

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923113612593.png" alt="image-20230923113612593" style="zoom:50%;" />

> 是的，您的理解是正确的。在数字系统中，数据可以以并行或串行的方式进行传输。
>
> **并行传输**是指在同一时间内，通过多个通道同时传输数据的各个位。这种方式的优点是传输速度快，因为多个位可以同时传输。然而，这种方式也有一些缺点，例如需要更多的物理线路，且在长距离传输时可能会出现信号同步问题。
>
> 相比之下，**串行传输**是指在同一时间内，通过单一通道依次传输数据的各个位。这种方式的优点是只需要少量的物理线路，且可以支持长距离传输。然而，由于数据位是依次传输的，所以串行传输的速度通常比并行传输慢。
>
> 因此，在实际应用中，我们可能会根据具体需求选择使用并行传输或串行传输。例如，在处理器内部，由于距离短且线路资源充足，通常使用并行传输以提高速度。而在处理器与外部设备（如硬盘、网络设备等）之间的通信中，则可能选择使用串行传输，以减少线路资源的使用和支持长距离传输。
>
> 总的来说，将并行数据转换为串行数据（或者反过来），是为了在满足系统需求（如速度、距离、资源等）的同时，实现数据的有效传输。

### LSI

[LSI，全称为大规模集成电路（Large-Scale Integration），是一种在微电子领域中使用的概念，指将大量数目的晶体管和其他电子元件集成在一个单一的芯片上](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)[。这项技术被广泛应用于电子设备中，很大程度上促进了计算机、通信和其他电子产品的发展](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)。

[大规模集成电路技术最早于20世纪60年代发明，初始目的是实现更高的电路密度和更好的性能](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)[。在早期，集成电路中的晶体管数量通常在几十或几百个之内。但随着技术的不断发展，现代的大规模集成电路中通常包含数亿个晶体管](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)。

[随着集成电路技术的不断发展，LSI已经被进一步扩展为超大规模集成电路（Very-Large-Scale Integration，VLSI）和超超大规模集成电路（Ultra-Large-Scale Integration，ULSI）](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)[。这项技术的不断发展和应用，使得计算机的速度和性能得以不断提升，同时也推动了电子产品的快速发展](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)。

[总的来说，LSI是一项非常重要的制造技术，是现代电子设备和计算机技术的基础](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)[。随着电子产品的不断普及和发展，LSI技术还将不断地向更高级别的VLSI、ULSI发展，用于实现更强大、更智能化的电子设备和计算机系统](https://zhuanlan.zhihu.com/p/620810858)[1](https://zhuanlan.zhihu.com/p/620810858)。

<iframe class="frame" src="https://www.bing.com/search?showonlyads=1&amp;codex_conid=51D%7CBingProd%7C661FC7EAB81EE8C8E11E8B51386A057E89E0ABFB83366E7303A338F94BE9E01C&amp;codex_summ=%5B%7B%22author%22%3A%22bot%22%2C%22text%22%3A%22Generating+answers+for+you...%22%7D%2C%7B%22author%22%3A%22bot%22%2C%22text%22%3A%22Searching+the+web+for%3A+%60%E9%9B%86%E6%88%90%E7%94%B5%E8%B7%AF%E4%B8%AD+DLL+%E4%B8%8E+PLL+%E7%9A%84%E5%8C%BA%E5%88%AB%60%22%7D%2C%7B%22author%22%3A%22user%22%2C%22text%22%3A%22%E5%9C%A8%E9%9B%86%E6%88%90%E7%94%B5%E8%B7%AF%E4%B8%AD%EF%BC%8CDLL%E4%B8%8EPLL%E5%AF%B9%E6%97%B6%E9%92%9F%E4%BF%A1%E5%8F%B7%E7%9A%84%E5%A4%84%E7%90%86%E7%9A%84%E4%B8%8D%E5%90%8C%EF%BC%8C%E6%98%AF%E4%B8%8D%E6%98%AF%E5%9C%A8%E4%BA%8E%EF%BC%8CDLL%E6%98%AF%E9%80%9A%E8%BF%87%E5%BB%B6%E8%BF%9F%E7%9A%84%E6%96%B9%E5%BC%8F%E8%BF%9B%E8%A1%8C%E7%9A%84%EF%BC%8C%E8%80%8CPLL%E5%88%99%E6%98%AF%E4%BA%A7%E7%94%9F%E6%96%B0%E7%9A%84%E7%9B%B8%E4%BC%BC%E5%B9%B6%E7%AC%A6%E5%90%88%E9%9C%80%E8%A6%81%E7%9A%84%E4%BF%A1%E5%8F%B7%22%7D%5D&amp;IG=EA1EEBBDE24F48B3AC0C4F190E3BE865&amp;IID=SERP.5028&amp;cw=1225&amp;ch=601&amp;form=codexx&amp;dissrchswrite=1&amp;kseed=12000&amp;SFX=11&amp;q=LSI+%E6%98%AF%E4%BB%80%E4%B9%88&amp;iframeid=0ced4714-54f5-99cc-efcd-1d7c3f0deb8c&amp;cdxpc=SERP&amp;codex_src=sq" style="width: 0px; height: 0px;"></iframe>

### SoC

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923114241240.png" alt="image-20230923114241240" style="zoom:50%;" />

### SPLD

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923173049661.png" alt="image-20230923173049661" style="zoom:50%;" />

### SRAM

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923173802732.png" alt="image-20230923173802732" style="zoom:50%;" />

### 反熔丝

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923173831741.png" alt="image-20230923173831741" style="zoom:50%;" />

### 嵌入式阵列

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923174207914.png" alt="image-20230923174207914" style="zoom:50%;" />

### 时钟树

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923193741127.png" alt="image-20230923193741127" style="zoom:50%;" />

### 门阵列

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923193833220.png" alt="image-20230923193833220" style="zoom:50%;" />

### 高层次综合

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923194600107.png" alt="image-20230923194600107" style="zoom:50%;" />

### 结构化ASIC

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923194638301.png" alt="image-20230923194638301" style="zoom:50%;" />

### 标准单元ASIC

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923200714774.png" alt="image-20230923200714774" style="zoom:50%;" />

### 软核处理器

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201043623.png" alt="image-20230923201043623" style="zoom:50%;" />

> [软核处理器和硬核处理器的主要区别在于它们的实现方式和性能](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[2](https://zhidao.baidu.com/question/12912986.html)[3](https://bing.com/search?q=软核处理器和硬核处理器区别)[4](https://blog.csdn.net/howardhaowang/article/details/105041104)[5](https://blog.csdn.net/u014470361/article/details/81390365)[6](https://cloud.tencent.com/developer/article/1663709)。
>
> - [**软核处理器**：软核处理器是使用FPGA的逻辑和资源搭建的一个CPU系统](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[。由于是使用FPGA的通用逻辑搭建的CPU，因此具有一定的灵活性，用户可以根据自己的需求对CPU进行定制裁剪，增加一些专用功能，例如除法或浮点运算单元，用于提升CPU在某些专用运算方面的性能，或者删除一些在系统里面使用不到的功能，以节约逻辑资源](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[。另外也可以根据用户的实际需求，为CPU添加各种标准或定制的外设，例如 UART ，SPI，I IC 等标准接口外设](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[。然而，由于软核CPU是使用FPGA的通用逻辑资源搭建的，相较使用经过布局布线优化的硬核处理器来说，软核处理器能运行的最高实时钟主频要低一些，而且也会相应地消耗较多的FPGA逻辑资源以及片上存储器资源](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)。
> - [**硬核处理器**：硬核处理器是在芯片设计之初，就在内部的硬件电路上添加了硬核处理器](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[。它是纯硬件实现的，不会消耗FPGA的逻辑资源](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[。硬核处理器和FPGA逻辑在一定程度上是相互独立的](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[。例如比较有名的Xilinx的ZYNQ/PYNQ系列集成ARM Cortex-A9处理器，同时具有ARM软件的可编程性和FPGA 的硬件可编程性](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)[。由于片上的ARM处理器是经过布局布线的硬线逻辑，因此其能工作的时钟主频较高，因此单位时间内能够执行的指令也更多](https://www.elecfans.com/d/1575004.html)[1](https://www.elecfans.com/d/1575004.html)。
>
> 总结来说，软核处理器提供了更大的灵活性和可定制性，而硬核处理器则提供了更高的性能和效率。

### 动态部分重配置

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201216369.png" alt="image-20230923201216369" style="zoom:50%;" />

### 动态可重构处理器

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201322410.png" alt="image-20230923201322410" style="zoom:50%;" />

### 硬宏单元

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201630991.png" alt="image-20230923201630991" style="zoom:50%;" />

### 闪存

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201720163.png" alt="image-20230923201720163" style="zoom: 50%;" />

### 制程工艺

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201757568.png" alt="image-20230923201757568" style="zoom:50%;" />

### 乘积项

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201935430.png" alt="image-20230923201935430" style="zoom:50%;" />

### 可重构系统

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923201956434.png" alt="image-20230923201956434" style="zoom:50%;" />

### 可重构逻辑

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923202016531.png" alt="image-20230923202016531" style="zoom:50%;" />

### 粒度

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923202131206.png" alt="image-20230923202131206" style="zoom:50%;" />

### 逻辑综合

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923202322711.png" alt="image-20230923202322711" style="zoom:50%;" />

### 逻辑块

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923202356914.png" alt="image-20230923202356914" style="zoom:50%;" />

---

---

# 二. FPGA概要

## 2.1 FPGA构成要素

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923204634524.png" alt="image-20230923204634524" style="zoom:50%;" />

- **实现电路的逻辑要素**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923205038840.png" alt="image-20230923205038840" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923205214702.png" alt="image-20230923205214702" style="zoom:50%;" />

- **输入输出要素**

  <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923205147522.png" alt="image-20230923205147522" style="zoom:50%;" />

- **布线要素**

  <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923205328276.png" alt="image-20230923205328276" style="zoom:50%;" />

- **其他要素**

  <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923205909718.png" alt="image-20230923205909718" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923205925602.png" alt="image-20230923205925602" style="zoom:50%;" />

---

## 2.2 可编程技术

FPGA通过可编程的开关进行控制电路，而现代常用的FPGA可编程技术有 **闪存**、**反熔丝** 和 **静态存储器（SRAM）**

### 2.2.1 闪存

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923210425716.png" alt="image-20230923210425716" style="zoom:50%;" />

闪存是EEPROM的一种，属于非易失存储器D，采用的是**MOS晶体管技术**，但其特点是绝缘层中含有**浮置栅极( floating gate),即浮栅。**

>  这种栅极通常使用多晶硅来制造，是在一层不与外界连接的绝缘层( SiO2)中浮空的栅极。

> MOS, 即Metal-Oxide-Semiconductor, 是一种由金属-半导体氧化物-半导体三层构造
> 形成的半导体结构，使用半导体氧化物( SiO2)作为绝缘层。

> 衬底：
>
> [在浮栅场效应晶体管中，衬底是由半导体单晶材料制造而成的晶圆片](https://www.zhihu.com/question/336474160)[1](https://www.zhihu.com/question/336474160)[。在这种晶体管中，源极和漏极是在衬底上形成的N型扩散区](https://www.zhihu.com/question/336474160)[1](https://www.zhihu.com/question/336474160)[。当我们在栅极上施加电压时，**衬底中的电子会受到电场的作用，向衬底表面移动，形成一个N型薄层，直到在源极和漏极之间形成N型沟道，连通两个N型扩散区，此时MOS管导通**

闪存根据写人方式不同可以分为两种: NAND型和NOR型。它们各自的特点是，**NAND型在写入时需要高电压**，而**NOR型在写入时需要大电流**。我们以NAND型为例来讲解闪存的原理。

#### 1.闪存的原理

浮栅在**被写入之前，不带电荷**，晶体管表现为**耗尽型**，**栅极零偏压时电流也可流过**(图2-3a)

> ["栅极零偏压"是指在场效应晶体管（FET）中，栅极（Gate）和源极（Source）之间没有电压差](https://zhuanlan.zhihu.com/p/451953737)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923230507243.png" alt="image-20230923230507243" style="zoom:65%;" />

浮栅在**写入后带电**，晶体管表现为增强型，**栅极零偏压时电流不能流过**(图2-3b)。因此，根据在浮栅上存储的电荷，在电流流过时控制电压就可以产生“0”和“1”。 

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230923230557416.png" alt="image-20230923230557416" style="zoom:65%;" />

具体来说，当浮栅上存有电荷时，控制栅极上就算**加低电压**(1 V左右)也会有**电流流过**;当浮栅上没有电荷时，只有加**相对较高的电压**(5V左右)才会有**电流流过**。(***电流从源极流向漏极***)

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924113003086.png" alt="image-20230924113003086" style="zoom:67%;" />

浮栅中的电荷**没有逃脱路径**，因此可以**半永久地**保存数据，也就是说闪存属于**非易失存储器**。

那么，没有连接到任何地方的浮栅如何锁住电荷呢?写入时，在**漏极和控制栅极间加高电压**，电子可成为隧道电
流注人浮栅

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924113333370.png" alt="image-20230924113333370" style="zoom:50%;" />

**擦除**时,在**源极加高电压**即可将浮栅中的电子以隧道电流的形式引出

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924113412482.png" alt="image-20230924113412482" style="zoom:50%;" />

此外，通常闪存能够以位(比特)为单位进行写入，但擦除是以块为单位的。也就是说，**它具有不能覆盖写人的特征。**

#### 2.基于闪存的可编程开关

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924113702357.png" alt="image-20230924113702357" style="zoom:67%;" />

- [**左侧的小晶体管**：这个晶体管用于对闪存进行写入/擦除操作](https://blog.csdn.net/qq_45364953/article/details/126820278)[【1】](https://blog.csdn.net/qq_45364953/article/details/126820278)。也就是说，它负责将数据写入或从闪存中删除数据。
- [**右侧的大晶体管**：这个晶体管是FPGA中控制用户电路的开关](https://blog.csdn.net/qq_45364953/article/details/126820278)[【1】](https://blog.csdn.net/qq_45364953/article/details/126820278)。也就是说，它负责根据左侧晶体管写入/擦除的结果，来控制用户电路的状态。

[这两个晶体管有着共同的控制栅极和浮栅](https://blog.csdn.net/qq_45364953/article/details/126820278)[【1】](https://blog.csdn.net/qq_45364953/article/details/126820278)[。当我们通过编程用的开关（即左侧的小晶体管）注入电子时，就可以直接决定用户所使用开关（即右侧的大晶体管）的状态](https://blog.csdn.net/qq_45364953/article/details/126820278)[链接【1】](https://blog.csdn.net/qq_45364953/article/details/126820278)。

[这种结构不仅对用户开关的连接没有限制，而且因为独立于用户信号，所以对其编程也较为容易](https://blog.csdn.net/qq_45364953/article/details/126820278)[【1】](https://blog.csdn.net/qq_45364953/article/details/126820278)。也就是说，我们可以更自由地控制用户电路的状态，而不需要担心与用户信号发生冲突或干扰。同时，由于编程用的开关与用户开关是分离的，我们可以更容易地对其进行编程操作，而不需要直接操作用户电路。



[基于闪存的可编程开关在实际编程时，利用隧道电流按照以下过程进行](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)：

1. [**写入阶段**：首先在编程晶体管的源极和漏极加5.0 V电压，然后在控制栅极加-11.0 V电压后，电子就会流入浮栅，开关变为开启状态](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)[。这个过程是通过隧道效应实现的，电子可以按照一定概率通过势垒的现象](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)。（*这里，是让源极接地，漏极加5V，控制栅极加-11V*）
2. [**正常工作阶段**：控制栅极保持2.5 V电压，这样浮栅的电位大致会维持在4.5V左右](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)[。这个状态下，开关保持开启状态，可以进行正常的读写操作](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)。
3. [**擦除阶段**：当需要关闭开关时，让编程晶体管的源极和漏极接地(GND)，在控制栅极加16.0 V电压后，浮栅内电位就能降到0V以下](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)[。这个过程也是通过隧道效应实现的，电子被从浮栅中抽出，从而关闭了开关](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)。

[这种基于闪存的可编程开关具有非易失性，即断电后数据不丢失的特性](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)[。因此，在断电重启后，开关状态（即存储的数据）可以保持不变](https://bing.com/search?q=基于闪存的可编程开关编程过程)[1](https://bing.com/search?q=基于闪存的可编程开关编程过程)[。这对于需要保持状态信息的应用（如FPGA）来说非常有用](https://bing.com/search?q=基于闪存的可编程开关编程过程)[【1】](https://bing.com/search?q=基于闪存的可编程开关编程过程)。

> 当左侧的编程晶体管使得共用栅极获得电子时，右侧的电路会处于连接状态（即开关闭合，导线连通）。
>
> 不同的闪存设备存在不同的实现原理

#### 3. 优缺点

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924161458130.png" alt="image-20230924161458130" style="zoom:50%;" />

### 2.2.2 反熔丝

反熔丝开关的初始状态为开放(断开)状态，反熔丝在通电熔断(严格来讲是熔合)后才导通。它和熔丝的特性相反，因此被称为反熔丝。

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924164342694.png" alt="image-20230924164342694" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924164404958.png" alt="image-20230924164404958" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924164426402.png" alt="image-20230924164426402" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924164729823.png" alt="image-20230924164729823" style="zoom:50%;" />

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924164657203.png" alt="image-20230924164657203" style="zoom:50%;" />

优缺点<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924164750244.png" alt="image-20230924164750244" style="zoom:50%;" /><img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924164811191.png" alt="image-20230924164811191" style="zoom:50%;" />

### 2.2.3 静态存储器（重点）

![image-20230924214157672](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230924214157672.png)

- **Data**：这是存储在存储单元中的实际数据。在写入操作中，我们将数据写入到这个位置
- **Data（头上有一条横线）**：这是Data的反相值，也就是说，如果Data是1，那么Data（头上有一条横线）就是0，反之亦然。这个反相值主要用于错误检测和纠正

- **VDD**：这是一个术语，通常用于MOSFET（金属氧化物半导体场效应晶体管）和CMOS（互补金属氧化物半导体）设备，表示电源的正极。"D"在这里代表"Drain"（漏极），这是MOSFET的一个主要部分。在现代电子设备中，VDD通常是3.3V，但也可能更低，如1.8V或1.2V。
- **VSS**：这是另一个术语，通常用于表示电源的负极。"S"在这里代表"Source"（源极），这也是MOSFET的一个主要部分。在大多数数字电子设备中，VSS通常被认为是零伏。

- **Write信号**：Write信号是控制线之一，用于指示存储器执行写入操作。当Write信号被激活时，数据会被写入到存储器中。具体来说，Write信号会驱动字线，并通过字线将数据写入到存储单元中。
- **传输晶体管（PT）**：传输晶体管在静态存储器中的作用是充当开关，控制数据在电路节点之间的传递。在写入操作中，PT会根据Write信号的状态来决定是否打开或关闭数据通道。此外，数据的读取也通过PT进行。

> **传输晶体管（Pass Transistor，PT）**通常是由**MOSFET（金属氧化物半导体场效应晶体管）制成的**。在MOSFET中，控制栅极（Gate）位于源极（Source）和漏极（Drain）之间。当我们在**控制栅极**上**施加电压**时，可以控制源极和漏极之间的电流流动。在静态存储器中，**控制栅极用于控制PT的开关状态，从而控制数据在电路节点之间的传递。**

**控制栅极和写入write的关系**

控制栅极和write信号是有关联的。write信号是用来控制传输晶体管（PT）的开关状态，从而控制数据在电路节点之间的传递。write信号的写入过程如下：

- 当write信号被激活时，它会驱动字线，并通过字线将数据写入到存储单元中。
- 存储单元由两个CMOS反相器构成的触发器和两个PT组成。触发器可以保持其状态（即数据值），直到新的数据被写入。
- PT是由MOSFET制成的，它的控制栅极与write信号相连，它的源极和漏极分别与数据线和触发器相连。
- 当write信号为高电平时，PT打开，数据线上的数据可以通过PT写入到触发器中，从而改变触发器的状态。
- 当write信号为低电平时，PT关闭，数据线上的数据无法通过PT写入到触发器中，触发器保持原来的状态。
