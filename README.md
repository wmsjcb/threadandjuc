### 前言
大家好,线程在现在的工作中使用的频率较高，自己构建了一个小的demo，来和大家分享下自己对线程的理解，希望和大家分享一下，希望大家能从中收益，如果有意见和好的想法请加我！
 ＱＱ:3341386488
 邮箱：QiuRunZe_key@163.com

我会不断完善，希望大家有好的想法拉一个分支提高，一起合作！


    觉得不错对您有帮助，麻烦右上角点下star以示鼓励！长期维护不易 多次想放弃 坚持是一种信仰 专注是一种态度！


## 线程可见性 volatile 和 synchronized 的区别和内容

    volatile 强制线程到共享内存中读取数据，而不从线程工作内存中读取，从而使变量在多个线程中可见
    volatile无法保证原子性，volatile属于轻量级的同步，性能比synchronized强很多(不加锁)，但是只保证线程见的可见性，
    并不能替代synchronized的同步功能，netty框架中大量使用了volatile
    ====================================================================================================
    Static保证唯一性, 不保证一致性，多个实例共享一个静态变量。
    Volatile保证一致性，不保证唯一性，多个实例有多个volatile变量
    ====================================================================================================
    1.共享变量在线程间的可见性 
    2.synchronized 实现可见性 
    3.volitile 实现可见性 
    　　指令重排序 
    　　as-if-serial语义     
    　　volatile使用注意事项 
    synchronized和volitile比较 

## 线程池讲解

    1.线程池的好处：　减少对象的开销，消亡的开销，性能提高 
    2.可以控制最大并发线程数，提高资源利用率，同时可以避免过多资源竞争，避免阻塞 
    3.提供定时执行，定期执行，并发数控制等 


## 线程安全－并发容器JUC--原理以及分析

    1.arrayList --copyonWriteArraylist 优缺点 
    2.HashSet,TreeSet -- CopyONWriteArraySet,ConcurrentSkipListSet 
    3.hashMap , treeMap -- ConcurrentHashMap,ConcurentSkipListMap(key有序，支持更高并发) 

## Concurrent同步工具类 

    countDownLatch 
    CyclicBarrier 
    Semaphore 
    Exchanger 
    ReenTrantLock 
    ReentrantReadWriteLock 

## 四种线程池与自定义线程池，底层代码
设计模式： 单例Future Master-Worker,Producer-Consumer的模式原理和实现

## CountDownLatch
    CountDownLatch是一个辅助的工具类，它允许一个或者多个线程等待一系列指定的操作的完成 
    以一个给定的数量初始化,countDown()每被调用一次，这一数量就减一.通过调用await()方法之一 
    线程可以阻塞等待这一数量到达0 
    三辆危险燃品汽车全部检查完毕后在发车, countdownlatch 初始值为3 每检查一辆减一 如果三辆车 
    都没有问题则发车  三辆车会等待 都检查完毕后才可以发车 

## CyclicBarrier
    CyclicBarrier一个同步辅助类,它允许一组线程互相等待,直到到达某 
    个公共屏障点 (common barrier point)。在涉及一组固定大小的线程的 
    程序中,这些线程必须不时地互相等待,此时 CyclicBarrier 很有用。 
    因为该 barrier 在释放等待线程后可以重用,所以称它为循环的barrier 
    起跑例子 ：  有两种用法 一种必须全部等待 另一种有超时时间  在等待某个时间后 
    可以独自起跑  

## Semaphore
    Semaphore一个计数信号量。信号量维护了一个许可集合; 通过acquire() 
    和release()来获取和释放访问许可证。只有通过acquire获取了许可证的线 
    程才能执行,否则阻塞。通过release释放许可证其他线程才能进行获取. 
    公平性:没有办法保证线程能够公平地可从信号量中获得许可。也就是 
    说,无法担保掉第一个调用 acquire() 的线程会是第一个获得一个许可的 
    线程。如果第一个线程在等待一个许可时发生阻塞,而第二个线程前来 
    索要一个许可的时候刚好有一个许可被释放出来,那么它就可能会在第 
    一个线程之前获得许可。如果你想要强制公平,Semaphore 类有一个具 
    有一个布尔类型的参数的构造子,通过这个参数以告知 Semaphore 是否 
    要强制公平。强制公平会影响到并发性能,所以除非你确实需要它否则 
    不要启用它 
