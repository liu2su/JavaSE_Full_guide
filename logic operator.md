有这么一道题：

```java
boolean x = true;
boolean y = false;
short z = 46;
if((z++ == 46)&&(y=true)){
  z++;
}
if((x= false) ||(++z == 49)){
  z++;
}
System.out.println("z=" + z);
```

这道题答案是50，解析没有，记录这道题提醒自己一下逻辑运算符的用法。
