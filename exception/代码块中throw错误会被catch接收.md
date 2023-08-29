
Java 的throwable存在两类：error和exception.

我们程序员可以通过处理异常来保证程序的健壮性，处理异常分为两类：
1. 在该方法内部处理， 使用try catch，一般处理的是RunTimeException
2. throws到上一个类，直到虚拟机。

```java
@SuppressWarnings({"all"})
public class EcmDef {
    public static void main(String[] args) {

        try {

            //先验证输入的参数的个数是否正确 两个参数
            if(args.length != 2) {
                throw new ArrayIndexOutOfBoundsException("参数个数不对");
            }

            //先把接收到的参数，转成整数
            int n1 = Integer.parseInt(args[0]);
            int n2 = Integer.parseInt(args[1]);

            double res = cal(n1, n2);//该方法可能抛出ArithmeticException
            System.out.println("计算结果是=" + res);

        }
        catch (ArrayIndexOutOfBoundsException e) {System.out.println(e.getMessage());}
        catch (NumberFormatException e) {
            System.out.println("参数格式不正确，需要输出整数");
        } catch (ArithmeticException e) {
            System.out.println("出现了除0的异常");
        }
        System.out.println("程序继续运行");


    }
    //编写cal方法，就是两个数的商
    public static double cal(int n1, int n2) {
        return n1 / n2;
    }
}

```

这道题里，try代码块里throw一个异常，会被catch接收并处理，如果没有接收，则会被默认抛出直到虚拟机。
**对try-catch代码块理解的不够深刻，不要觉得显式throw命令有什么特殊的**
