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

推荐使用Spring Initializr生成spring boot的maven构建项目

具体做法：

1. 访问[http://start.spring.io](http://start.spring.io)
2. 选择 Maven Project 以及 Spring-boot版本
3. 填写maven项目基本信息
4. 下载初始化源码

如下图

![Spring Initializr初始化项目代码]("\img\in-post\springboot系列(一)-spring-initializr.png")