## Exchanger

    Exchanger Exchanger 类表示一种两个线程可以进行互相交换对象的会 
    和点。 
    只能用于两个线程之间,并且两个线程必须都到达汇合点才会进行数 
    据交换 

## ReentrantLock
    ReentrantLock可以用来替代Synchronized,在需要同步的代码块加上 
    锁,最后一定要释放锁,否则其他线程永远进不来。 
     可以使用Condition来替换wait和notify来进行线程间的通讯, 
    Condition只针对某一把锁。 
     一个Lock可以创建多个Condition,更加灵活 
    ReentrantLock的构造函数可以如传入一个boolean参数,用来指定公平 
    非公平模式,默认是false非公平的。非公平的效率更高。 
     Lock的其他方法: 
    tryLock():尝试获得锁,返回true/false 
    tryLock(timeout, unit):在给定的时间内尝试获得锁 
    isFair():是否为公平锁 
    isLocked():当前线程是否持有锁 
    lock.getHoldCount():持有锁的数量,只能在当前调用线程内部使用,不能再其他 
    线程中使用 
## ReentrantReadWriteLock

    ReentrantReadWriteLock读写所,采用读写分离机制,高并发下读多写 
    少时性能优于ReentrantLock。 
    读读共享,写写互斥,读写互斥 
    
## ThreadPool

    newCachedThreadPool 具有缓存性质的线程池,线程最大空闲时间60s,线程 
    可重复利用(缓存特性),没有最大线程数限制。任务耗时端,数量大。 
    newFixedThreadPool 具有固定数量的线程池,核心线程数等于最大线程数, 
    线程最大空闲时间为0,执行完毕即销毁,超出最大线程数进行等待。高并 
    发下控制性能。 
    newScheduledThreadPool 具有时间调度特性的线程池,必须初始化核心线 
    程数,底层使用DelayedWorkQueue实现延迟特性。 
    newSingleThreadExecutor 核心线程数与最大线程数均为1,用于不需要并发 
    顺序执行。 
    四种线程池都是通过Executors类创建的, 底层创建的都是 
    ThreadPoolExecutor类, 可以构建自己需要的线程类 

## 设计模式：单例模式

    饿汉模式： 类加载的时候，就进行对象的创建，系统开销较大，但是 
    不存在线程安全问题 
    懒汉模式： 多数采用饿汉模式，在使用时才真正的创建单例对象，但 
    是存在线程安全问题 
    静态内部类单例：兼具懒汉模式和饿汉模式的优点 
    饿汉示例： DemoThread22 
    懒汉示例： DemoThread23（线程安全问题和解决方案） 
    懒汉模式： DemoThread24（线程安全的性能优化） 
    静态内部类单例： DemoThread25 

## 设计模式：future

    简单来说,客户端请求之后，先返回一个应答结果，然后异步的去准 
    备数据，客户端可以先去处理其他事情，当需要最终结果的时候再来 
    获取, 如果此时数据已经准备好，则将真实数据返回；如果此时数据 
    还没有准备好，则阻塞等待 
    
     JDK的Concurrent包提供了Futrue模式的实现，可以直接使用。
     使用Futrue模式需要实现Callable接口，并使用FutureTask进行封装，
    使用线程池进行提
    
## 设计模式-producer-consumer
    
     Producer-Consumer称为生产者消费者模式，是消息队列中间件的核心
    实现模式， ActiveMQ、 RocketMQ、 Kafka、 RabbitMQ
    
 ## 设计模式： Master-Worker
    
    Master-Worker模式是一种将串行任务并行化的方案，被分解的子任务在
    系统中可以被并行处理，同时，如果有需要， Master进程不需要等待所
    有子任务都完成计算，就可以根据已有的部分结果集计算最终结果集。
    客户端将所有任务提交给Master， Master分配Worker去并发处理任务，并
    将每一个任务的处理结果返回给Master，所有的任务处理完毕后,由
    Master进行结果汇总再返回给Clien
    
 ##  使用Atomic类
    
    使用AtomicInteger等原子类可以保证共享变量的原子性。 
    使用Atomic类不能保证成员方法的原子性。 
    Atomic类采用了CAS非锁机制（Check And Set)
    
