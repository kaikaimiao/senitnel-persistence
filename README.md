##                                                        sentinel 持久化nacos 版本
### 1. 下载源码   打包运行 sentinel-dashboard 模块 
### 2. 客户端引入maven依赖
```
        <dependency>
            <groupId>com.alibaba.csp</groupId>
            <artifactId>sentinel-datasource-nacos</artifactId>
        </dependency>
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
        </dependency>
```        
### 3. 在springboot bootstrap.yaml增加配置
```
spring:
  cloud:
    sentinel:
      transport:
        dashboard: ${sentinel.host}
        port: 通信sentinel会占用一个本地端口
      datasource:
        ds:
          nacos:
            server-addr: @nacos-server@
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-flow-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: flow
        ds1:
          nacos:
            server-addr: @nacos-server@
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-degrade-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: degrade
        ds2:
          nacos:
            server-addr: @nacos-server@
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-authority-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: authority
        ds3:
          nacos:
            server-addr: @nacos-server@
            namespace: @nacos-namespace@
            data-id: ${spring.application.name}-system-rules
            group-id: SENTINEL_GROUP
            data-type: json
            rule-type: system
      eager: true
```

