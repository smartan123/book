# Netty性能优化

## 一、netty线程模型

### 1、传统阻塞 I/O 网络模型

### 2、Reactor网络模型

### 3、单Reactor单线程

### 4、单Reactor多线程

### 5、主从Reactor多线程

## 二、netty意外退出及优化

### 1、netty服务端意外退出问题重演

### 2、Java Daemon线程（守护线程）

### 3、netty服务端启动原理

### 4、NioEventLoop线程详解

### 5、Netty的ChannelFuture机制

### 6、如何防止Netty服务意外退出

### 7、实际项目中的优化策略

### 8、kill -9 pid强杀netty进程可能引发的问题

### 9、Java优雅退出机制

### 10、Java优雅退出注意点

### 11、Netty优雅退出机制

### 12、Netty优雅退出原理和源码分析

## 三、netty客户端连接池泄露及优化

### 1、Netty连接池资源泄漏问题重演

### 2、Netty连接池错误代码演示

### 3、Netty客户端运行之后抛出异常详解

### 4、异常原因：错用了NIO编程模式（本质上是BIO模型）

### 5、Netty连接池正确的创建方式代码演示

### 6、修改代码之后的线程模型详解

### 7、Bootstrap工具类的工作原理

### 8、并发安全和资源释放错误代码演示

### 9、java NIO客户端创建原理分析

### 10、Netty客户端创建原理分析

### 11、Bootstrap连接服务器原理

## 四、netty内存池泄露及优化

### Netty内存池泄露故障复现

### Netty内存池泄露错误代码片段详解

### 采集堆内存快照分析

### 问题排查详细过程

### Netty内存释放深层解析（writeAndFlush方法）

### Netty内存释放深层解析（read方法）

### ByteBuf申请和释放场景分析

### Netty内存池的性能压测对比

## 五、ByteBuf故障排查及优化

### HTTP协议栈ByteBuf使用不当问题

### HTTP协议栈ByteBuf正确使用解决方案

### ByteBuf使用注意事项

### java原生ByteBuffer的局限性

### Netty ByteBuf工作原理分析

### ByteBuf引用计数器工作原理和源码分析

## 六、netty发送队列积压及优化

### Netty发送队列积压故障

### Netty高并发故障复现

### Netty高并发故障示例代码

### Netty高并发故障异常信息分析

### 统计GC,老年代已满，发生多次Full GC分析

### CPU被大量GC线程占用分析

### dump内存，mat工具查看泄漏点（NioEventLoop）分析

### 大量WriteAndFlushTask及客户端发送信息积压分析

### WriteAndFlashTask源码分析

### 如何防止队列积压？

### Netty高水位机制原理

### Netty消息积压其他因素

### Netty消息发送机制

### 分析结论

### ChannelOutboundBuffer原理和源码分析

### Netty消息发送原理

## 七、api网关高并发性能波动及优化

### Netty高并发性能波动故障

### Netty高并发故障复现

### 故障示例代码分析

### 故障异常信息分析

### 统计GC,老年代已满，发生多次Full GC分析

### CPU被大量GC线程占用分析

### dump内存，mat工具查看泄漏点（ThreadPoolExecutor）分析

### LinkedBlockingQueue中积压大量的char数组分析

### 故障原因猜测

### 故障根本原因

### 图解故障根本原因

### 故障解决优化方案

### 主动内存泄漏定位法

### 优化建议

## 八、netty Channelhandler并发安全陷阱

### 这样的代码安全吗？

### 串行执行的ChannelHandler

### 测试不同线程执行同一个ChannelHandler

### 跨链路共享ChannelHandler

### 共享ChannelHandler中变量的安全性

### ChannelHandler并发陷阱的场景1

### ChannelHandler并发陷阱的场景2

### 消息在ChannelPipeline中流转的原理图分析

### ChannelPipeline通过链表管理ChannelHandler

## 九、netty ChannelHandler并发失效及优化

### 配置了线程池，但是业务ChannelHandler无法并发执行分析

### 设置客户端以100QPS的速度压测服务端，吞吐量个位数分析

### 原因排查，检查线程数，只有1个defaultEventExecutorGroup线程

### DefaultEventExecutor源码解析

### 为什么无法并行执行？

### 并行执行优化策略1：使用EventExecutorGroup

### 并行执行优化策略2：使用ExecutorService

### 如何选择优化策略：图解优化策略1

### 如何选择优化策略：图解优化策略2

## 十、netty NioEventLoop线程夯住及优化

### 故障复现演示

### 故障排查：cpu，内存等指标都正常

### 故障排查：GC分析，正常

### 故障排查：dump线程，查看线程堆栈信息

### 故障原因分析

### 故障演示

### NioEventLoop线程防夯死策略

### Netty多线程最佳实践

## 十一、netty性能统计误区

### 时延毛刺问题

### 性能统计不一致分析

### 同步思维惹的祸

### writeAndFlush处理流程分析

### 分析writeAndFlush方法，忽略的几个耗时

### 正确的消息发送速度性能统计策略

### 常见的消息发送性能统计误区

### 代码演示Netty关键性能指标采集策略

## 十二、netty事件触发策略使用不当案例

### ChannelHandler调用问题

### 生产环境问题模拟重现

### channelReadComplete方法调用

### ChannelHandler职责链调用

## 十三、netty流量整形案例

### 通用流量整形功能

### netty流量整形功能

### 流量整形示例代码

### 流量整形功能测试

### 流量整形工作原理和源码分析

### 并发编程在流量整形中的应用

### 使用流量整形的一些注意事项