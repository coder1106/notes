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
