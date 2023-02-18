# Threadpool
使用c++来实现的线程池项目：
1、解决了不同平台下运行产生的死锁问题，可在windows和linux平台下良好运行。
2、该项目中使用了类似bind表达式和function结合的方式，完成了对lambda函数对象或类对象的状态保存。
3、该项目使用了可变参模板编程，采用了引用折叠原理，能在提交任务时提交任意函数和任意参数。
4、使用future类型来获取submit的返回值，可在不同线程间传输结果，方便结果的获取。
5、使用vector和queue来管理线程对象和提交的线程任务。
6、基于互斥锁mutex和条件变量condition_variable实现任务提交线程和任务执行线程之间的通信机制。
7、线程支持fixed模式和catched模式，可适应不同环境（未完善）。
Notes:最初设计submit返回值时，我自己写了一个返回值Result类、信号量Semaphore类以及能够接收任何数据类型的Any类；
Any通过多态和模板编程实现；
Semaphore通过条件变量condition、互斥锁mutex和计数变量来实现；
Result用Semaphore进行线程间的通信，使用指针在heap上开辟一个Any对象来保存任务的运行结果。
通过上述方法来完成submit返回值的获取。不过后来我发现有更完善的future库，便改用了future。
