以下代码输出什么：

```java
public class Test {   //公有类
    int count = 9; //属性
    public void count1() { //Test类的成员方法
 			count=10;//这个count就是属性  改成 10
        	System.out.println("count1=" + count); //10  
    }
    public void count2() {  //Test类的成员方法
        System.out.println("count1=" + count++);
    } 
   
   	//这是Test类的main方法, 任何一个类，都可有main
    public static void main(String args[]) {
        new Test().count1()
       //1.  new Test()	是匿名对象， 匿名对象使用后，就不能使用
       //2.  new Test().count1() 创建好匿名对象后, 就调用count1()
      面向对象基础/构造函数的复用.md
      
       Test t1= new Test();
       t1.count2();
       t1.count2();
    }
}
```
本题涉及了匿名对象的用法，匿名对象没有引用变量接收他的地址，所以只能用一次：

``` new Test().count1()```语句执行后，jvm执行对象创建流程，再初始化完成后调用count1方法，调用count1方法后，如果有赋值运算符则将地址返回给变量，

但是该语句没有，所以这行代码执行完成后会被垃圾回收机制回收空间。
