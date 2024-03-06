我们都知道，ArrayList的扩容机制实在grow方法里实现的，

这里有个需要注意的点，那就是使用有参构造器创建一个size为1的List

扩容时会执行：
```java
newCpacity = oldCapacity + (oldCapacity >> 2) // 此时 oldCapacity = 1 ，所以newCpacity是 1 + 0 = 1 
```

此时会进入下一个if语句比较两个整数大小，而明显new是比min小的，因此此时new 会被赋予min的值，也就是2!!!!

这个神奇之处在于，一般书上讲的都是1.5倍扩容，然而size = 1时是2倍扩容。

这是由源码决定的，虽然不影响使用但是感觉如果面试的时候问一下答上来感觉还是很酷。
