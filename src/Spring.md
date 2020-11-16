### Spring

```
框架：是一个其他人写好的软件。
	1）需要知道框架可以用来做什么，mybatis--访问数据库，对表中的数据执行增删改查。
	2）框架的语法，框架要完成一个功能，需要一定的步骤支持。
	3）框架的内部实现，框架的内部怎么实现的。 原理是什么？
	4）通过学习，做一个自定义框架。
```

**Spring的第一个核心功能IoC**

```
IoC(Inversion of Control):控制反转，是一个理论，概念，是一个想法。
	它描述的时把对象的创建，赋值，管理工作都交给代码之外的容器来实现，也就是说对象的创建是由其他外部资源来完成的。
	控制：创建对象，对象的属性赋值，对象之间的关系管理。
	反转：把原来的开发人员管理，创建对象的权限转移给代码之外的容器实现，由容器代替开发人员管理对象创建对象，给属性赋值。
	正转：有开发人员在代码中，使用new构造方法创建对象，开发人员主动管理对象。
	容器：是一个服务软件，一个框架（spring）
为什么要用ioc：
	目的就是减少对代码的改动，也能实现不同的共能。实现解耦合。
java中创建对象有哪些方式？
	1.构造发方法，new Student（）
	2.反射
	3.序列化
	4.克隆
	5.ioc：容器创建对象
	6.动态代理
ioc的体现：
	servlet  1：创建类继承HttpServlet 
	         2：在web.xml 注册servlet，使用<servelt-name>myServlet</servlet-name>
	         							<servlet-class>com.ah.comtroller.MyServlet</servlet-class>
	         3:没由创建过Servlet对象，但可以使用，因为由Tomcat创建了Servlet对象，Tomcat作为容器：里面存放的由Servlet对				 象，Listener，Filter对象
IoC的技术实现：
	DI 是ioc的技术实现
	DI（Dependency Injection） ：依赖注入，只需要在程序中使用对象的名称就可以，至于对象如何在容器中创建，赋值，查找都由容器内部实现。
	
Spring时使用DI实现了ioc的功能，spring底层创建对象使用的反射机制。
```

基于注解的di：通过注解完成java对象的创建，属性赋值

```
使用注解步骤：
	1.加入maven的依赖 spring-contenxt，在你加入spring-context的同时间接加入spring-aop的依赖，使用注解必须使用spring-aop的依赖
	2.在类中加入spring的注解（多个不同功能的注解）
	3.在spring的配置文件中，加入一个组件扫描器的标签，说明注解在你的项目中的位置
学习的注解：
	1.@Compoent
    2.@Respotory
    3.@Service
    4.@Controller
    5.@Value
    6.@Autwoired
    7.@Resource
```

aop

```
***1.动态代理
实现方式：jdk动态代理，使用jdk中的Proxy，Method，InvocationHandler创建代理对象。
		jdk动态代理要求目标类必须实现接口。
cglib动态代理：第三方工具库，创建代理对象，原里是继承。通过继承目标类，创建子类。子类就是代理对象，要求子类不能是final的，方法也不能是fianl的
***2.动态代理的作用***
	1）可以在目标类源代码不改动的情况下增加功能
	2）减少代码的重复
	3）专注业务逻辑代码
	4）解耦合，让你的业务功能和日志，事务非事务功能分高。
3.Aop：面向切面编程，基于动态代理的，可以使用jdk，cglib两种代理方式。
	aop就是动态代理的规范化，把动态代理的实现步骤，方式都定义好了。让开发人员用一种统一的方式，就用动态代理。
4.Aop（Aspect Orient Programming）面向切面编程
	Aspect：切面，给你的目标类增加的功能，就是切面。像日志和事务等。。。
		    切莫的特点：独立使用，一般都是非业务方法。
	Orient：面向:对着。
	Programming：编程。
	oop：面向对象编程
***如何理解面向切面编程？
	1）需要在分析项目功能时，找出切面
	2）合理的安排切面的执行时间（在目标方法前还是目标方法后）
	3）合理的安排切面执行的位置，在哪个类，那个方法增加增强功能
	术语：
	1）Aspect：切面，表示增强功能，就是一堆代码，完成某一个个功能，非业务功能。
		常见的切面功能有日志，事务，统计信息，参数检查，权限验证。
	2）JoinPoint：连接点，连接业务方法和切面的位置。就是某个类中的业务方法
	3）Pointcut：切入点，指多个连接点方法的集合，
	4）目标对象：给哪个类的方法增加功能，这个类就是目标对象
	5)Advice：通知，通知表示切面功能执行的时间。
切面的三个关键要素：
	1）切面的功能代码，切面干什么
    2）切面的执行位置，使用Pointcut表示切面执行的位置
    3）切面的执行时间，使用Advice来表示时间，在目标方法之前还是之后
5.aop的实现
	aop是一个规范，是动态的一个规范化，一个标准
	aop的技术实现框架：
	1.spring：spring在内部实现了aop规范，能够做aop的工作
			spring主要在事务处理使用aop。
			我们项目开发中很少用spring的aop实现，因为spring的aop比较笨重。
	2.aspectJ：一个开源的专门做aop的框架。spring框架中继承了aspectJ框架，通过spring就可使用aspectJ的功能。
	aspectJ框架实现有两种方法:
	1.使用xml配置文件：配置全局事务
	2.使用注解，我们在项目中要做aop功能一般都是用注解，aspect主要有5个注解：
6.学习aspectJ的使用语法：
	1）切面的执行时间，这个执行时间在规范中它叫做Advice（通知，增强）
		在aspectJ框架中使用注解表示的。
		1）@Before
		2）@AfterReturning
		3）@AroundA
		4）@AfterThrowing
		5）@After
	2）表示切面执行的位置，使用的是切入点表达式
		com.service.impl
		com.ah.service.impl
		com.crm.ah.service
		execution(* *..service.*.*(..))
```











