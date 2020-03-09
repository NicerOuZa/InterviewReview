## 1. springboot的优点及实现
## 2. 怎么理解AOP？
1. Spring的关键组件之一是AOP框架。虽然Spring IoC容器不依赖于AOP（这意味着您不需要使用AOP），但AOP是对Spring IoC的补充，以提供功能非常强大的中间件解决方案。
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
## 6. 注释
1. 从Spring Framework 4.3开始，@Autowired如果目标bean仅定义一个构造函数作为开始，则不再需要在此类构造函数上添加注释。但是，如果有多个构造函数可用，则必须至少注释一个构造函数，@Autowired以指示容器使用哪个构造函数。
2. 还可以将注释应用于具有任意名称和多个参数的方法。
3. **下面为常见注释：**
- 通过@Value将外部的值动态注入到Bean中，使用的情况有：
  + 注入普通字符串
  + 注入操作系统属性
  + 注入表达式结果
  + 注入其他Bean属性：注入beanInject对象的属性another
  + 注入文件资源
  + 注入URL资源
- **@Repository注释**是针对满足的存储库（也被称为数据访问对象或DAO）的作用或者固定型的任何类的标记。如Exception Translation中所述，此标记的用途是自动翻译 异常。

## 7. @Resource和@Autowired的区别
1. @Autowired与@Resource都可以用来装配bean. 都可以写在字段上,或写在setter方法上。两者如果都写在字段上，那么就不需要再写setter方法。
2. @Autowired默认按类型装配（这个注解是属业spring的），默认情况下必须要求依赖对象必须存在，如果要允许null值，可以设置它的required属性为false，如：@Autowired(required=false) ，如果我们想使用名称装配可以结合@Qualifier注解进行使用，如下：
```
@Autowired()
@Qualifier("baseDao")
private BaseDao baseDao;
```
3. @Resource（这个注解属于J2EE的），默认按照名称进行装配，名称可以通过name属性进行指定，如果没有指定name属性，当注解写在字段上时，默认取字段名进行安装名称查找，如果注解写在setter方法上默认取属性名进行装配。当找不到与名称匹配的bean时才按照类型进行装配。但是需要注意的是，如果name属性一旦指定，就只会按照名称进行装配。
```
@Resource(name="baseDao")
privateBaseDao baseDao;
```
4. 推荐使用：@Resource注解在字段上，这样就不用写setter方法了，并且这个注解是属于J2EE的，减少了与spring的耦合。这样代码看起就比较优雅。
5. **简单的说：</br>@Autowired默认按type注入</br>@Qualifier("xxx")//一般作为@Autowired()的修饰用</br>@Resource(name="xxx")//默认按name注入，可以通过name和type属性进行选择性注入**