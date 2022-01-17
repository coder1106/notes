@JsonSerialize(using=ToStringSerializer.class)
Long型后端传前端导致数据精度丢失

The Hystrix timeout of 10000ms for the command user-oauth-consumer is set lower than the 
combination of the Ribbon read and connect timeout, 42000ms.
AbstractRibbonCommand.java文件
![](https://raw.githubusercontent.com/coder1106/diarynote/master/PicGo/20210817191434.png)
可以看到ribbonTimeout是一个总时间，所以从逻辑上来讲，作者希望hystrixTimeout要大于ribbonTimeout，
否则hystrix熔断了以后，ribbon的重试就都没有意义了。

https://ask.csdn.net/questions/26763
返回的HTTP报文中的Content-Type控制，Content-Type如果为image/jpeg（或其他图片格式）则展示图片，
若application/octet-stream这种或者其他的则是下载

ActiveMQ
https://www.huaweicloud.com/articles/4c9c08dae3b3a390c70fc91c02c36105.html
Web Console监控：
之所以先介绍这个，是因为Web Console是最简单的，不需要任何配置就能使用的监控方式。同时也是最直观的监控方式。
直接在浏览器访问http://activemq-host:8161/admin/。把localhost换成你activemq启动机器的ip，端口号默认是8161，
可以在${ACTIVEMQ_HOME}/conf/jetty.xml中修改。默认的用户名和密码都是admin。
http://172.1.0.4:8161/admin/


https://segmentfault.com/a/1190000021566330

private String getPath() {
String scheme = "http://";
InetAddress localHost = null;
try {
localHost = Inet4Address.getLocalHost();
} catch (UnknownHostException e) {
log.error(e.getMessage(), e);
}
String ip = localHost.getHostAddress();
String port = environment.getProperty("local.server.port");
String contextPath = environment.getProperty("server.servlet.context-path");
String path = String.format("%s%s:%s%s", scheme, ip, port, contextPath);
log.info("订阅访问根路径：{}", path);
return path;
}