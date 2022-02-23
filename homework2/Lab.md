<center>
<font face="楷体" size=6px>  武汉大学计算机学院</font>

<font face="楷体" size=6px>  实验报告</font> 
</center>

<font tace="黑体" size=4px>课程名称: 计算机网络 </font>

<font tace="黑体" size=4px>专业年级: 2020级软件工程 </font>

<font tace="黑体" size=4px>姓名: 朱小东 </font>

<font tace="黑体" size=4px>学号: 2020302111030 </font>

#### 实验目的：

了解软件Wireshark，学习并使用Wireshark来分析数据包。

#### 实验内容1

在step7中的协议栏下我们可以找到TCP、HTTP、ARP等协议。

#### 实验内容2

![](http.png)

从图片中我们可以看出HTTP GET message在20:39:33.030783发送，HTTP OK reply在20:39:33.084622收到，耗时53.839ms

#### 实验内容3

从上幅图片中我们可以看到HTTP GET message从10.128.51.227发送到202.114.64.41；HTTP OK reply从202.114.64.41发送到10.128.51.227。

所以cs.whu.edu.cn的网络地址为202.114.64.41，本地网络地址为10.128.51.227

#### 实验内容4

HTTP GET message和HTTP OK reply的打印内容见wireshark_WLAN1EJWH1.pdf

#### 小结
在这次实验中，了解、学习并练习了wireshark的使用。对数据包的传输有了更深刻的理解。