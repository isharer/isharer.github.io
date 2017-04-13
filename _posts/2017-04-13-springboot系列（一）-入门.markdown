---
layout:     post
title:      "SpringBoot系列（一）"
subtitle:   " \"SpringBoot系列 快速入门\""
date:       2017-04-13 12:00:00
author:     "Zhk"
header-img: "img/post-bg-2017.jpg"
catalog: true
tags:
    - Spring Boot
---

## SpringBoot系列 入门##

### 序言 ###

SpringBoot一直是一个非常火的软件，公司好些项目中也使用到了，最近刚好在做项目阶段总结，所以，在这里进行一个Springboot的一个技术使用总结回顾，也顺便系统化学习一下SpringBoot。

### 简要介绍 ###

Springboot作为一个升级版的Spring，它很容易创建一个独立运行的（以jar与运行，内嵌Servelet服务器），可以达到准生产级别的基于Spring框架的项目。相比Spring来讲少了大量的xml配置文件，它自身内置了许多习惯性的配置，无需手动添加配置。

### 核心优势 ###

- 创建独立的Spring应用程序
- 嵌入式Tomcat、jetty容器，无需部署war包
- 简化meven配置
- 自动化配置Spring
- 内置Starter POM 最大化简化项目构建配置

### 系统要求 ###

目前Spring1.5版本，需要spring Framwork 4.3.6以上版本 及jdk8，虽然你也可以使用jdk6，7 但我们推荐使用jdk8

IDE使用Intellij Idea

### 快速入门 ###

首先，我们对比一下传统Spring实现一个Hello word简单web应用需要做的事情

- 你必须现有一个SpringMVC 和 Servelet API 依赖
- 然后得有Spring MVC 的xml配置
- 一个web.xml
- 一个Helloword控制器
- 一个用于部署的web服务器，如tomcat

上面这一大堆的事情，与我们做的事情有关的仅仅就一个Helloword控制器，其他的都是spring应用所需的通用配置

但是使用Springboot就能通过很少的配置搭建一个web项目

### 初始化一个Spring boot项目 ###

具体可以使用两种方式初始化spring boot项目， web端生成和使用Spring Initilizr。推荐使用Spring Initializr生成spring boot的maven构建项目


- web端生成


具体做法：

