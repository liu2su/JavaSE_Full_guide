看下面一行代码
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

这行代码输出的是java了。体会不同
