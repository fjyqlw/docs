# 项目中遇到的问题

## 锁表问题
周六下午，客户反映XXX系统突然某几个页面无法响应数据了，而其他功能又是正常的。经过分析有问题的那些接口，发现都包含了同一个业务表，于是直接把这个业务表放到plsql上去查询发现也查不出来，由此推断应该是锁表了，于是查询所有加锁的表及session，该表确实被锁了。把该表的session结束掉之后系统恢复正常。经过询问开发和测试是否操作过这个表，最终发现是测试在头天晚上下班前应客户要求修改了错误数据，使用for Update后未提交导致锁表问题。

## MQTT服务端订阅错误问题
xx项目中使用阿里云的MQTT服务传输从设备采集的数据，由于公司之前没有使用过MQTT，需要根据需求需要对服务的部署和数据的收发做技术预研。我通过查阅阿里云官方文档，通过代码实现了订阅、发布的demo。当与设备联调的时候，发现设备连接时会把平台的连接踢下线，于是继续查找文档发现是平台订阅方式错误，平台不能以同一设备的方式去订阅，更换了平台专用的服务端订阅接口后问题解决。

## 服务器中勒索病毒

