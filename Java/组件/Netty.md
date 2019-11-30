# Reactor线程模型

Netty通过配置EventLoopGroup可以支持以下Reactor线程模型。主从Reactor多线程模型性能更好，bossEventLoopGroup负责Accept连接，workEventLoopGroup负责读写事件处理。

* 单 Reactor 单线程
* 单 Reactor 多线程
* 主从 Reactor 多线程

# 责任链模式ChannelPipeline、ChannelHandler

# 集成多种消息/协议编解码框架，解决半包粘包问题

# 支持IP 黑白名单控制

# ByteBuf减少内存拷贝、减少内存分配及回收

* PoolHeapByteBuf、UnpoolHeapByteBuf、PoolDirectByteBuf、UnpoolDirectByteBuf
* 读写IO使用直接内存，减少内存拷贝到堆的情况，性能更好
* 消息编解码过程使用堆内存，性能更好
* CompositeByteBuf，减少数据组包的拷贝

# Netty版本

最新稳定版4.1.x，Netty5基于AIO实现，只出了预览版，实测性能相比NIO提高不大




