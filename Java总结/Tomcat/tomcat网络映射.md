tomcat网络映射

网络映射

原因

- 保护服务器上的资源，不允许浏览器直接访问

方法

网络映射分为以下几步：首先需要注册 Servlet ，然后再进行网络映射，举例如下

在 web.xml 文件中注册 Servlet 

```xml
<servlet>
    <servlet-name>hello</servlet-name>
    <servlet-class>com.example.demo1.HelloServlet</servlet-class>
</servlet>
```

然后添加网络映射

```xml
<servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/hello</url-pattern>
</servlet-mapping>
```

后记

- 在注册 Servlet  与网络映射过程中，要保持 注册的 servlet 与网络映射相同（即`<servlet-name>`标签中的内容相同）

- 在路由映射中，可使用通配符，如下实现默认路径处理（当没有写具体路径时），

```xml
<servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/*</url-pattern>
</servlet-mapping>
```

- 自定义后缀访问（只要是以此结尾的后缀，都会映射到 hello ，后缀可以任意发挥)

```xml
<servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>*.do</url-pattern>
</servlet-mapping>
```

但不能写成如下形式

```xml
<servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/*.do</url-pattern>
</servlet-mapping>
```

