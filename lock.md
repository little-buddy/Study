# Java 并发引发的锁问题
## 基础知识
### 并发编程的优缺点
- 为什么要用到并发
- 并发编程的优缺点
- 易混淆的概念
### 线程的状态和基本操作
- 如何新建线程
- 线程状态的转换 
- 线程的基本操作
- 守护线程Daemon
## 并发理论
- JMM内存结构
- 重排序 
- happens-before规则

## 并发关键字
### 让你彻底了解 Synchronized
- 如何使用 synchronized
- monitor机制 
- synchronized的happens-before关系
- synchronized的内存语义
- 锁优化
- 锁升级策略
### 彻底了解volatile
- 实现原理
- happens-before的关系推导
- 内存语义
- 内存语义的实现
### 你真的了解final吗？
- 如何使用
- final的重排序规则
- final实现原理
- final引用不能从构造函数中溢出(this逃逸)
### 三大性质总结 原子性、有序性、可见性
- 原子性：synchronized
- 可见性：synchronized，volatile
- 有序性：synchronized，volatile
## lock体系
### 初始lock与AbstractQueuedSynchronizer(AQS)
- Lock 和 synchronized 比较
- AQS设计意图
- 如何使用AQS实现自定义同步组件
- 可重写方法
- AQS提供的模板方法
### 深入理解 AbstractQueuedSychronizer
- AQS 同步队列的数据结构
- 独占式锁
- 共享式锁
### 再一次理解 Reentrantlock
- 重入锁的实现原理
- 公平锁的实现原理
- 非公平锁的实现原理
- 公平所和非公平锁的比较
### 深入理解读写锁ReentrantReadWriteLock
- 如何表示读写状态
- Writelock的获取和释放
- ReadLock的获取和释放
- 锁降级策略
- 生成 condition等待队列
- 应用场景
### 详解Condition的await和signal等待/通知机制
- 与Object的wait/notify机制相比具有的特性
- 与Object的wait/notify相对应的方法
- 底层数据结构
- await 实现原理
- signal/signalAll 实现原理
- await 和 signal/signalAll的结合使用
### LockSupport工具
- 主要功能
- 与synchronized阻塞唤醒相比具有的特色
## 并发容器 不是java开发，这一章还是比较难懂的
### 并发容器之ConcurrentHashMap
- 关键属性
- 重要内部类
- 涉及到的CAS操作
- 构造方法
- put执行流程
- get执行流程
- 扩容机制
- 用于统计size的方法的执行流程
- 1.8 的ConcurrentHashMap与之前版本的比较
### 并发容器之CopyOnWriteArrayList
- 实现原理
- COW 和 ReentrantReadWriteLock的区别
- 应用场景
- 为什么具有弱一致性
- COW的缺点
### 并发容器之ConcurrentLinkedQueue
- 实现原理
- 数据结构
- 核心方法
- HOPS延迟更新的设计意图
### 并发容器之ThreadLocal
- 实现原理
- set方法原理
- get方法原理
- remove方法原理
- ThreadLocalMap
### ThreadLocal内存泄漏问题
- ThreadLocal内存泄漏原理
- ThreadLocal的最佳实践
- 应用场景
### 并发容器之BlockingQueue
- BlockingQueue的基本操作
- 常用的BlockingQueue
## 线程池 Executor体系
### 线程池实现原理
- 为什么要用到线程池
- 执行流程
- 构造各个参数的意义
- 如何关闭线程池
- 如何配置线程池
### 线程池之ScheduledThreadPoolExecutor
- 类结构
- 常用方法
- ScheduledFutureTask
- DelayedWorkQueue
### FutureTask基本操作总结
- FutureTask的集中状态
- get方法
- cancel方法
- 应用场景
- 实现Runable接口

### 原子类操作、并发工具、并发实践 就很JAVA了，对于前端的我来说有点远了

# 次 MD 是对java并发的一次整理，原帖出自 https://github.com/CL0610/Java-concurrency




### 再一次
## 一致性、事务
### 事务ACID特性
### 事务的隔离级别
### MVCC
## 锁
AQS(abstract queue synchronizer)
### Java 中的锁和同步类
### 公平锁 & 非公平锁
### 悲观锁
### 乐观锁 & CAS
### ABA 问题
### CopyOnWrite容器
### RingBuffer
### 可重入锁 & 不可重入锁
### 互斥锁 & 共享锁
### 死锁