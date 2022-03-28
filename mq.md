cd /opt/soft/mq/apache-activemq-5.9.0/bin/linux-x86-64
./activemq start/stop
默认访问端口8161,默认的用户名和密码都是admin。ex:http://172.1.0.4:8161/admin/

ActiveMQ：“通道长时间不活动”异常会阻止代理消息传递
https://www.codenong.com/16320022/

Transport Connection to: tcp://172.17.9.90:59649 failed: org.apache.activemq.transport.InactivityIOException: Channel was inactive for too (>30000) long: tcp://172.17.9.90:59649 | org.apache.activemq.broker.TransportConnection.Transport | ActiveMQ InactivityMonitor Worker
tcp://localhost:61616?wireFormat.maxInactivityDuration=0
补充上这块?wireFormat.maxInactivityDuration=0

清除消息purge
Chrome点击purge可能会报错，后台日志提示：/admin/purgeDestination.action | org.eclipse.jetty.servlet.ServletHandler | qtp1900366749-22095
java.lang.UnsupportedOperationException: Possible CSRF attack
换个浏览器，比如Firefox或者IE等

https://www.jianshu.com/p/31239f2b5651
CLOSE_WAIT表示一个连接被被动关闭了，服务器没有检测到，因此程序忽略了继续进行连接的关闭。最麻烦的是CLOSE_WAIT的连接会占用amq的总连接数，因此如果要清理，只能重启mq来解决。
有一篇文章对TIME_WAIT和CLOSE_WAIT解释得很详细。
http://www.cnblogs.com/sunxucool/p/3449068.html
出现这个问题后，可能直接导致activemq报出timer already cancelled，连接超限，无法建立线程OOM等报错。（推测）
该问题在JIRA上已经被关闭，见AMQ-5543和AMQ-5251。

经过一段时间的研究，发现是我的代码触发了MQ 的一个bug代码中建立了过多的JMX连接，导致服务器无法建立新的线程，从而导致连接无法被正常处理，而后连接被客户端关闭，就出现了close_wait。

这个bug连接的是InactivityMonitor中建立ReadChecker和WriteCheck的bug，出现问题时会导致MQ上报出大量的Timer Already Cancelled报错，因为无法建立新的checker线程了，但是代码中仍然进行了checker的Timer类的配置，所以抛出了timer already cancelled的异常。在AMQ 5.13及以后的版本已修复该问题。