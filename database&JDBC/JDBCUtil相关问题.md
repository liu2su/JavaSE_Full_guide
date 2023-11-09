在工具类的静态代码块里，我们要注册驱动，有一句代码我认为值得解析一下：

```java
JDBCUtil.class.getClassLoader().getResourceAsStream("jdbc.properties")
```

1. ```.getResourceAsStream("jdbc.properties")```

使用类加载器从类路径中获取指定文件（在这里是 jdbc.properties）的输入流。当你使用 getResourceAsStream("jdbc.properties") 时，
Java 会在类路径下搜索与给定文件名匹配的资源。如果 jdbc.properties 文件位于类路径下，那么这个方法将返回一个 InputStream，可以用于读取该文件的内容。

这里为什么类加载器可以找到properties文件呢？是因为我们用IDEA的功能标记了！

Mark Directory as Resource Root" 是 IntelliJ IDEA 提供的另一个功能，用于标记一个文件夹作为资源根目录。
资源文件可以包括但不限于配置文件、图像、样式表、模板等。标记目录为资源根可以在项目构建和运行时的类路径配置中包含这些资源，确保它们可以被正确加载和访问。


