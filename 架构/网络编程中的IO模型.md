# BIO 同步阻塞IO

recvfrom系统调用，线程挂起；当数据包到达时唤醒线程，线程将数据从内核复制到用户空间

# NIO 1.0 同步非阻塞IO

select/poll/epoll系统调用，线程挂起；当数据包到达时唤醒线程，线程通过reccvfrom系统调用将数据从内核复制到用户空间。区别是，只需要一个线程可以监视多个读或写操作。

JDK4开始提供（ServerSocketChannel、SocketChannel）

## select 

轮询扫描FD数组查找是否有就绪的FD。一个线程能监听的端口有限，32位机默认是1024个。64位机默认是2048。

## poll

poll本质上和select没有区别，FD数组是链表，无数量限制。

## epoll

epoll是Linux内核为处理大批量FD而作了改进的poll，无需遍历FD，只需遍历Ready队列。使用mmap加速内核与用户空间的消息传递。

# NIO 2.0 异步IO

aio_read系统调用，系统在数据包到达时，将数据从内核复制到用户空间后，通知调用者。

Windows上可以使用iocp了，Linux2.6支持但是不够完善，性能和epoll差不多。

JDK7开始提供（AsynchronousServerSocketChannel、AsynchronousSocketChannel、CompletionHandler）