测试代码：
```java
public static void main(String[] args) {
        ArrayList test1 = new ArrayList();
        ArrayList test2 = new ArrayList();
        test1.add(1);
        test1.add(2);
        test2.add(3);
        test2.add(4);
        test1.addAll(test2);
        Integer int1 = 1;
        test1.add(int1);
        System.out.println(test1);
        int1 = null;
        test2 = null;
        System.out.println(test1);
    }
```

输出结果
```
[1, 2, 3, 4, 1]
[1, 2, 3, 4, 1]
```

结论，ArrayList的add方法可以添加引用类型，添加后引用类型指向的值发生变化后，不影响ArrayList.