1. 访问[http://start.spring.io](http://start.spring.io)
2. 选择 Maven Project 以及 Spring-boot版本
3. 填写maven项目基本信息
4. 下载初始化源码

如下图

![Spring Initializr初始化项目代码](\img\in-post\springboot系列(一)-spring-initializr.png)

- 使用Spring Initializr

	1. 打开Intellij idea
	2. 选择new project->选择Spring Initializr
	3. 然后在右侧选择jdk版本，初始化url选择默认，然后下一步
	4. 填写项目的基本信息，然后下一步
	5. 选择项目模块依赖，我们选择web-web，然后下一步完成

### 项目结构 ###

	│  .gitignore
	│  mvnw
	│  mvnw.cmd
	│  pom.xml
	│  spring-boot-init.iml
	│
	└─src
	    ├─main
	    │  ├─java
	    │  │  └─com
	    │  │      └─nptever
	    │  │          └─zhk
	    │  │                  SpringBootInitApplication.java
	    │  │
	    │  └─resources
	    │      │  application.properties
	    │      │
	    │      ├─static
	    │      └─templates
	    └─test
	        └─java
	            └─com
	                └─nptever
	                    └─zhk
                            SpringBootInitApplicationTests.java

主要文件说明

- pom.xml Maven构建说明文档
- SpringBootInitApplication.java 带main()方法的一个springboot的启动类，很重要
- SpringBootInitApplicationTests.java 一个空的Junit测试类
- application.properties 空的属性配置文件

### Pom文件说明 ###

pom文件展示如下

	<?xml version="1.0" encoding="UTF-8"?>
	<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
		<modelVersion>4.0.0</modelVersion>
	
		<groupId>com.nptever.zhk</groupId>
		<artifactId>spring-boot-init</artifactId>
		<version>0.0.1-SNAPSHOT</version>
		<packaging>jar</packaging>
	
		<name>spring-boot-init</name>
		<description>Initalizr Demo project for Spring Boot</description>
	
		<parent>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-parent</artifactId>
			<version>1.5.2.RELEASE</version>
			<relativePath/> <!-- lookup parent from repository -->
		</parent>
	
		<properties>
			<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
			<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
			<java.version>1.8</java.version>
		</properties>
	
		<dependencies>
			<dependency>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-starter-web</artifactId>
			</dependency>
	
			<dependency>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-starter-test</artifactId>
				<scope>test</scope>
			</dependency>
		</dependencies>
	
		<build>
			<plugins>
				<plugin>
					<groupId>org.springframework.boot</groupId>
					<artifactId>spring-boot-maven-plugin</artifactId>
				</plugin>
			</plugins>
		</build>
	
	
	</project>

**springboot中的父级依赖**

	<parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.2.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

这块的配置是springboot的父级依赖，有了这个项目就是Spring Boot项目，spring-boot-starter-parent是一个特殊的starter用来提供maven的默认依赖。有了它，常用的包依赖可以省略version版本标签。

可以在\..\repository\org\springframework\boot\spring-boot-dependencies\1.5.1.RELEASE\spring-boot-dependencies-1.5.1.RELEASE.pom文件中看到Springboot的jar包依赖。

部分spring-boot-dependencies-1.5.1.RELEASE.pom内容如下

	<properties>
		<!-- Dependency versions -->
		<activemq.version>5.14.3</activemq.version>
		<antlr2.version>2.7.7</antlr2.version>
		<appengine-sdk.version>1.9.49</appengine-sdk.version>
		<artemis.version>1.5.3</artemis.version>
		<aspectj.version>1.8.9</aspectj.version>
		<assertj.version>2.6.0</assertj.version>
		<atomikos.version>3.9.3</atomikos.version>
		<bitronix.version>2.1.4</bitronix.version>
		<caffeine.version>2.3.5</caffeine.version>
		<cassandra-driver.version>3.1.4</cassandra-driver.version>
		<classmate.version>1.3.3</classmate.version>
		...
	</properties>

如果你不想使用默认的依赖版本，可以在properties配置中进行覆盖，比如，我修改使用tomcat8.5.11版本就可以这样

	<properties>
		<tomcat.version>8.5.11</tomcat.version>
	</properties>

当你不想使用继承自spring-boot-starter-parent的pom，或者你希望显式声明所有maven依赖配置，你可以通过scope = import 依赖关系来保持依赖管理如下

	<dependencyManagement>
	     <dependencies>
	        <dependency>
	            <!-- Import dependency management from Spring Boot -->
	            <groupId>org.springframework.boot</groupId>
	            <artifactId>spring-boot-dependencies</artifactId>
	            <version>1.5.1.RELEASE</version>
	            <type>pom</type>
	            <scope>import</scope>
	        </dependency>
	    </dependencies>
	</dependencyManagement>

该实现不允许使用上面的properties进行依赖覆盖，但是你可以通过在dependencyMannagement中添加依赖配置scope=import type=pom完成

	<dependencyManagement>
	    <dependencies>
	        <!-- Override Spring Data release train provided by Spring Boot -->
			<dependency>
				<groupId>org.apache</groupId>
				<artifactId>tomcat-embed-core</artifactId>
				<version>8.5.11</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
	        <dependency>
	            <groupId>org.springframework.boot</groupId>
	            <artifactId>spring-boot-dependencies</artifactId>
	            <version>1.5.1.RELEASE</version>
	            <type>pom</type>
	            <scope>import</scope>
	        </dependency>
	    </dependencies>
	</dependencyManagement>


**起步依赖 spring-boot-start-xxx**

Spring boot提供了一些“开箱即用的”依赖模块，都是以srping-boot-start-xxx命名。就是说，spring boot已经封装好了一些功能实现依赖，不需要自己再组织依赖，这样做的好处不仅免实现而且可靠。比如，我们要实现web功能，就只需要引入 spring-boot-starter-web这个起步依赖就可以了。

我们可以看下这个起步依赖到底依赖了哪些东西：

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-tomcat</artifactId>
		</dependency>
		<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-validator</artifactId>
		</dependency>
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-databind</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
		</dependency>
	</dependencies>

可以看到这些依赖要让我们自己来维护管理的话，那将会相当麻烦，而且很有可能会出现各种依赖问题。所以spring boot使用起步依赖降低依赖的复杂度，其实它本质上就是一个maven项目对象模型POM，定义了对其他库的传递依赖，这些依赖加在一起支持某项功能。很多情况下我们都可以根据起步依赖的名字来知道它所支持的功能。

**Spring boot maven插件**

	<plugin>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-maven-plugin</artifactId>
	</plugin>

通过spring boot的maven插件，我们可以很方便的做一些事情

- 讲项目打包成一个可执行jar包，包括打入依赖，并添加描述文件，描述文件内容允许你使用 java jar 运行你的项目

