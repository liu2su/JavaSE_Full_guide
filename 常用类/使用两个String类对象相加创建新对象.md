```java
public class StringExercise08 {
    public static void main(String[] args) {
        String a = "hello"; //创建 a对象
        String b = "abc";//创建 b对象
        //1. 先 创建一个 StringBuilder sb = StringBuilder()
        //2. 执行  sb.append("hello");
        //3. sb.append("abc");
        //4. String c= sb.toString()
        //最后其实是 c 指向堆中的对象(String) String对象里的属性value[] -> 池中 "helloabc"
        String c = a + b;
        String d = "helloabc";
        System.out.println(c == d);//真还是假? 是false
        String e = "hello" + "abc";//直接看池， e指向常量池
        System.out.println(d == e);//真还是假? 是true
    }
}
```

例：
```java
        String str = "lsy";
        String str3 = str + "1";
        String str4 = "lsy1";
        System.out.println(str3 == "lsy1"); //false
        System.out.println(str4 == "lsy1"); // true
```
