字符串常量池在JVM源码中对应的类是StringTable，底层实现是一个Hashtable

**我们以String s = new String("xyz")**;为例：

首先去找字符串常量池找，看能不能找到“xyz”字符串对应对象的引用，如果字符串常量池中找不到：
1. 创建一个String对象
2. 将创建的String对象封装成HashtableEntry，作为StringTable的value进行存储
3. new String("xyz")会在堆区又创建一个String对象，char数组直接指向创建好的char数组对象

如果字符串常量池中能找到：new String("xyz")会在堆区创建一个对象，char数组直接指向已经存在的char数组对象

**而String s = "xyz"是怎么样的逻辑**：

首先去找字符串常量池找，看能不能找到“xyz”字符串的引用，如果字符串常量池中能找不到：
1. 创建一个String对象
2. 将创建的String对象封装成HashtableEntry，作为StringTable的value进行存储
3. 返回创建的String对像：

如果字符串常量池中能找到：直接返回找到引用对应的String对象

可以这样简单理解，储存在常量池里的字符串也是一个个的包含value数组的String对象（其实是一个个的hashtable entry）

具体看这篇文章  [文章](https://segmentfault.com/a/1190000039074103)
