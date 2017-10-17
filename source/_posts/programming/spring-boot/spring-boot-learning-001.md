---
title: [Little book] Spring Boot 手记 001
date: 2017-10-17 22:35:19
tags: [Programming, Spring-boot, little-book]
---

## 官方文档
[Spring boot reference]: (https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)

## 简化代码
使用 Spring boot 的终极目标就是简化繁杂的配置，使开发最简化。所以，我们需要以下几个东西。
- [Lombok]: (https://projectlombok.org/)
- Java 8 语法糖
- Spring Data & Spring Data REST
- RxJava(TODO)
- ...

## 使用参数
1 实现 ApplicationRunner 接口
2 重写run方法，处理参数列表

实例如下：

```java
@Slf4j
@SpringBootApplication
public class Application implements ApplicationRunner{

    public static void  main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @Override
    public void run(ApplicationArguments args) throws Exception {
        log.info("Application started with command-line arguments: {}", Arrays.toString(args.getSourceArgs()));
        log.info("NonOptionArgs: {}", args.getNonOptionArgs());
        log.info("OptionNames: {}", args.getOptionNames());

        for (String name : args.getOptionNames()){
            log.info("arg-" + name + "=" + args.getOptionValues(name));
        }
    }
}
```

## 数据库加密密码
### jasypt-spring-boot
详细请参考: https://github.com/ulisesbocchio/jasypt-spring-boot
1 POM 中引用 jasypt-spring-boot
2 在 application.yml 中配置 config，可以配置从环境变量中读取加密盐
  > jasypt:
    encryptor:
      algorithm: PBEWithMD5AndDES
      password: ${PWD_SALT_ENV} # from environment

3 设置 password: ENC(加密后的密文)

## Profile
1 在 resources 目录下新建 application-${profile}.yml
2 java -Dspring.profiles.active=${profile} -jar yourSpringBootJar.jar
