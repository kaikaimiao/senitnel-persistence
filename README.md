#sentinel 持久化nacos 版本
##1. 打包运行 server端

##2. springboot客户端增加配置
```
spring:
  cloud:
    sentinel:
      transport:
        dashboard: 127.0.0.1:8858
        port: 6666
      datasource:
        ds:
          nacos:
            server-addr: 192.168.10.51:8848
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-flow-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: flow
        ds1:
          nacos:
            server-addr: 192.168.10.51:8848
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-degrade-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: degrade
        ds2:
          nacos:
            server-addr: 192.168.10.51:8848
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-authority-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: authority
        ds3:
          nacos:
            server-addr: 192.168.10.51:8848
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-system-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: system
      eager: true
```

