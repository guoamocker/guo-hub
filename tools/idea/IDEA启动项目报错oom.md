idea启动项目报错oom

```java
java: java.lang.OutOfMemoryError: WrappedJavaFileObject[org.jetbrains.jps.javac.InputFileObject[file:/E:/codes/40_source-java6%20-%20副本/30_业务组件/commons-np-fygyyw/java/src/com/thunisoft/np/fy/fygyyw/service/impl/SpzzcyServiceImpl.java]]@pos15520: WrappedJavaFileObject[org.jetbrains.jps.javac.InputFileObject[file:/E:/codes/40_source-java6%20-%20副本/30_业务组件/commons-np-fygyyw/java/src/com/thunisoft/np/fy/fygyyw/service/impl/SpzzcyServiceImpl.java]]@pos15523: WrappedJavaFileObject[org.jetbrains.jps.javac.InputFileObject[file:/E:/codes/40_source-java6%20-%20副本/30_业务组件/commons-np-fygyyw/java/src/com/thunisoft/np/fy/fygyyw/service/impl/SpzzcyServiceImpl.java]]@pos15524: WrappedJavaFileObject[org.jetbrains.jps.javac.InputFileObject[file:/E:/codes/40_source-java6%20-%20副本/30_业务组件/commons-np-fygyyw/java/src/com/thunisoft/np/fy/fygyyw/service/impl/SpzzcyServiceImpl.java]]@pos15553: WrappedJavaFileObject[org.jetbrains.jps.javac.InputFileObject[file:/E:/codes/40_source-java6%20-%20副本/30_业务组件/commons-np-fygyyw/java/src/com/thunisoft/np/fy/fygyyw/service/impl/SpzzcyServiceImpl.java]]@pos15542: GC overhead limit exceeded

```

- 调整idea配置

    - build process heap size(Mbytes) 调整700 -> 2048

![](https://gitee.com/guoamocker/picture/raw/master/markdown/20210803174647.png)

- importor vm options 参数
![](https://gitee.com/guoamocker/picture/raw/master/markdown/20210803175716.png)