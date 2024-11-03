**注解的本质就是接口**
在我们写注解的时候，为什么要在变量名后面写括号？相信很多人都有这个疑问。
这是因为注解本质上是接口的扩展，不是类，也不能使用 new 来创建注解实例。
而，gerAnnotation 会返回一个注解的“实例”，这又是怎么回事？
其实这不是注解的实例，而是JAVA通过动态代理实现注解接口的类的实例
请看下面的代码：
```java
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.reflect.Method;

// 定义一个注解
@Retention(RetentionPolicy.RUNTIME)
@interface MyAnnotation {
    String value();
}

// 使用注解
public class Example {
    @MyAnnotation("Hello, Annotation!")
    public void myMethod() {
    }

    public static void main(String[] args) throws NoSuchMethodException {
        Method method = Example.class.getMethod("myMethod");

        // 获取注解对象
        MyAnnotation annotation = method.getAnnotation(MyAnnotation.class);

        // 检查是否获取到注解
        if (annotation != null) {
            System.out.println("注解的类对象: " + annotation.getClass()); // 输出代理类信息
            System.out.println("注解的值: " + annotation.value());
        } else {
            System.out.println("注解不存在");
        }
    }
}

```

输出：
注解的类对象: class com.itheima.$Proxy1
注解的值: Hello, Annotation!

解释输出

annotation.getClass() 输出的类信息表明，这个对象是由 JVM 动态生成的代理类（如 com.sun.proxy.$Proxy1）。
这个代理对象实现了注解接口（如 MyAnnotation），并返回注解属性值。

注解对象的本质

动态代理：当你通过反射获取注解时，JVM 创建了一个动态代理对象来实现注解接口。该对象可以通过引用调用其方法来获取注解的属性值。
注解本身没有实例，但在运行时，JVM 通过动态代理生成了一个实现注解接口的对象，该对象提供了类似实例的行为。
你可以使用这个对象访问注解的属性，但它不是真正的类实例，而是 JVM 生成的代理。
