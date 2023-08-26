包装类是基础数据类型的类形态，虽然是引用类型，但是包装类之间也存在的类型转换。


例：
```java
public class test {
    public static void main(String[] args) {
        Object obj = true?new Integer(1):new Double(2);
        System.out.println(obj);//1.0
    }
}

```

这段代码会输出1.0。

这是因为 Java 中的三元条件运算符要求两个分支的返回类型一致或者可以进行类型转换。
在这里，一个分支返回 Integer，另一个分支返回 Double，它们可以被转换为共同的父类类型 Object。
在这种情况下，由于 obj 是声明为 Object 类型，所以 Java 会自动将 Integer 类型的 1 转换为 Double 类型的 1.0，因为这是合法的类型转换。
所以最终 obj 包含的是 1.0，并且打印出来的结果是 1.0。

此时，obj 的编译时类型是 Object，而运行时类型是 Double
