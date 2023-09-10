在学过程中我发现，使用集合调用toString方法会打印出集合内的元素，这是怎么做到的呢？

原来在一个叫做abstractCollection的抽象类内重写了toString方法，以HashSet为例,其实老师在课上讲的集合结构图是简化版的。
真实的结构图是：

![1](https://github.com/liu2su/JavaSE_Full_guide/assets/96462566/60d000ef-930a-46f4-9e2b-5f253f288a5b)

所以HashSet可以调用abstractCollection重写的toString方法
