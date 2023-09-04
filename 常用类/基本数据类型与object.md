学习Arrays 类-自定义排序时遇到的问题：

java 中万物皆对象，除8种基础数据类型 （byte，short ，int，long,float ,double,char,boolean）以外都是Object的子类。但是如下代码为啥不会报错呢？

```java
Object o = 1; 
```

这里需要注意的一点，8种基本数据类型都有其对应的包装数据类型，在赋值的过程中进行自动装箱。可用以下方法进行验证，由最后的输出可知进行了自动装箱。

```java
public static void main(String[] args) {
        int j=1;
        Object o = j;
        //获取对象o的实际对应的类名
        System.out.println(o.getClass().getName());
    }
```
输出Integer.
