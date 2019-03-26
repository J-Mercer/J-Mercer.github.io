---
title: application.yml
description: springboot  application.yml
tags:
 - Java
 - springboot
---

```
application.yml
server:
  port: 443
  servlet:
    context-path: /yxzs
  ssl:
    key-store: classpath:yxzs.chxgk.com.jks
    key-store-password: 123qaz
    key-store-type: JKS
    key-alias: yxzs.chxgk.com

spring:
  profiles:
    active: prod
    
  #表示所有的访问都经过静态资源路径
  mvc:
    static-path-pattern: /static/**
    favicon:
      enabled: false
    
  #在这里表示配置静态资源根路径
  resources:
    static-locations: classpath:/static/
    
  thymeleaf:
    cache: false  
    prefix: classpath:/templates/
    suffix: .html
    
  redis:
    host: 111.231.228.27
    port: 6379
    pool:
      #连接池最大连接数
      max-active: 8
      #最大阻塞等待时间，-1表示没有限制
      max-wait: -1
      #最大空闲连接
      max-idle: 8
      #最小空闲连接
      min-idle: 0
      #连接超时时间
      timeout: 0
    password: 123!@#qaz
    
mybatis:
  mapper-locations: classpath:mappers/*.xml
  type-aliases-package: com.chkj.yxzs.domain

qiniu:
  accessKey: oPv1HwYDw__kSVCR_OMwFvLSKX7wMN2gWzg5wPdA
  secretKey: j4euZ_h1wQ-B21sw6rnooM8gswQlLma5GIVzpxfh
  bucket: 360tu
  path: http://qn.chxgk.com
```

```
application-dev.yml
spring:
  datasource:
    name: test
    #使用stater 不需要配置type
    #type: com.alibaba.druid.pool.DruidDataSource
    #druid相关配置
    druid:
      #监控统计拦截的filters
      #filters: stat
      driver-class-name: com.mysql.cj.jdbc.Driver
      #基本属性
      url: jdbc:mysql://localhost:3306/yxzs?serverTimezone=GMT%2B8&useUnicode=true&characterEncoding=UTF-8&zeroDateTimeBehavior=convertToNull&allowMultiQueries=true
      username: root
      password: root
      #配置初始化大小/最小/最大
      initial-size: 1
      min-idle: 1
      max-active: 20
      #获取连接等待超时时间
      max-wait: 60000
      #间隔多久进行一次检测，检测需要关闭的空闲连接
      time-between-eviction-runs-millis: 60000
      #一个连接在池中最小生存的时间
      min-evictable-idle-time-millis: 300000
      #validation-query: SELECT 'x'
      #test-while-idle: true
      #test-on-borrow: false
      #test-on-return: false
      #打开PSCache，并指定每个连接上PSCache的大小。oracle设为true，mysql设为false。分库分表较多推荐设置为false
      #pool-prepared-statements: false
      #max-pool-prepared-statement-per-connection-size: 20
```

