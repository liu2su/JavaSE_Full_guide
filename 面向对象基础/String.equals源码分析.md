以下是String类内的equals方法

```java
public boolean equals(Object anObject) {
        if (this == anObject) { //如果是同一个对象
            return true;
        }
        if (anObject instanceof String) { //String 的修饰符是final不存在子类
            String anotherString = (String)anObject;
            int n = value.length; //value是字符串的属性，用来存储字符串的内容（是个数组）
            if (n == anotherString.value.length) { //如果长度相同
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {// 一个个比较字符
                    if (v1[i] != v2[i]) 
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }
```

在分析源码时我犯了一个错误，因为我没有彻底理解向下转型已经编译类型的概念：

我认为``` if (anObject instanceof String)``` 这句话已经判定了 anObject 是否为String,或者String的子类，为什么下面还需要向下转型呢？

这是因为anObject的编译类型是Object,编译器是不知道他的运行类型的，所以如果不转换类型是无法访问String 的特有字段和方法。
