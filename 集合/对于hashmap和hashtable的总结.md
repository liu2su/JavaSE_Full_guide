HashMap和HashSet都是利用hashmap来实现的，hashmap本质是通过数组+链表+红黑树来实现的。

key的内容不同，经过计算的hash(key）可能相同。所以当hash值相同时，**并且**key不同，并且与该链表每一个节点都不同，则会在链表末尾新增一个节点。

如果hash值相同，**并且**key值不同，那么就会发生value值的替换。

这是hashmap的基本原理。

通过这个原理可以解释，当一个节点key相同时，HashMap和HashSet所展现的不同特性：
1. 在hashset中，节点的value值都是相等的，指向一个默认的Object，真正存储数据的是key，所以当一个重复对象加入时，本质是重复key，实际上执行了value替换，可以没有变。
而又因为value不是实际存储数据的元素，所以实现了禁止添加重复元素的功能。 而hashmap,存储的数据是键值对。

2. 总的来讲，key是一个值，hash是根据key计算得到的整数，key不同，hash有可能相同。


hashtable是线程安全版本的hashmap,并且不能加null 的key和value，并且扩容机制有区别，除此之外没有区别。
