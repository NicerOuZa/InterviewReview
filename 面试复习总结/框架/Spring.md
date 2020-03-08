## 1. springboot的优点及实现
## 2. 怎么理解AOP？
## 3. 简述 Spring DI(依赖注入)
- **依赖注入（Dependency Injection，DI）和控制反转含义相同，它们是从两个角度描述的同一个概念**。

- 当某个 Java 实例需要另一个 Java 实例时，传统的方法是由调用者创建被调用者的实例（例如，使用 new 关键字获得被调用者实例），而使用 Spring 框架后，被调用者的实例不再由调用者创建，而是由 Spring 容器创建，这称为控制反转。

- Spring 容器在创建被调用者的实例时，会自动将调用者需要的对象实例注入给调用者，这样，调用者通过 Spring 容器获得被调用者实例，这称为依赖注入。

- 依赖注入主要有两种实现方式，分别是属性 setter 注入和构造方法注入。具体介绍如下。
 + 1）**属性 setter 注入:**
   指 IoC 容器使用 setter 方法注入被依赖的实例。通过调用无参构造器或无参 static 工厂方法实例化 bean 后，调用该 bean 的 setter 方法，即可实现基于 setter 的 DI。
 + 2）**构造方法注入:**
   指 IoC 容器使用构造方法注入被依赖的实例。基于构造器的 DI 通过调用带参数的构造方法实现，每个参数代表一个依赖。
   
## 4. Spring配置元数据
从JDK 1.5开始, Java增加了对元数据(MetaData)的支持，也就是 Annotation(注解)。</br>
Spring IoC容器使用一种形式的配置元数据。此配置元数据表示您作为应用程序开发人员如何告诉Spring容器实例化，配置和组装应用程序中的对象。
**换句话说，就是告诉容器如何去实例化bean**。
- 基于XML的配置元数据的基本结构：
 ```
 <?xml version="1.0" encoding="UTF-8"?>
 <beans xmlns="http://www.springframework.org/schema/beans"
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xsi:schemaLocation="http://www.springframework.org/schema/beans
         https://www.springframework.org/schema/beans/spring-beans.xsd">
 
     <bean id="..." class="...">  
         <!-- collaborators and configuration for this bean go here -->
     </bean>
 
     <bean id="..." class="...">
         <!-- collaborators and configuration for this bean go here -->
     </bean>
 
     <!-- more bean definitions go here -->
 
 </beans>
 ```
- 有关在Spring容器中使用其他形式的元数据的信息，请参见：
  + 基于注释的配置：Spring 2.5引入了对基于注释的配置元数据的支持。
  + 基于Java的配置：从Spring 3.0开始，Spring JavaConfig项目提供的许多功能成为核心Spring Framework的一部分。因此，您可以使用Java而不是XML文件来定义应用程序类外部的bean。要使用这些新功能，请参阅 @Configuration， @Bean， @Import，和@DependsOn注释。

## 5. 循环依赖