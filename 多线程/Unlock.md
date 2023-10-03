在某些情况下线程会释放锁，大家不用去背，只需要抓住一条：

**线程从 runnable 状态进入其他状态（blocked,waiting和terminate）就会unlock** 注意：timed-waiting不会unlock

抓住上面那一条，是不是就很清晰了，比如sleep方法会释放锁吗？不会的，sleep方法没有改变线程状态（线程处于timed-wait）。
