---
title: "[Little Book] Spring Cloud 手记 001"
date: 2017-11-01 12:54:20
tags: [programming, springboot, littlebook, springcloud]
---
[#IMG - Spring Cloud Projects](http://wx3.sinaimg.cn/mw690/897b1cc3ly1fl2qyqm1hgj20pk0cttco.jpg)
## 官方文档

[Spring Cloud](http://projects.spring.io/spring-cloud/)
[Spring Cloud Projects Reference](http://projects.spring.io/spring-cloud/spring-cloud.html)

## 博客链接
感谢博客园 liumiaocn 的总结，以下是系列原文链接汇总：

1. [Spring Cloud 介绍](http://blog.csdn.net/liumiaocn/article/details/53868315)
1. [服务发现之 eureka](http://blog.csdn.net/liumiaocn/article/details/53886164)
1. [业务逻辑服务](http://blog.csdn.net/liumiaocn/article/details/53922951)
1. [API 网关之 Zuul](http://blog.csdn.net/liumiaocn/article/details/53941354)
1. [断路器之 Hystrix](http://blog.csdn.net/liumiaocn/article/details/54015221)
1. [统一配置管理之 spring cloud config](http://blog.csdn.net/liumiaocn/article/details/54309866)
1. [用 docker 进行 Build/Ship/Run](http://blog.csdn.net/liumiaocn/article/details/54611891)

## 坑
[统一配置管理之 spring cloud config](http://blog.csdn.net/liumiaocn/article/details/54309866) 中的 client 端配置应放在 bootstrap.yml 中，
否则不会生效。详见[bootstrap.yml](https://bitbucket.org/prometheus-imp/spring-cloud-service-user/src/855e47813969185decfa96df70de3ab0b18568d4/src/main/resources/bootstrap.yml?at=master&fileviewer=file-view-default)


## Sample
[Spring Could Samples](https://bitbucket.org/account/user/prometheus-imp/projects/CLOUD)
