这里补充一下wait和notify的运行机制，需要说明的是notify和wait的调用者是对象锁本身，所以只会唤醒处于使用同一个对象锁上的，且处于"等待状态"的任意一个线程。

![20190804232832471](https://github.com/liu2su/JavaSE_Full_guide/assets/96462566/1f2da4a6-e2b7-44c1-893d-8929b660d85a)

- 线程1获取对象A的锁，正在使用对象A。
- 线程1调用对象A的wait()方法。
- 线程1释放对象A的锁，并马上进入等待队列。
- 锁池里面的对象争抢对象A的锁。
- 线程5获得对象A的锁，进入synchronized块，使用对象A。
- 线程5调用对象A的notifyAll()方法，唤醒所有线程，所有线程进入同步队列。若线程5调用对象A的notify()方法，则唤醒一个线程，不知道会唤醒谁，被唤醒的那个线程进入同步队列。
- notifyAll()方法所在synchronized结束，线程5释放对象A的锁。
- 同步队列的线程争抢对象锁，但线程1什么时候能抢到就不知道了。

### 同步队列状态
- 当前线程想调用对象A的同步方法时，发现对象A的锁被别的线程占有，此时当前线程进入同步队列。简言之，同步队列里面放的都是想争夺对象锁的线程。
- 当一个线程1被另外一个线程2唤醒时，1线程进入同步队列，去争夺对象锁。
- 同步队列是在同步的环境下才有的概念，一个对象对应一个同步队列。
- 线程等待时间到了或被notify/notifyAll唤醒后，会进入同步队列竞争锁，如果获得锁，进入RUNNABLE状态，否则进入BLOCKED状态等待获取锁。