## ThreadLocal

    使用ThreadLocal维护变量时，ThreadLocal为每个使用该变量的线程提供独立的变量副本，所以每一个线程都可以独立地改变自己的副本，而不会影响其它线程所对应的副本

## 同步类容器
    古老的实现方法
    Vector、HashTable等古老的并发容器，都是使用Collections.synchronizedXXX等工厂方法创建的，并发状态下只能有一个线程访问容器对象，性能很低
    
    先进的实现方法
    JDK5.0之后提供了多种并发类容易可以替代同步类容器，提升性能、吞吐量
    ConcurrentHashMap替代HashMap、HashTable
    ConcurrentSkipListMap替代TreeMap
    ConcurrentHashMap将hash表分为16个segment，每个segment单独进行锁控制，从而减小了锁的粒度，提升了性能
    
    

## 并发类容器

    Copy On Write容器,简称COW;写时复制容器，向容器中添加元素时，先将容器进行Copy出一个新容器，
    然后将元素添加到新容器中，再将原容器的引用指向新容器。并发读的时候不需要锁定容器，
    因为原容器没有变化，使用的是一种读写分离的思想。由于每次更新都会复制新容器，所以如果数据量较大，
    并且更新操作频繁则对内存消耗很高，建议在高并发读的场景下使用
    ============================================================
    CopyOnWriteArraySet基于CopyOnWriteArrayList实现，其唯一的不同是
    在add时调用的是CopyOnWriteArrayList的addIfAbsent方法, 
    adIfAbsent方法同样采用锁保护，并创建一个新的大小+1的Object数组。
    遍历当前Object数组，如Object数组中已有了当前元素，则直接返回，如果没有则放入Object数组的尾部，
    并返回。从以上分析可见，CopyOnWriteArraySet在add时每次都要进行数组的遍历，因此其性能会低于CopyOnWriteArrayList.

## 并发无阻塞式队列

### ConcurrentLinkedQueue 

    无阻塞、无锁、高性能、无界、线程安全，性能优于BlockingQueue、不允许null值
    单生产者，单消费者  用 LinkedBlockingqueue
    多生产者，单消费者   用 LinkedBlockingqueue
    单生产者 ，多消费者   用 ConcurrentLinkedQueue
    多生产者 ，多消费者   用 ConcurrentLinkedQueue

## 并发阻塞式队列
### ArrayBlockingQueue

    ArrayBlockingQueue：基于数组实现的阻塞有界队列、
    创建时可指定长度，内部实现维护了一个定长数组用于缓存数据,
    内部没有采用读写分离，写入和读取数据不能同时进行，不允许null值
    
### LinkedBlockingQueue

    基于链表的阻塞队列,内部维护一个链表存储缓存数据，支持写入和读取的并发操作，
    创建时可指定长度也可以不指定，不指定时代表无界队列，不允许null值
### SynchronousQueue
    没有任何容量，必须现有线程先从队列中take,才能向queue中add数据
    否则会抛出队列已满的异常。不能使用peek方法取数据,此方法底层没有实现,会直接返回null
### PriorityBlockingQueue

    一个无界阻塞队列，默认初始化长度11，也可以手动指定，但是队列会自动扩容。
    资源被耗尽时导致OutOfMemoryError。不允许使用null元素。不允许插入不可比较的对象
    （导致抛出ClassCastException）, 加入的对象实现Comparable接口
### DelayQueue
    
    DelayQueue：Delayed 元素的一个无界阻塞队列，只有在延迟期满时才能从中提取元素。
    该队列的头部是延迟期满后保存时间最长的Delayed 元素。如果延迟都还没有期满，则队列没有头部，
    并且poll 将返回null。当一个元素的getDelay(TimeUnit.NANOSECONDS) 方法返回一个小于等于0 的值时
    ，将发生到期。即使无法使用take 或poll 移除未到期的元素，也不会将这些元素作为正常元素对待。
    例如，size 方法同时返回到期和未到期元素的计数。此队列不允许使用null 元素。内部元素需实现Delayed接口
    场景：缓存到期删除、任务超时处理、空闲链接关闭等
 