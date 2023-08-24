Java中枚举存在在Method Area(方法区)

看下面的代码：
```java
public enum T {
E1, E2

}
```
使用javap decompile:
```
$ javap T.class

Compiled from "T.java"

public final class io.zhudy.web.T extends java.lang.Enum {
public static final io.zhudy.web.T E1;

public static final io.zhudy.web.T E2;

public static io.zhudy.web.T[] values();

public static io.zhudy.web.T valueOf(java.lang.String);

static {};

}
```

可以发现常量最后实际都是被编译为静态变量了，Java中静态变量都是存储在Method Area。
根据我的理解，抽象类，接口的代码都存在于方法区，只有需要new的引用才会存在于heap中。
enum 类和class 类不同，enum类的实例数和内容都是确定的，我猜想：当枚举类代码写好之后，编译完成后运行，虚拟机会在方法区内创建n个枚举类实例,用一个线性数据结构存储。
每个实例都继承了一个Enum抽象类。和class实例不同，enum类的实例都存储在方法区，这些都是我的猜想，也许不对。
