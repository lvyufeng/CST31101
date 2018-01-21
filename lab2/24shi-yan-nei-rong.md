## 实验内容

阅读实验原理实现以下模块：

1. _**PC**_，要求输出指令存储器_**Inst\_Rom**_读使能信号ce，地址addr\(长度自定，与ROM地址匹配\)。若选择按字节使能\(Byte Write Enable\)，PC+4得到地址；否则使用PC+1。
2. _**Controller**_，其中包含两部分，分别为_**main\_decoder**_，_**alu\_decoder**_。参考MIPSfpga中控制器的实现代码，使用组合逻辑产生下列信号：
   1. | memtoreg | memwrite | pcsrc | alusrc | regdst | regwrite | jump | alucontrol |
      | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
      | \[0:0\] | \[0:0\] | \[0:0\] | \[0:0\] | \[0:0\] | \[0:0\] | \[0:0\] | \[2:0\] |
      | led\[0\] | led\[1\] | led\[2\] | led\[3\] | led\[4\] | led\[5\] | led\[6\] | led\[7:9\] |
3. 使用Block Memory Generator IP核，构造指令存储器，注意考虑PC地址位数统一。\(参考实验一\)
4. 将指令存储器读取的指令显示到7段数码管中。控制器信号输出至led0-led9\(参考实验一\)
5. 导入仿真程序，验证取指、译码阶段正确执行。
6. 加入时钟分频器，将板载100Mhz频率降低为1hz，连接PC、Inst\_Rom时钟。\(参考数字逻辑实验\)
7. 建立top顶层，根据实验原理图，将上述5个模块正确连接，上板执行。


