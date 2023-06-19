以下代码属于重复定义，不属于重载：

仅仅是形参变量名不同不算构成重载，属于重复定义,此外如果只有return的数据类型不同，也不能算是构成重载。

```java
class Calulator{
  public void calculate(int n1, int n2)  {
    System.out.println("calculate(int n1, int n2) 被调用");
    int res =  n1 + n2;
  } 
  
  //看看下面是否构成重载
  public int calculate(int a1, int a2)  {
    System.out.println("calculate(int n1, int n2) 被调用");
    return a1 + a2;
  } //仅仅是形参变量名不同不算构成重载，属于重复定义,此外如果只有return的数据类型不同，也不能算是构成重载。
  
}

```
