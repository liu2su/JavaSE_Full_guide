有这么一道题：

```java
boolean x = true;
boolean y = false;
short z = 46;
if((z++ == 46)&&(y=true)){
  //z++ == 46 先判断后自增
  z++;
}
if((x= false) ||(++z == 49)){
  z++;
}
System.out.println("z=" + z);
```

这道题答案是50，解析没有，记录这道题提醒自己一下逻辑与，短路与，逻辑或和短路或的机制的不同。
