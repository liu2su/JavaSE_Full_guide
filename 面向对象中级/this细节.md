### 深入理解this和super

this是一个引用，this是一个变量，在this中保存了对象地址（指向自身），this存储在JVM堆内存的内部。

首先this调用构造器是不能进行递归调用的：

```java
class Mytools {
    public Mytools() {
        this();//会报错，recursive constructoe invokation
    }
    
}
```

所以如果想利用this调用构造器，构造器必须有俩个（当然不能互相调用，这样也会报错：recursive constructoe invokation，总而言之构造器的一切使用规则都是为了确保对象能够顺利初始化）
