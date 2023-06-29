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
