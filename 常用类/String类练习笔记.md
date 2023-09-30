**第一题**看下面一行代码
```java
class Test1 {
    String str = new String("hsp");
    final char[] ch = {'j', 'a', 'v', 'a'};

    public void change(String str, char ch[]) {
        str = "java";
        ch[0] = 'h';
    }

    public static void main(String[] args) {
        Test1 ex = new Test1();
        ex.change(ex.str, ex.ch);
        System.out.print(ex.str + " and ");
        System.out.println(ex.ch);
    }
}
```

这行代码输出的是hsp and hava. 

把这行代码改变一下：
```java
public class Test1 {
    String str = new String("hsp");
    final char[] ch = {'j', 'a', 'v', 'a'};

    public void change() {
        str = "java";//去掉了局部变量
    }

    public static void main(String[] args) {
        Test1 ex = new Test1();
        ex.change();
        System.out.print(ex.str);
    }

}
```
这行代码输出的是java了。不同点在于局部变量的存在导致了指向不同

**第二题** 我们都知道比较两个String对象时，要用equals()来比较内容。但是在有些情况下，也是可以通过==来比较的，比如：
```java
        String str = "lsy";
        String str2 = new String("lsy");
        System.out.println(str == "lsy");//output true
        System.out.println(str2 == "lsy");// output false
```
我的理解是，字符串字面量都是存储在常量池的。（所以str和 "lsy"地址一样，显示为true,但是很明显这种比较方法不推荐，因为比较的是地址）
