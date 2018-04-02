---
layout: post
title: 对I/Q信号的理解
categories: [信号]
description: 对I/Q信号的理解
keywords: 信号
---

<h2 align = "center">对I/Q信号的理解</h2>

最近阅读认知无线电相关的论文，总是遇到I/Q信号的概念，隐约记得高频信号里有讲过这东西，但是认识已经很模糊了，于是这里总结一下。

简单来说，I/Q数据可以表示一个正弦波信号的幅度和相位的变化情况。如果信号的幅度和相位按照一定可控的规律发生变化，这样我们就可以用这种变化在正弦波中编码一些信号，这个过程称为“调制”。

调制使得一个高频的载波信号以一定的比例，随着低频信息或信号变化。I/Q数据在无线电通信系统非常常见，在信号调制中更是普遍，因为这是一种非常方便的对信号进行调制的方式。

### 1.信号相关的背景知识

信号调制通过改变正弦波的特性来编码信息。正弦波的数学表示如下：

<img src="http://www.ni.com/cms/images/devzone/tut/dhall_2_equation.JPG" style="border:none;width: 300.0px;margin: center;"/>

对于上面的表达式，我们很难对幅度、频率和相位进行改变来编码信息。频率是正弦波的相位变化的速率（也就是一阶导数），频率和相位都可以认为是和正弦波的相位角有关。因此，我们可以用复平面的一个向量来表示正弦波的的瞬时状态，向量使用的是极坐标系下的幅度和相位作为轴。

<img src="http://www.ni.com/cms/images/devzone/tut/sine_polarrep.gif" style="border:none;width: 300.0px;margin: center;"/>

在上图中，原点到图中黑点的距离，代表的是正弦波的幅度，水平轴和直线之间的夹角，代表相位的大小。因此，原点到黑点的距离会保持不变，如果正弦波不发生变化。该点的相位随着正弦波的当前状态发生变化，因此，一个频率为1Hz（2π/s）的正弦波，其在该极坐标下，将围绕着圆心进行逆时针旋转（公转）。如果在公转的过程中，幅度不发生变化，那么该点将以1秒1圈的速度，保持半径大小等于幅度的状态，作圆周运动。

因为相位只是一个相对的单位，假设作为参照的正弦波，其频率和该正弦波相等。如果参照的正弦波频率，如果参考正弦波频率和标绘的正弦波频率相同，则两个信号相位的变化率相同，并且围绕原点的正弦波的旋转变得平稳。在这种情况下，单个的幅值/相位点可以表示为参考频率的正弦波。在原点周围的任何相位旋转都表示参考正弦波与正弦波之间的频率差。

上面是对极坐标系下的幅度和相位的介绍，所有的概念应用到I/Q数据，实际上，I/Q数据只是极坐标系下的幅度和相位的变换到笛卡尔坐标下的情况。具体如下图所示：

<img src="http://www.ni.com/cms/images/devzone/tut/iq_polarrep.gif" style="border:none;width: 300.0px;margin: center;"/>


### 2.通信系统中的I/Q数据

RF通信系统使用先进的调制形式来增加在给定量的频谱中可以传输的数据量。调制可以分为模拟调制和数字调制两种。如果模拟信号被调制到正弦波中，则称之为模拟调制。如果通过模数转换器（ADC）对模拟音频数据进行采样，并将所得到的数字比特调制为载波正弦波，则该技术被定义为数字调制，因为数字数据被编码。模拟调制和数字调制都通过改变信号的幅度、频率和相位来实现。

幅度调制(AM)，频率调制(FM),相位调制(PM)是模拟调制的所有类型。

<img src="http://www.ni.com/cms/images/devzone/tut/dhall_analog_modulation.JPG" style="border:none;width: 500.0px;margin: center;"/>

上图中是不同的模拟调制的类型：AM,FM和PM。对于AM，其中传递的信息实际上是蓝色的包络线。对于FM，传递的信息是蓝色的矩形包络。对于PM，传递的信息也是蓝色的包络。

