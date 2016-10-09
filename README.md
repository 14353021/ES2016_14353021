#DOL框架描述

----------
　　DOL是一个软件开发框架程序并行应用程序。它可以详细说明一个应用程序，基于卡恩过程网络模型计算，还可以基于SystemC特性去模拟引擎。此外,DOL提供了一个基于xml的规范格式去描述多处理器系统并行应用程序的实现,包括绑定和映射。其运作图如下图所示：
![？？？](http://b177.photo.store.qq.com/psb?/V11uwP4a2cS7Cz/rDnwIAS7b1qJeNtgscnFSJFmLcTavEdBwOckGL5TyuI!/b/dLEAAAAAAAAA&bo=8QMqAvEDKgIDCSw!&rf=viewer_4)
　　实验一我进行了DOL的安装以及配置。其中首先要安装一些必要的配置工具，如make、ant、java等，然后安装openjdk-7-jdk并编译，设置相关环境变量，然后安装systemc-2.3.1.tgz并编译。安装好这些必要的组成部分后，就可以进行DOL的安装、配置以及编译了。编译成功后，测试第一个例子runexample.xml -Dnumber=1，运行结果无误则代表DOL配置成功啦~

<br />

#DOL 安装笔记

----------
###1.首先，安装一些必要的环境


`$	sudo apt-get update`

`$	sudo apt-get install ant`

`$ 	sudo apt-get install openjdk-7-jdk`

`$	sudo apt-get install unzip`

![](http://a1.qpic.cn/psb?/V11uwP4a2cS7Cz/YB9wsjYOnO*Y0kLOYrMjK1NCOOWJeyHgpOivOeqso6A!/b/dOEAAAAAAAAA&bo=swLNAQAAAAADB18!&rf=viewer_4)

###2.把安装DOL所必须的软件文件拉到虚拟机里

![](http://a1.qpic.cn/psb?/V11uwP4a2cS7Cz/3d0aZR0vGYSr144tLc*Pd2NWG1p6SvMWHAqMCX.iE0U!/b/dLEAAAAAAAAA&bo=LAGhACwBoQADCSw!&rf=viewer_4)

###3.进行jdk-8u40-linux-x64的安装的配置

#####a. 将安装包解压到 /usr/lib/java，进入安装包下载所在路径,，重命名为jdk8

#####b. 配置环境变量

    `gedit ~/.bashrc`

   在打开的文件的末尾添加：

    `export JAVA_HOME=/usr/lib/java/jdk8`
     `export JRE_HOME=${JAVA_HOME}/jre`
     `export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib`
     `export PATH=${JAVA_HOME}/bin:$PATH`

   然后保存退出，然后输入下面的命令来使之生效

    `source ~/.bashrc`

![](http://a2.qpic.cn/psb?/V11uwP4a2cS7Cz/qWDIy9zczRgiKowhF3SfGBmIEq7YXupJxKEnSiOpQuE!/b/dLIAAAAAAAAA&bo=8gFYAPIBWAADACU!&rf=viewer_4)

#####c. 配置默认JDK

    `sudo update-alternatives --install /usr/bin/java java /usr/lib/java/jdk8/bin/java 300`
    `sudo update-alternatives --install /usr/bin/javac javac /usr/lib/java/jdk8/bin/javac 300`
    `sudo update-alternatives --config java`

![](http://a1.qpic.cn/psb?/V11uwP4a2cS7Cz/EGwVnjl3LoniqC1SqE2kmB1XETrzIASfb1hOz9w*vLQ!/b/dP8AAAAAAAAA&bo=3gJYAd4CWAEDACU!&rf=viewer_4)

#####d. 通过一下命令验证配置是否成功

    `java -version`  
    `java`  
    `javac`

###4.安装和编译SystemC

#####a. 解压文件，然后创建objdir文件夹，进行环境验证

    `../configure	--disable-async-updates	`

![](http://a1.qpic.cn/psb?/V11uwP4a2cS7Cz/GOh3M8UUd9C*bOhWAorja2rPLlZjdFFYsZg*zET2M*Q!/b/dPYAAAAAAAAA&bo=eALbAXgC2wEDACU!&rf=viewer_4)

#####b. 编译

    `sudo make install`

   编译完后文件目录如下，则代表已编译成功

![](http://a3.qpic.cn/psb?/V11uwP4a2cS7Cz/NbTBO.t4KmsnfBsbF3X6PSxGGWrfdqDeYUROILvlUd8!/b/dLAAAAAAAAAA&bo=dQJHAHUCRwADACU!&rf=viewer_4)

###5.安装和编译dol

#####a. 解压文件到dol文件夹中，进入dol的文件夹，修改build_zip.xml文件，修改编译的systemc位置为自己systemc的路径

![](http://a3.qpic.cn/psb?/V11uwP4a2cS7Cz/CN*89kHtotCd5EDQX8Vrii08cBbrzLz30jblyjc0tQ4!/b/dPgAAAAAAAAA&bo=0wJHANMCRwADACU!&rf=viewer_4)

#####b. 编译

    `ant -f build_zip.xml all`   

   若编译成功，则会显示build successful，如下图所示：

![](http://a3.qpic.cn/psb?/V11uwP4a2cS7Cz/JTyqSq3YEjj3eStnseZa.PbHg.tg6uBcibGG5rxBeYk!/b/dOMAAAAAAAAA&bo=6QA2AOkANgADACU!&rf=viewer_4)

#####c. 测试是否安装成功

   首先进入main文件夹

    `cd build/bin/main`

   然后运行第一个例子

    `ant -f runexample.xml -Dnumber=1`

   成功如下图所示：

![](http://a2.qpic.cn/psb?/V11uwP4a2cS7Cz/BlemiprjKi.mOY6HyY7KXBIOsZeo7a8qCPYXbQSJIDo!/b/dNwAAAAAAAAA&bo=rgHQAa4B0AEDACU!&rf=viewer_4)

于是，我们的DOL就安装配置好啦！

<br />

#实验感想、实验心得

----------
　　经过这次实验，我对DOL的结构有了一定的了解。在整个DOL的安装配置过程中，又学习到了很多新的软件的安装和使用方法，收获巨大。DOL让我感觉是一个十分强大的“评测系统”，相信在今后的实验中，我们将会接触到DOL越来越强大好用的功能，我将继续努力，争取精益求精。

 
