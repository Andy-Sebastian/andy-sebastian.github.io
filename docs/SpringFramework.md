# SpringFramework

## Spring核心概念

1. 依赖注入（DI）：这是Spring框架的核心功能，它消除了硬编码的依赖关系，使得代码更加灵活，易于测试和维护

2. 面向切面编程（AOP）：Spring支持面向切面编程，允许定义方法拦截器和切点，以将代码逻辑解耦，提高代码的可重用性和可维护性。

3. Spring MVC：Spring的Web MVC框架是一种分离式的框架，设计目标是通过分离模型（Model）、视图（View）和控制器（Controller）来使Web应用更易于开发和维护。

4. 事务管理：Spring提供了一种抽象的事务管理接口，可以与Java的事务处理模型集成，简化了事务管理的复杂性。

5. Spring Boot：这是Spring的一个模块，它提供了一种快速开发新Spring应用的方式，无需进行复杂的配置。

6. Spring Cloud：为开发者提供了一系列的工具，帮助开发者快速构建一些常见的模式在分布式系统（例如：配置管理，服务发现，断路器，智能路由，微代理，控制总线，一次性令牌，全局锁，领导选举，分布式会话，集群状态）。

## Spring启动流程

1. 初始化Spring应用上下文：Spring应用启动的第一步是创建并初始化Spring应用上下文（ApplicationContext）。Spring应用上下文是Spring应用的核心，它负责管理Spring应用中的所有对象（Bean）。

2. 加载配置文件：Spring应用上下文在初始化时会加载Spring的配置文件，这些配置文件定义了Spring应用中的所有Bean以及它们之间的依赖关系。

3. 创建Bean：根据配置文件中的定义，Spring应用上下文会创建并初始化所有的Bean。在这个过程中，Spring会自动处理Bean之间的依赖关系，例如，如果Bean A依赖于Bean B，那么在创建Bean A之前，Spring会先创建Bean B。

4. 依赖注入：在创建Bean的过程中，Spring会自动将Bean的依赖注入到Bean中。这是通过Spring的依赖注入（DI）机制实现的。

5. 启动完成：当所有的Bean都被创建并初始化完成后，Spring应用就启动完成了。此时，你可以通过Spring应用上下文获取任何你需要的Bean，并使用这些Bean进行业务逻辑的处理。

## Bean生命周期

## 推断构造方法

## 依赖注入

## @PostConstruct

## 初始化前

## 初始化

## 初始化后

## AOP

## Spring事务

## @Configuration

## 循环依赖

## 三级缓存