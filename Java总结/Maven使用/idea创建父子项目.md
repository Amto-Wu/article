idea创建父子项目

## 为什么需要父子项目

### 解耦

按照以往的创建项目方式，一个maven项目就是一个大工程，一开始还能进行简单的测试编译，但是随着项目的不断变大和复杂化，后期再做改动则可能牵一发而动全身。但是使用父子工程，每个模块都是独立的，他们通过父控制器聚合在一起，这样当你要改动一个模块的时候你改动的也只是这一个模块而已，并不会影响其他的模块。

### 提高 jar 包复用

父项目的依赖子项目可以直接去用，子项目就不用再单独添加依赖了。一个项目存在多个模块，可能同时由多个人开发，比如abc3个模块，3个模块都是基于spring的那么3个开发都需要引入spring的核心jar包，这样就引入了3份，但是使用父子工程，则只需要在父工程中引入了，则子工程自动继承。

## 创建方法

### 创建父子项目

首先，创建一个普通项目（不选择模板创建，一路next下去）

然后，选中父项目，按此选择创建子项目

![](D:\E\myideal\imges\fuzi1.png)

这样父子项目就创建完了，但父项目和子项目的 pom 文件仍存在一定问题，要进行父项目与子项目 pom 文件的修改

### 修改pom文件

首先修改父项目pom文件，添加如下标签（module标签中填写子模块名称）

```xml
<modules>
	<module>servlet_test</module>
</modules>
```

并修改打包方式

```xml
<packaging>pom</packaging>
```

然后修改子项目pom文件中parent标签的内容
在父项目中找到下面内容，然后复制粘贴到子项目的parent标签中

```xml
<groupId>org.example</groupId>
<artifactId>trueJavaWeb</artifactId>
<version>1.0-SNAPSHOT</version>
```

子项目的 parent 标签修改完后，如下

```xml
<parent>
    <groupId>org.example</groupId>
    <artifactId>trueJavaWeb</artifactId>
    <version>1.0-SNAPSHOT</version>
</parent>
```

自此，父子项目就真正创建完成了


