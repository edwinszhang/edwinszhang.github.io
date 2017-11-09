---
title: Maven 项目 tomcat 热部署
date: 2017-11-09 16:12:39
tags: [programming, maven, tomcat]
---

## 非 Maven 项目
对于非 Maven 项目的热部署，假设你的 web resource 根目录是 webapp, 那么你需要作如下设置：
1. 编译 java 源代码到 webapp/WEB-INF/classes 目录下
2. Copy 依赖 jar 包到 webapp/WEB-INF/lib 目录下
3. 在 tomcat 中设置 xml 指向 webapp, 设置如下:
  ```xml
  <Context path="/appName"
    reloadable="true"
    docBase="your\path\to\webapp" >    
  </Context>  
  ```
完成以上设置后，每次更改代码时， tomcat 会自动感知修改并加载，不需要手动部署项目或重启。

## Maven 项目
参考[maven tomcat plugin 实现热部署](https://github.com/junehappylove/june.web.new/wiki/maven-tomcat-plugin%E5%AE%9E%E7%8E%B0%E7%83%AD%E9%83%A8%E7%BD%B2), 这里精简后如下:

1. 在 tomcat 中配置用户权限, 即添加管理员帐号
  修改 conf /tomcat-user.xml 文件
  ```xml
  <role rolename="manager-gui" />  
  <role rolename="manager-script" />  
  <user username="tomcat" password="tomcat" roles="manager-gui, manager-script" />  
  ```
2. 在 maven 中添加 server, 配置 tomcat 的管理员帐号密码
  修改 maven conf/settings.xml 文件, 给你本地的 maven 开启 tomcat 权限
  ```xml
  <server>    
     <id>admin</id>    
     <username>tomcat</username>    
     <password>tomcat</password>    
  </server>
  ```
3. 在 project 中添加插件, 以及 maven 中配置的 deploy 的 server
  设置项目 deploy 配置(TODO: check tomcat version)
  ```xml
  <plugins>  
    <!-- 第一种方式: apache官方tomcat插件,支持deploy -->  
    <plugin>  
        <groupId>org.apache.tomcat.maven</groupId>  
        <artifactId>tomcat7-maven-plugin</artifactId>  
        <version>2.0-SNAPSHOT</version>  
        <configuration>  
            <url>http://localhost:8080/manager/text</url>  
            <server>admin</server>  
        </configuration>  
    </plugin>  
    <!-- 第二种方式: 第三方tomcat插件,支持redeploy -->  
    <plugin>  
        <groupId>org.codehaus.mojo</groupId>  
        <artifactId>tomcat-maven-plugin</artifactId>  
        <version>1.1</version>  
        <configuration>  
            <url>http://localhost:8080/manager/text</url>  
            <server>admin</server>  
            <ignorePackaging>true</ignorePackaging>  
        </configuration>  
    </plugin>  
</plugins>  
  ```
4. 命令行部署

// TODO

## 支持多 Profile (pro|qa|dev)

// TODO
