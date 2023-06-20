## 1. 以下代码属于重复定义，不属于重载：

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
## 2. 当存在重载方法，传入实参与形参值类型不完全匹配但符合自动转换原则时，方法调用机制是什么呢？

```java
public class test { 

	//编写一个main方法
	public static void main(String[] args) {
		Methods method = new Methods();
		//注意以下语句输出值
		System.out.println(method.max(10.0, 1.4, 30)); // 会进入方法二
		System.out.println(method.max(1,2,3));// 不考虑自动转换，0个参数与方法一匹配，1个参数与方法二匹配，也会进入方法二
		System.out.println(method.max(1.0,2,3));//不考虑自动转换，1个参数与方法一匹配，2个参数与方法二匹配还是会进入方法二
		System.out.println(method.max(1.0,2,3.0));//不考虑自动转换，2个参数与方法一匹配，1个参数与方法二匹配还是会进入方法一

	}
}

class Methods {

	public double max(double n1, double n2, double n3) {
		//方法一
		System.out.println("max(double n1, double n2, double n3)");
		//求出n1 和  n2的最大值
		double max1 = n1 > n2 ? n1 : n2;
		return max1 > n3 ? max1 : n3;
	}

	public double max(double n1, double n2, int n3) {
		//方法二
		System.out.println("max(double n1, double n2, int n3)");
		//求出n1 和  n2的最大值
		double max1 = n1 > n2 ? n1 : n2;
		return max1 > n3 ? max1 : n3;
	}
	
}
```
