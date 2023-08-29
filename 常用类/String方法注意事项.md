String类的方法有很多，这里一toUpperCase()为例，提醒读者注意method的用法，养成看源码的好习惯

```java
  String str3 = "hello";
  str3.toLowerCase();
  System.out.println(str3); //output: hello
```

toUpperCase() return 一个 new String需要一个变量接收，所以str3值不改变。 以此为例，仅做提醒。
