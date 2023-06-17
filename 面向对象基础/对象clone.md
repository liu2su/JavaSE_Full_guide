这个问题是我在克隆一个对象时发现的，下面的代码创建了一个新对象，并赋值旧对象的成员变量（包括一个string）:

```java
  public class MethodExercise02 { 

	//编写一个main方法
	public static void main(String[] args) {
		
		Person p = new Person();
		p.name = "milan";
		p.age = 100;
		//创建tools
		MyTools tools = new MyTools();
		Person p2 = tools.copyPerson(p);

		p.name = "new";
		System.out.println(p.name);//这里输出new
		System.out.println(p2.name);//这里输出milan
	}
}

class Person {
	String name;
	int age;
}

class MyTools {
	
	public Person copyPerson(Person p) {
		//创建一个新的对象
		Person p2 = new Person();
		p2.name = p.name; //把原来对象的名字赋给p2.name
		p2.age = p.age; //把原来对象的年龄赋给p2.age
		return p2;
	}
}
```

JVM内存图我就不画了，脑补即可，不是很复杂。我说一下我犯错的点和我理解,首先string在JVM的储存方式有以下两种：

1. String s1="abc"； s1指向的是String常量池中的字符串
2. String s2=new String("abc")；  s2指向的是堆上的对象

首先对象克隆产生的p2里的string字段是指向了常量池里“milan”的地址，p也指向了**同一个**地址。

当p的string字段改变时，会很想当然的认为p1里的字段也改变了（共同指向同一个地址嘛）但是实际上p.name = "new"会在常量池里开辟一个“new”字符串并指向他，没有影响p1。

所以p1还是指向常量池里的“milan”字符串。
