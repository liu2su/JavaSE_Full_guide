hashset在判断元素是否重复时，需要判断两个对象的hashcode,和equals().

两者必须同时满足ture相同才会让hashset认为两个Node相同。

封装类和String都重写了hashcode方法，所以同字面量的不同实例会有相同的hash.


```java
public class Homework1 {
    public static void main(String[] args) {
        Employee e1 = new Employee("liu2su",10);
        Employee e2 = new Employee("liu2su",10);
        Set set = new HashSet();
        System.out.println(set.add(e1));
        System.out.println(set.add(e2));
        set.add(1000);
        System.out.println(set.add(1000));
    }
}
```


```
true
true
false
```
