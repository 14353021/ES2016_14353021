#Lab3--DOL实例分析

----------

##1.改完的*.dot截图
（1）修改 example2，让 3个square模块变成 2个

得到的模块图：

![](http://a2.qpic.cn/psb?/V11uwP4a2cS7Cz/y4pqKBFDpi5VIPNg4LPI2Ly*yz28n8NarcsPvvPWoTw!/b/dAkBAAAAAAAA&bo=*QFlAAAAAAADB7s!&rf=viewer_4)

运行结果图：

![](http://a2.qpic.cn/psb?/V11uwP4a2cS7Cz/ojY4TtWmUpEPPgRIC3jw412r3uhDOE18C.CY7GbmnSg!/b/dAkBAAAAAAAA&bo=LgKjAQAAAAADAKs!&rf=viewer_4)

（2）修改 example1，使其输出3次方数

得到的模块图：

![](http://a3.qpic.cn/psb?/V11uwP4a2cS7Cz/Twkgf8aZUjPw5pc3SN5EupLHJ3NUFy82P.2FZmIkxSE!/b/dAoBAAAAAAAA&bo=BAJ7AAAAAAADAFg!&rf=viewer_4)

运行结果图：

![](http://a1.qpic.cn/psb?/V11uwP4a2cS7Cz/RqEBBIntaAJ4*9hmFOSm8GiwW39EKOid4Gr0j3faeMs!/b/dAsBAAAAAAAA&bo=LgKnAQAAAAADAK8!&rf=viewer_4)

##2.代码实现
（1）修改 example2，让 3个square模块变成 2个

step1: 理解example2代码

　　查看example2.xml文件，可发现它在声明square模块时，首先定义了一个名为N值为3的variable，然后使用iterator语句，通过迭代生成3个square模块。

![](http://a3.qpic.cn/psb?/V11uwP4a2cS7Cz/VhK5TdyukYrv2BuFSkz*K4SZjrXhfB.TDGXFaYG.XZ4!/b/dI8AAAAAAAAA&bo=jwEVAQAAAAADAL8!&rf=viewer_4)

step2: 修改example2代码

　　根据实验题目的要求，我们需要把原来的3个square模块改为2个，因此我们只需要在example2.xml文件定义名为N值的variable时，把它的值由3改为2，就能生成2个sqaure模块了。修改位置如下图所示：

![](http://a1.qpic.cn/psb?/V11uwP4a2cS7Cz/nzlDIEB*6P5F2JD8kTOtTnyvrmZ6f6eF6j5.C44SnYo!/b/dAsBAAAAAAAA&bo=HAEfAAAAAAADByA!&rf=viewer_4)

（2）修改 example1，使其输出3次方数

step1: 理解example1代码

　　查看example1文件夹中的square.c文件，可发现它在定义square模块的行为时，首先使用DOL-read 函数读入模块的输入值i，然后对i进行i=i*i的平方操作，随后再通过DOL-write函数输出，通过这种方法实现了平方进程。

![](http://a2.qpic.cn/psb?/V11uwP4a2cS7Cz/9Ksz6AK6CPNczovwKl8eNmPBnyIgcadL46gixm1.BGU!/b/dG8BAAAAAAAA&bo=DQIoAQAAAAADAAM!&rf=viewer_4)

step2: 修改example1代码

　　根据实验题目的要求，我们需要让square模块输出三次方数，因此我们只需要在square.c文件修改定义平方进程的函数，即square_fire函数，把其中的平方操作i=i×i修改为三次方操作i=i×i×i，就能实现三次方操作了。修改位置如下图所示：

![](http://a1.qpic.cn/psb?/V11uwP4a2cS7Cz/AHrzV.G7dnY.Xvdtd2bgpEVnI5MEYpt5VwgDgufaqXQ!/b/dHcBAAAAAAAA&bo=5QFtAAAAAAADAKw!&rf=viewer_4)

##3.实验感想

　　通过这次实验，我学会了DOL实例生成的原理和方法，理解了各个文件的用途和代表的意义，也学会了如何修改实例的代码来完成自己想要的效果，基本理解了DOL工作的原理，真是收获良多。在我个人看来，DOL是我们平时实现算法或进程的一种形象化的工具，我们可以通过它来查看我们算法的输出结果，还可以方便地查看到模块化的dol图，是我们实践算法的良好工具。在今后的实验，我一定更加努力，并争取使用DOL完成更多有用的算法。