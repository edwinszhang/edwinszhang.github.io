---
title: Spring Cloud Stream
tags: [programming, springboot, littlebook, springcloud]
---

![Spring Cloud Stream Application](https://docs.spring.io/spring-cloud-stream/docs/current/reference/htmlsingle/images/SCSt-with-binder.png)
## Keyword

- Message-driven
- Spring Boot
- Spring Integration
- Durability
  + Tips: In general, it is preferable to always specify a consumer group when binding an application to a given destination

## Concepts

### Main Concepts
- Binder
- Sink
- Source
- Processor

### Others
- MessageChannel
- MessageHandler

### Mode

- Publish-Subscribe
  + Publish-subscribe model makes it easy to connect applications through shared topics
![Publish-Subscribe](https://docs.spring.io/spring-cloud-stream/docs/current/reference/htmlsingle/images/SCSt-sensors.png)
- Consumer Groups
  + Scale up by creating multiple instances
![Consumer Groups](https://docs.spring.io/spring-cloud-stream/docs/current/reference/htmlsingle/images/SCSt-groups.png)
- Durability
- Partitioning

## Annotations

- @EnableBinding
- @StreamListener
- @Input
  + Identifies an input channel
- @Output
  + Identifies an output channel
