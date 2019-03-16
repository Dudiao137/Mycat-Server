NIO
1.org.opencloudb.net.NIOProcessor  检查前端连接 检查后端连接 连接清理
2.org.opencloudb.net.NIOReactorPool NIOReactor线程池 存放reactor线程 初始化并启动
3.org.opencloudb.net.NIOReactor 处理读写请求
3.org.opencloudb.net.NIOConnector.NIOConnector 存放NIOReactor线程池  对应前端的一个连接或者后端连接(连接成功交给ractor线程处理)
org.opencloudb.net.factory.FrontendConnectionFactory
org.opencloudb.net.factory.BackendConnectionFactory
org.opencloudb.manager.ManagerConnectionFactory
org.opencloudb.server.ServerConnectionFactory
org.opencloudb.mysql.nio.MySQLConnectionFactory
生成对应的前端连接 和后端连接和管理连接
org.opencloudb.mysql.nio.MySQLConnection
org.opencloudb.server.ServerConnection
org.opencloudb.manager.ManagerConnection
4.org.opencloudb.net.NIOAcceptor.NIOAcceptor  分成管理端(9066)和服务端(8066) 接受前端连接
5.初始化数据源org.opencloudb.backend.PhysicalDBPool datahost database.xml 文件
org.opencloudb.backend.PhysicalDBPool 里面进行初始化后端连接initSource方法每个数据源都初始化一个连接保证最小连接数
初始化一个connection(org.opencloudb.mysql.nio.MySQLConnectionFactory)

定时任务
1.系统时间定时更新任务 
2.处理器定时检查任务
3.数据节点定时连接空闲超时检查任务
4.数据节点定时心跳任务
5.catletClassClear


handle
org.opencloudb.mysql.nio.MySQLConnectionAuthenticator 验证处理器
org.opencloudb.net.handler.FrontendAuthenticator 前端验证处理
org.opencloudb.net.handler.FrontendCommandHandler 前端命令处理
org.opencloudb.mysql.nio.MySQLConnectionHandler 认证之后操作
org.opencloudb.server.ServerQueryHandler

查询的方法
org.opencloudb.server.handler.SelectHandler
到ServerConnection的execute 方法  -> routeEndExecuteSQL (选择路由并执行sql )
单节点 org.opencloudb.mysql.nio.handler.SingleNodeHandler
多节点和全区表
org.opencloudb.mysql.nio.handler.GlobalTableMultiNodeQueryHandler
org.opencloudb.mysql.nio.handler.MultiNodeQueryHandler


文件
database.xml 
user.xml     mycat用户前端
server.xml  mycat服务端的一些配置
schema.xml  mycat的表的配置
rule.xml    分片规则
router.xml  路由规则

--------------------- 
作者：K-Darker 
来源：CSDN 
原文：https://blog.csdn.net/zhouhao88410234/article/details/78065504 
版权声明：本文为博主原创文章，转载请附上博文链接！


线程模型：

https://blog.csdn.net/u011983531/article/details/78964350

https://blog.csdn.net/d6619309/article/details/52330133


使用示例 1:

https://blog.csdn.net/qq_28804275/article/details/80892095
