## static方法能不能被重写呢？

答案很明确：java的静态方法不能被重写！
静态方法，可以通过类直接调用（是属于类的方法，静态方法在代码中的调用方式一般形式是：Math.abs(); 当然通过引用该类型对象的变量也可以调用，只是通常不这样使用）；

实例方法，只能通过对象调用；

重写的目的在于父类引用可以根据子类对象的运行时实际类型不同而调用不同实现代码，从而表现出多态。
并且，静态方法无需创建对象即可使用，而重写的方法发挥作用，需要父类引用，和（不同的）子类对象。

假设我们有以下代码：
```java
class A{
	public static show(){
		System.out.println(" Static Method of A");
	}
}
class B extends A{
	public static show(){
		System.out.println("Static Method of B");
		
	}
}

```

根据代码运行程序：

![res](https://github.com/liu2su/Java/assets/96462566/e8158219-74b8-41c9-839e-45ff6aa92e20)


