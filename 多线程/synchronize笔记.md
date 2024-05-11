synchronized 方法是针对同一个**对象**（不是类哦）的同一个方法的修饰符，确保一个方法在一个时间点只有一个线程操作，

课上讲的车票超卖的解决方案：
```java
package threads.syn;

public class Run {
    public static void main(String[] args) {
        Windows sell = new Windows();
        Thread t1 = new Thread(sell);
        Thread t2 = new Thread(sell);
        Thread t3 = new Thread(sell);
        t1.start();
        t2.start();
        t3.start();

    }
}

class Windows extends Thread{
    private int ticketNum = 500;
    private boolean inStock = true;

    @Override
    public void run() {
            long start = System.currentTimeMillis();
            while (inStock){
                sell();
                try {
                    Thread.sleep(500);
                }catch (Exception e){
                    e.getMessage();
                }
            }
            long end = System.currentTimeMillis();
            System.out.println("time cost: " + (end-start));


    }

    private synchronized void sell(){
        if(ticketNum <= 0){
            System.out.println(Thread.currentThread().getName() + "out of stock");
            inStock = false;
            return;
        }else {
            System.out.println(Thread.currentThread().getName() + " sell one ticket");
            ticketNum--;
            System.out.println("Ticket left: " + ticketNum);

        }
    }
}
```
三个线程同时卖票，卖光50张票所需时间是84198毫秒。

为什么我要提毫秒数呢？因为加了synchronized方法之后，给人的感觉是“一个线程”在操作，消耗时间和一个线程卖500张票是差不多的，其实，不是，因为线程操作完sell()之后便会继续执行代码，这里只有一个sell(),所以看不出来，我们用sleep方法，模拟其余代码执行的时间。

我们用单线程卖票：
```java
package threads.syn;

public class Compare {
    public static void main(String[] args) {
        long start = System.currentTimeMillis();
        win w = new win();
        w.start();
        long end = System.currentTimeMillis();
        System.out.println("time cost: " + (end-start));
    }
}

class win{
    int ticketNum = 500;
    boolean inStock = true;

    public void start(){
        while (inStock){
            sell();
        }
    }

    private synchronized void sell(){
        if(ticketNum <= 0){
            System.out.println(Thread.currentThread().getName() + "out of stock");
            inStock = false;
        }else {
            System.out.println(Thread.currentThread().getName() + " sell one ticket");
            ticketNum--;
            System.out.println("Ticket left: " + ticketNum);
            try {
                Thread.sleep(500);
            }catch (Exception e){
                e.getMessage();
            }
        }
    }
}
```

只用一个线程，耗时252773，大约是三个线程的三倍。

但是去掉sleep方法，单线程运行时间比多线程低，单线20ms，多线33ms，这是因为我们加锁的代码是涉及数据共享的代码，剩余的代码是各个线程并发进行，这里我们没有体现出来。。
