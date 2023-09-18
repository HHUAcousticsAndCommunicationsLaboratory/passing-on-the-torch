## 1.2 同步电路设计

### 1.2.1触发器

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

### 1.2.3 时序分析