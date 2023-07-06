抽象类是不能用private, static和final来修饰的。
1. 不能用static 修饰很好理解，因为静态方法是属于类的，所以静态方法必须满足给类调用，如果通过类无法调用，那么这种静态方法肯定是不对的。

   为了达到这一要求，static方法就必须有方法体，即已经实现了，也就不是抽象方法了。所以静态（static）方法不能是抽象方法，即abstract不能与static同时修饰方法。即没有类抽象方法。

2. 不能用final修饰 也好理解，abstract修饰的类需要被子类继承，abstract修饰的方法需要子类重写，但是final修饰的类不能被继承，final修饰的方法也不能被子类重写。
3. **不能用private修饰这一点我就有疑惑了** 这就迁出了一个我一直疑惑的机制：

   **子类到底能不能继承父类的私有属性？**

   首先可以明确的一点是，子类要是想访问父类的私有成员则必须使用父类提供的方法完成。
   - 从继承的概念来说，private和final不被继承。Java官方文档上是这么说的。
     ```
     A subclass does not inherit the private members of its parent class. However,
     if the superclass has public or protected methods for accessing its private fields,
     these can also be used by the subclass.
     ```
     
   - 从内存的角度来说，父类的一切都被继承（从父类构造方法被调用就知道了，因为new一个对象，就会调用构造方法，
     子类被new的时候就会调用父类的构造方法，所以从内存的角度来说，子类拥有一个完整的父类）。子类对象所引用的内存有父类变量的一份拷贝。
     如果一个子类继承了父类，那么这个子类拥有父类所有的成员属性和方法，即使是父类里有private属性的变量，子类也是继承的，
     只不过不能使用，也就是说，它继承了，但是没有使用权，似乎又点矛盾，用我们通俗的说法就是
     只能看，不能用，虽然是这样，但是，我们还是可以通过set和get的方法来间接的访问父类中的private属性的变量。

     **这点很重要，因为从这个角度理解，private是不能参与重写的，也就是说即便格式满足重写要求，也是两个不同的方法。**
     


