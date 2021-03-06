## 指令周期
指令周期是取出一条指令并执行这条指令的时间。一般由若干个机器周期组成，是从取指令、分析指令到执行完所需的全部时间。
指令周期类型有非访内指令的指令周期、取数指令的指令周期、存数指令的指令周期、空操作指令和转移指令的指令周期。
中文名 指令周期 外文名 Instruction Cycle 概    述 完整执行一条指令所需要的时间
目录
### 1 基本概念
### 2 类别
▪ 非访内指令
▪ 取数指令
▪ 存数指令
▪ 空操作指令
### 3 特点
基本概念编辑
指令周期，读取－执行周期（fetch-and-execute cycle）是指CPU要执行指令经过的步骤。 [1] 
计算机之所以能自动地工作，是因为CPU能从存放程序的内存里取出一条指令并执行这条指令；紧接着又是取指令，执行指令，如此周而复始，构成了一个封闭的循环。除非遇到停机指令，否则这个循环将一直继续下去。
指令周期 :CPU从内存取出一条指令并执行这条指令的时间总和。
CPU周期 :又称机器周期，CPU访问一次内存所花的时间较长，因此用从内存读取一条指令字的最短时间来定义。
时钟周期: 通常称为节拍脉冲或T周期。一个CPU周期包含若干个时钟周期。 

#### 非访内指令
CLA是一条非访内指令，它需要两个CPU 周期，其中取指令阶段需要一个CPU周期，执行指令阶段需要一个CPU周期。
1、取指令阶段
(1)程序计数器PC的内容20(八进制)被装入地址寄存器AR；
(2)程序计数器内容加1，变成21，为取下一条指令做好准备；
(3)地址寄存器的内容被放到地址总线上；
(4)所选存储器单元20的内容经过数据总线，传送到数据缓冲寄存器DR；
(5)缓冲寄存器的内容传送到指令寄存器IR；
(6)指令寄存器中的操作码被译码或测试；
(7)CPU识别出是指令CLA，至此，取指令阶段即告结束。
2、执行指令阶段
(1)操作控制器送一控制信号给算术逻辑运算单元ALU；
(2)ALU响应该控制信号，将累加寄存器AC的内容全部清零，从而执行了CLA指令。 [2] 
取数指令
1.送操作数地址
第二个CPU周期主要完成送操作数地址。在此阶段，CPU的动作只有一个，那就是把指令寄存器中的地址码部分(30)装入地址寄存器，其中30为内存中存放操作数的地址。
2.两操作数相加
第三个CPU周期主要完成取操作数并执行加法操作中。在此阶段，CPU完成如下动作：
(1)把地址寄存器中的操作数的地址发送到地址总线上。
(2)由存储器单元30中读出操作数，并经过数据总线传送到缓冲寄存器。
(3)执行加操作：由数据缓冲寄存器来的操作数可送往ALU 的一个输入端，已等候在累加器内的另 一个操作数(因为CLA指令执行结束后累加器内容为零)送往ALU的另一输入端，于是ALU将两数相加，产生运算结果为0+6=6。这个结果放回累加器，替换了累加器中原先的数0 。 [2] 
存数指令
STA指令的指令周期由三个CPU周期组成。
1.送操作数地址
在执行阶段的第一个CPU周期中，CPU完成的动作是把指令寄存器中地址码部分的形式地址40装到地址寄存器。其中数字40是操作数地址。
2.存储和数
执行阶段的第二个CPU周期中，累加寄存器的内容传送到缓冲寄存器，然后再存入到所选定的存储单元(40)中。CPU完成如下动作：
(1)累加器的内容被传送到数据缓冲寄存器DR；
(2)把地址寄存器的内容发送到地址总线上，即为将要存入的数据6的内存单元号；
(3)把缓冲寄存器的内容发送到数据总线上；
(4)数据总线上的数写入到所选中的存储器单元中，即将数6写入到存储器40号单元中。注意 在这个操作之后，累加器中仍然保留和数6，而存储器40号单元中原先的内容被冲掉 。 [2] 
空操作指令
第四条指令即“NOP”指令，这是一条空操作指令。其中第一个CPU周期中取指令，CPU把23号单元的“NOP”指令取出放到指令寄存器，第二个CPU周期中执行该指令。因译码器译出是“NOP”指令，第二个CPU周期中操作控制器不发出任何控制信号。NOP指令可用来调机之用。
1.第一个CPU周期（取指令阶段）
CPU把24号单元的“JMP 21”指令取出放至指令寄存器，同时程序计数器内容加1，变为25，从而取下一条指令做好准备。
2.第二个CPU周期（执行阶段）
CPU把指令寄存器中地址码部分21送到程序计数器，从而用新内容21代替PC原先的内容25。这样，下一条指令将不从25单元读出，而是从内存21单元开始读出并执行，从而改变了程序原先的执行顺序。
注意 执行“JMP 21”指令时，我们此处所给的四条指令组成的程序进入了死循环，除非人为停机，否则这个程序将无休止地运行下去，因而内存单元40中的和数将一直不断地发生变化。当然，我们此处所举的转移地址21是随意的，仅仅用来说明转移指令能够改变程序的执行顺序而已。 

# 答案选 C 程序计数器 (PC)
