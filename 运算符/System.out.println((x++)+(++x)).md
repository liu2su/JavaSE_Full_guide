请问下面代码输出什么：

```java
  public class TestOrder2 {
    public static void main(String[] args) {
        int x = 0;
        System.out.println(x++ + ++x);
    }
}
```
输出结果为2，以下是解析：

变量名在前的自增运算符，先取变量值做运算再自增，这里x++和++x是表达式（单目运算符和赋值运算也是表达式，这点很容易忽略），表达式也有值，若x初值为0，则x++表达式的值为0（先参与运算后自增），取值后自增，x = 1。此时运算顺序继续向右运动，因为自增符优先级高于+，所以先取++x的值，此时 x = 1，先自增 x = 2，后取值。所以最后的结果是0+2 = 2

同样的：
```java
public class TestOrder2 {
    public static void main(String[] args) {
        int x = 0;
        System.out.println(++x + x++);
    }
}
```

x初值为0，++x表达式的值为1。计算后面的x++表达式值时，要把前面前面的++x当做语句，相当于前面执行了++x;，这时候x值为1，所以后面x++表达式的值为1。最后执行System.out.println(1 + 1);，结果为2。
