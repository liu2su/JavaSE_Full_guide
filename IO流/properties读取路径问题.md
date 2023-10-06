请看下面的代码：
```java
package exercise.IO.h2;

import java.io.FileReader;
import java.io.IOException;
import java.util.Properties;

public class ProperTool {
    public static void main(String[] args) {
        Properties tool = new Properties();
        String properPath = "src\\exercise\\IO\\h2\\dog.properties";

        try {
            tool.load(new FileReader(properPath));
        } catch (IOException e) {
            throw new RuntimeException(e);
        }

        Dog dog = new Dog((String)tool.get("name"),Integer.parseInt((String) tool.get("age")),(String)tool.get("color"));
        System.out.println(dog);
    }
}

```

这是一个简单的properties读取程序。我想说的是读取路径的问题。

路径无非就是相对路径和绝对路径，绝对路径从盘根目录开始即可。

但是相对路径就有需要注意的地方了：相对路径不是从当前类的路径开始的，而是从**包的根目录开始的**在本题中需要从src文件夹开始，即使我们的properties文件和class文件在一个自包下。
