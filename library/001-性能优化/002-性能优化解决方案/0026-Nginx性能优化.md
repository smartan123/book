# Nginx性能优化 [ [配套教程](https://coding.imooc.com/class/442.html) ]

## 一、为什么是nginx而不是apache？

### 1、轻量级：同样起web 服务，比apache 占用更少的内存及资源

### 2、静态处理：Nginx 静态处理性能比 Apache 高 3倍以上

### 3、抗并发：nginx 处理请求是异步非阻塞的，而apache则是阻塞型的，在高并发下nginx 能保持低资源低消耗高性能

### 4、高度模块化的设计，编写模块相对简单

### 5、社区活跃，各种高性能模块出品迅速

## 二、Nginx是如何做到高性能和高可扩展的？

### 1、事件驱动架构

### 2、一个主进程和若干worker进程和helper进程

### 3、每个worker进程以非阻塞的方式处理多个连接，这减少了上下文切换的次数

### 4、状态机的调度

## 三、Nginx运行工作进程数量优化

### 如何查看工作进程数？

### 调整worker进程数=CPU的核心或者核心数x2

### 调整后检查进程:ps -aux | grep nginx |grep -v grep

## 四、Nginx运行CPU亲和力优化

### 为什么要绑定 Nginx 进程到不同的CPU上？

### 如何分配不同的Nginx进程给不同的CPU处理？

### 配置案例演示

## 五、Nginx最大打开文件数优化

### nginx报错打开文件数过多，原因是什么？

### 配置案例演示

## 六、Nginx事件处理模型

### 不同的操作系统会采用不同的 I/O 模型

### 常见的事件处理模型举例

### linux下指定最佳事件处理模型

## 七、开启高效传输模式

### nginx中的“零拷贝”

### sendfile 参数详解

### tcp_nopush 参数详解

### 开启sendfile的注意点（默认是开启的）

## 八、连接超时时间优化

### 什么是连接超时

### 连接超时的作用

### 连接超时存在的问题

### 设置连接超时

## 九、fastcgi调优

### 什么是CGI？

### 为什么选择FastCGI？

### FastCGI的各大配置项详解

## 十、gzip调优

### Gzip压缩作用

### 详解Gzip具体配置

## 十一、expires缓存调优

### expires优点

### expires缺点

### expires具体配置

## 十二、防盗链

### 防盗链3种解决办法

### 设置防盗链的两种配置方案详解

### 相关参数解释

## 十三、内核参数优化

### 详解fs.file-max

### 详解net.ipv4.tcp_max_tw_buckets

### 详解net.ipv4.tcp_tw_recycle

### ......

## 十四、关于系统连接数的优化

### 详解worker_connections

### worker_connections生效机制

## 未完，待续。。。