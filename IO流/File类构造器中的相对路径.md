Java File API中 构造器传入相对路径，是从哪个地方为起点开始寻找文件？

在Java的File API中，如果构造器传入一个相对路径，相对路径的起点取决于运行Java虚拟机(JVM)时的工作目录。这通常是你启动应用程序的目录。例如，如果你在命令行中启动应用程序，工作目录通常是你当前所在的目录。
```java
System.out.println(System.getProperty("user.dir"));
```
这会打印出JVM的工作目录，即相对路径的起点。例如，如果你在/home/user/projects/myapp目录下运行你的Java应用程序，并且你使用了相对路径data/file.txt，
那么实际寻找文件的路径就是/home/user/projects/myapp/data/file.txt。总结起来，Java中的相对路径是相对于当前工作目录的。

在IntelliJ IDEA中，相对路径的起点通常是项目的根目录。这是因为IDEA会将工作目录设置为项目的根目录，这样可以确保相对路径在开发环境中更具一致性和可预测性。

当你在IDEA中运行一个程序时，IDEA会自动配置运行时的工作目录，使其指向项目的根目录。查看或修改工作目录的设置：

在菜单栏中选择 Run -> Edit Configurations。
在运行配置窗口中，选择你要修改的配置。
在 Working directory 字段中，你可以看到或更改工作目录。
