## Java 中 char 类型的本质
char看上去是很简单的，正如我们之前所说，char用于表示一个字符，这个字符可以是中文字符，也可以是英文字符。赋值时把常量字符用单引号括起来，例如：

```java
char c = 'A';
char z = '中';
```

但为什么字符类型也可以进行算术运算和比较？char的本质到底是什么呢？

字符型存储到计算机中，需要将字符对应的码值（整数）找出来，比如‘a’: 需要注意的是，char可以赋予整数常量值，但不能赋予变量值

存储： ‘a’ => 码值97 => 二进制（1100001）=> 存储

读取：二进制（1100001） => 97 => a => 显示

char本质上是一个固定占用两个字节的无符号正整数，这个正整数对应于Unicode编号，用于表示那个Unicode编号对应的字符。

不论在编写.java 文件时使用的是哪种字符集， javac 都会将其编译为utf-8文件。 所以不论使用何种字符集，
用整数值赋予char时，整数值对应的编码应该是Unicode字符集。

char有多种赋值方式：
```java
char c = 'A'       // 1
char c = '马'      // 2
char c = 39532     // 3
char c = 0x9a6c    // 4
char c = '\u9a6c'  // 5
```
此外char还可以和整数比较：
```java
import java.util.Scanner;

public class test{
	public static void main(String[] args){
		double score;
		char gender;
		Scanner scoreScan = new Scanner(System.in);
		System.out.println("输入你的成绩：");
		score = scoreScan.nextDouble();
		System.out.println("输入你的性别：");
		gender = scoreScan.next().charAt(0);
		if(score >= 8.0){
			//分组
			if(gender == 30007){
        //30007是‘男’在Unicode下的十进制，的值这段代码等价于 == ‘男’
				System.out.println("入选男子组");
			}
			else{
				System.out.println("入选女子组");
			}
		}
		else{
			System.out.println("您没有入选。");
		}
	}

}
```

