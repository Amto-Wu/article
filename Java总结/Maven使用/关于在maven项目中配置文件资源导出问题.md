关于在maven项目中配置文件资源导出问题

标准的Maven项目都会有一个resources目录来存放我们所有的资源配置文件，但是我们往往在项目中不仅仅会把所有的资源配置文件都放在resources中，同时我们也有可能放在项目中的其他位置，那么默认的maven项目构建编译时就不会把我们其他目录下的资源配置文件导出到target目录中，就会导致我们的资源配置文件读取失败，从而导致我们的项目报错出现异常，比如说尤其我们在使用MyBatis框架时，往往Mapper.xml配置文件都会放在dao包中和dao接口类放在一起的,那么执行程序的时候，其中的xml配置文件就一定会读取失败，不会生成到maven的target目录中，所以我们要在项目的pom.xml文件中进行设置，并且我建议大家，每新建一个maven项目，就把该设置导入pom.xml文件中，以防不测！！！

``` xml
    <build>
        <resources>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>true</filtering>
            </resource>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>true</filtering>
            </resource>
        </resources>
    </build>
```

后记

关于`<filtering>`是 false 还是 true ，看实际情况