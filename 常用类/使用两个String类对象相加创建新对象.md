```java
public class StringExercise08 {
    public static void main(String[] args) {
        String a = "hello"; //创建 a对象
        String b = "abc";//创建 b对象
        String c = a + b;
        //1. 先 创建一个 StringBuilder sb = StringBuilder()
        //2. 执行  sb.append("hello");
        //3. sb.append("abc");
        //4. String c= sb.toString()
        //字符串 c 指向堆中的String对象,这个对象里的属性value字符串指向池中 "helloabc"
        String d = "helloabc";
        System.out.println(c == d);//false
        String e = "hello" + "abc";//这种运算 e指向常量池
        System.out.println(d == e);//true
        //注意我们这里使用的是==进行比较，而不是equals方法，所以比较的是地址
    }
}
```

例：
```java
        String str = "lsy";
        String str3 = str + "1"; // 有String类型的变量参与运算，使用StringBuilder
        String str4 = "lsy1";
        System.out.println(str3 == "lsy1"); //false
        System.out.println(str4 == "lsy1"); // true
        //注意我们这里使用的是==进行比较，而不是equals方法，所以比较的是地址
```
