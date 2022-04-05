# java三大版本

## java SE

javaSE 是java标准版的简称，其定位是个人计算机应用（应用原生界面比较ugly） 全称：Java Platform Standard Edition 主要用于开发和部署桌面、服务器以及嵌入设备和实时环境中的Java应用程序。例如，Java应用程序开发平台Eclipse。

##  java EE

javaEE 是java企业版的简称，其定位是服务器端应用　（目前应用最广泛的版本）全称：Java Platform Enterprise Edition 是在JavaSE的基础上构建的他提供Web 服务、组建模型、管理和通信API.可以用来实现企业级的面向服务体系结构(service-oriented 

architecture,SOA)和web2.0应用程序。

## javaME 

javaME 是java微型版的简称，主要定位是移动产品和车载产品等（基本没有使用，大部分移动产品使用Android）全称：Java Platform Micro Edition Java ME为在移动设备和嵌入式设备（比如手机、PDA、电视机顶盒和打印机）上运行的应用程序提供一个健壮且灵活的环境。Java ME包括灵活的用户界面、健壮的安全模式、许多内置的网络协议以及对于动态下载的连网和离线应用程序的丰富支持。基于Java ME规范的应用程序只需要编写一次，就可以用于许多设备，而且可以利用每个设备的本级功能。

## 　　1.4 包含关系

　　　　　　[![img](https://img2018.cnblogs.com/blog/1676271/201904/1676271-20190430121330408-847419857.png)](https://img2018.cnblogs.com/blog/1676271/201904/1676271-20190430121330408-847419857.png)

 

#  JVM JRE 与 JDK 的关系

## JVM 

JVM 全称 Java Virtual Machine 是java虚拟机，它是整个java实现跨平台的最核心的部分，所有的java程序会首先被编译为.class的类文件，这种类文件可以在虚拟机上执行。

也就是说class并不直接与机器的操作系统相对应，而是经过虚拟机间接与操作系统交互，由虚拟机将程序解释给本地系统执行。

JVM屏蔽了与具体操作系统平台相关的信息，使得Java程序只需生成在Java虚拟机上运行的目标代码（字节码），就可以在多种平台上不加修改地运行。

##  JRE 

JRE 全称 Java Runtime Environment 是java运行时环境，这里面包含了运行java程序所需要的所有类库，一台机器上只有安装了jre才可以运行java程序

JRE 是包含 JVM的，并且还包含了一些运行java程序所需要的类库和资源文件等。 

## JDK

JDK 全称 Java Development Kit 是java开发工具包，是Sun Microsystems针对Java开发员的产品。JDK 中包含了很多关于java程序开发的工具，例如编译工具javac，文档生成工具javadoc等等等等。同理，JDK是包含JRE 和 JVM 的，并且在此基础上还包括了一些开发工具，调试工具，以及用于管理程序的管理工具等。 

## 　　2.4 关系图 

　[![img](https://img2018.cnblogs.com/blog/1676271/201904/1676271-20190430122937654-774914274.png)](https://img2018.cnblogs.com/blog/1676271/201904/1676271-20190430122937654-774914274.png)

# 其他一些补充知识

## 三大版本更名是在jdk5.0中　　　

　　　　　　①SE(J2SE)，standard edition，标准版，是我们通常用的一个版本，从JDK 5.0开始，改名为Java SE。

　　　　　　②EE(J2EE)，enterprise edition，企业版，使用这种JDK开发J2EE应用程序，从JDK 5.0开始，改名为Java EE。

　　　　　　③ME(J2ME)，micro edition，主要用于移动设备、嵌入式设备上的java应用程序，从JDK 5.0开始，改名为Java ME。

##  java实现跨平台的原理

　　　　　　这里要从java的编译方式说起，java源代码编译之后并不是直接生成一个可执行文件（.exe），而是生成对应的java字节码文件（.class），这个字节码电脑的并不能运行，而是需要java虚拟机来再次进行解释，才能被cpu执行，也就是说，java程序并不是直接运行在cpu上的，而是运行在java虚拟机JVM上面的。

　　　　　　对于不同的从操作系统，有不同的java虚拟机。虽然是不同的虚拟机，但是他们可以识别相同的字节码文件。这样，就达到了一次编译，到处运行的目的，也就是java跨平台的原理。

　　　　[![img](https://img2018.cnblogs.com/blog/1676271/201904/1676271-20190430124557582-747117888.png)](https://img2018.cnblogs.com/blog/1676271/201904/1676271-20190430124557582-747117888.png)

 