## 附录C 七段数码管的使用

![](/assets/apendix_c.png)

Minisys实验板上有两个4位带小数点的七段数码管，上图显示了它们与主芯片的连接方式。其中_**A7~A0**_是数码管8个位的使能信号，而_**CA~CG/DP**_则对应各个位上七个段以及小数点的触发信号。**需要注意的是，使能信号和触发信号都是低电平触发的**。

---

![](/assets/apendix_c-2.png)

上图以数码管中最右侧的A0数码管为例说明了Minisys板卡上的7段数码管的连接方式。8个位中的各个相应的段及小数点分别连接到一组低电平触发的引脚上，他们被称为**CA、CB、CC、…、CG、DP**，其中，CA接到这8个数码管中每一个数码管A段的负极,CB接到这8个数码管中每一个数码管B段的负极，以此类推。

此外，每一个数码管都有一个使能信号**A\[7:0\]**。**A\[7:0\]**通过一个反相器接到对应数码管的每一个段的正极上。比如说，只有到A\[0\]为0的时候，最右侧数码管的显示才会受到**CA…CG**这几个信号的驱动。

---

下图列出了数码管显示0到F时点亮的段。例如，在显示数字0的时候，除了中间的G段外其他的段都被点亮了。而数字1只点亮了B段和C段。

![](/assets/apendix_c-3.png)

要想让每个数码管显示不同的数字，使能信号（**A\[7:0\]**）和段信号（**CA…CG**）必须依次地被持续驱动，数码管之间的刷新速度应该足够快，这样就看不出来数码管之间在闪烁。举个例子，如果想在数码管0上显示数字3而数码管1上显示数字9，可以先把**CA…CG**设置为显示数字3，并拉低**A\[1\]**信号，然后再把**CA…CG**设置为显示数字9并拉高**A\[1\]**拉低**A\[2\]**。刷新频率可以设置为**2ms**刷新一次，这样人眼就看不出闪烁了。

