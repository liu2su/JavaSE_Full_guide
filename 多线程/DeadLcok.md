死锁可以帮助理解synchronize代码块，我自己写了一段代码，帮助大家理解锁的概念：

```java
package threads.Deadlock;

public class run{
    public static void main(String[] args) {
        myThread t1 = new myThread(true);
        myThread t2 = new myThread(false);
        t1.start();
        t2.start();
    }
}

class myThread extends Thread {
    private static Object lock1 = new Object();
    private static Object lock2 = new Object();
    private boolean flag;

    public myThread(boolean flag) {
        this.flag = flag;
    }

    @Override
    public void run() {
        if(flag){
            synchronized(lock1){
                System.out.println(Thread.currentThread().getName()+" lock1 grabbed");
                synchronized (lock2){
                    System.out.println(Thread.currentThread().getName()+" lock2 Grabbed");
                }
            }
        }else {
            synchronized(lock2){
                System.out.println(Thread.currentThread().getName()+" lock2 grabbed");
                synchronized (lock1){
                    System.out.println(Thread.currentThread().getName()+"lock2 Grabbed");
                }
            }
        }
    }
}

```
控制台输出后，程序一直处于运行状态，出现deadlock
```
Thread-0 lock1 grabbed
Thread-1 lock2 grabbed
```