如前面提到的一样，如果只有正弦载波的幅度随着时间变化，那么，对于AM来说，信号在极坐标系下的I/Q图只会改变到图中原点的距离。

<img src="http://www.ni.com/cms/images/devzone/tut/a/d1c38d1a1109.gif" style="border:none;width: 400.0px;margin: center;"/>

上图显示I / Q数据点的幅度固定相位在45度的情况。你不能知道太多的消息信号，因为它只是幅度调制。但是，如果想观察I / Q数据点在时间上的大小如何变化，则可以变换一种表示形式。

<img src="http://www.ni.com/cms/images/devzone/tut/a/d1c38d1a1110.gif" style="border:none;width: 400.0px;margin: center;"/>

上图是3维度情况下的信号表示，信号的幅度变化，类似于正弦波，这表明其传递的信息是正弦波。图中红色的波形，代表的是信号在I/Q轴(平面)上的投影，表示的就是I/Q信号的波形。

PM的信号如下，幅度不变，但是相位随着时间在变化。相位在45°和-45°之间不断变化。

<img src="http://www.ni.com/cms/images/devzone/tut/a/d1c38d1a1111.gif" style="border:none;width: 400.0px;margin: center;"/>

同样地，我们在三维坐标下来看波形随着时间的变化情况：

<img src="http://www.ni.com/cms/images/devzone/tut/a/d1c38d1a1112.gif" style="border:none;width: 400.0px;margin: center;"/>

本质上，I / Q数据表示的是消息信号。由于I / Q数据波形是极坐标下幅​​度和相位波形的笛卡尔变换，因此我们可能无法直观确定消息信号的性质。

### 3.为什么要使用I/Q信号呢？

表面上来看，使用幅度和相位的表示法，对于我们来说更直观，而I/Q看起来是更抽象的概念。但是，实际的硬件设计，证明I/Q信号表示是更好的。

根据输入消息信号精确地改变硬件电路中的高频载波正弦波的相位是困难的。因此，操纵载波正弦波的幅度和相位的硬件信号调制器将是昂贵的并且难以设计和构建，并且事实证明，不如使用I和Q波形的电路那样灵活。要了解如何避免直接操纵射频载波的相位，有如下的I / Q调制方程式:

<img src="http://www.ni.com/cms/images/devzone/tut/trig_equations.jpg" style="border:none;width: 500.0px;margin: center;"/>

同频率的正弦波和余弦波之间的差异是它们之间的90度相位偏移,同频率的正弦波和余弦波之间的差异是它们之间的90度相位偏移。用这种方法，就不需要直接改变射频载波正弦波的相位。当然，等式的后半部分是正弦波，前半部分是余弦波，所以必须在硬件电路中包含一个器件，以便在用于I和Q的载波信号之间产生90度相移，但是与上述的直接相位处理相比，这种添加是一个更简单的设计问题。

<img src="http://www.ni.com/cms/images/devzone/tut/dhall_2_modulator.JPG" style="border:none;width: 500.0px;margin: center;"/>

上图显示了调制的过程和电路设计。带有“X”的圆圈表示混频器 ---- 执行倍频和上变频或下变频信号的器件（此处为上变频）。I / Q调制器将I波形与RF载波正弦波混合，并将Q信号与相同的RF载波正弦波以90度相位偏移，从I信号中减去Q信号，产生最终的RF调制波形。实际上，载波的90度移位是I和Q数据名称的来源，I是指同相数据（因为载波是同相的），Q是正交数据（因为载波是偏移90度）。这种技术被称为正交上变频，我们可以在任何调制方案中使用相同的I / Q调制器。I / Q调制器只是对I和Q波形幅度的变化作出反应，I和Q数据可以表示消息信号的大小和相位的任何变化。 I / Q调制器设计的灵活性和简单性（相对于其他选择）是为什么它被广泛使用和普及的原因。

**参考资料**

* <a href = "http://www.ni.com/tutorial/4805/en/">What is I/Q Data?</a>