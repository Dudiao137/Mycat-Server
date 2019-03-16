
mysql 协议分析

MySQL Internals Manual: MySQL Client/Server Protoco

[Mysql协议分析](https://www.cnblogs.com/davygeek/p/5647175.html)

握手认证和命令执行

1、握手认证

服务器 -> 客户端 握手初始化消息;

客户端 -> 服务端 登录认证消息

服务端 -> 客户端 认证结果消息

2、命令执行

客户端 -> 服务器： 执行命令消息

服务端 -> 客户端： 命令执行结果


![MySQL客户端与服务器的完整交互过程](https://img2018.cnblogs.com/blog/710354/201811/710354-20181109114727378-1203542823.png)


请求连接 3次握手

断开连接 4次握手



报文结构：

消息头和消息体两部分： 消息头固定4字节，3个字节用于消息长度，一个字节用于序号，