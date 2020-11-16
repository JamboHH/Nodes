MyBatis

```java
三层框架
	1.界面层（视图层）
		完成和用户的交互，接受请求，显示请求的处理结果
	2.业务逻辑层
		计算数据，处理业务逻辑
	3.数据访问层（持久层）
		数据库操作

框架
	1.界面层：SpringMVC
	2.业务逻辑层：Spring
	3.数据访问层：MyBatis

MyBatis
	作用：增强的jdbc，访问数据库，执行增删查改
	基本步骤
		1.加入maven依赖
			 <dependency>
            	<groupId>org.mybatis</groupId>
            	<artifactId>mybatis</artifactId>
            	<version>3.4.6</version>
  			</dependency>
		2.创建Dao接口：定义了你操作数据的方法
		3.创建mapper文件，也叫做sql映射文件：写sql的语句，和接口中方法对应的sql语句
		4.创建mybatis的一个配置文件：1）连接数据库；2）指定mapper文件的位置
		5.使用mybatis的对象SqlSession，通过他的方法执行sql语句
使用mybatis的动态代理：
		什么是动态代理：mybatis帮你创建Dao接口的实现类，在实现类中他去调用SqlSession的方法执行sql语句
		使用动态代理的方法：
			1.获取SqlSession对象，SqlSessionFactory.openSession()
			2.使用getMapper方法获取某个接口的对象，sqlSession.getMapper(接口.class)
			3.使用dao接口的方法，调用方法就执行了mapper文件的sql语句
使用动态代理方式的要求：
			1.dao接口和mapper文件放在一起，同一个目录
			2.dao接口和mapper文件名称一致
			3.mapper文件中的namespace的值是dao接口的全限定名称
			4.mapper文件中的<select>,<insert>...中的id是接口中的方法名称
			5.dao接口中不要使用重载方法，不要使用同名的不同参数的方法
理解参数
		从java代码中把实际的值传入到mapper中
		1.一个简单类型的参数：#{任意字符}
		2.多个简单类型的参数，使用@Param("自定义名称")
		3.使用一个java对象，对象的属性值作为mapper文件找到参数，#{java对象的属性名称}
		4.使用参数的位置，语法#{arg0}，#{arg0}
		5.使用map作为参数，#{map的key}
#和$的区别：
		1.#是占位符，表示列值的，放在等号右侧
		2.$是占位符，表示字符串的连接的，把sql语句连接成一个字符串
		3.#占位符使用的是jdbc中的PreparedStatement对象执行Sql语句，效率高，没有sql注入的风险
		4.$使用的Statement对象执行Sql，效率低，由sql注入的风险
mybatis返回结构
		resultType
			表示sql语句的执行结果，转为的java对象的类型
				1.类型的全限定名称
				2.别名
					在mybatis中配置文件定义别名
					1.使用<typeAlias>
					2.使用<package name=“报名”>：类名就是别名
		resultMap
			自定义列名和java对象的属性名对应关系
		列名和属性名不一样的解决方式
			1.使用别名
			2。使用resultType
		like
			1.在java代码中指定like的内容
			2.在mapper中拼接like
动态sql
	根据一些条件，能够得到不同的sql语句，使用的是mybatis的标签，例如：if，where，foreach等
		if：判断条件的，条件为true，就会把if之间的sql加入到主sql之后
		where：<where>标签里是多个if，如果有一个if判定为true，会在sql后面加入where关键字，会去掉一些无用的 and，or等字符。
		foreach：循环数组，list集合
			 <foreach collection="" item="" open="" close="" separator="">
    			 #{xxx}
 			</foreach>
		 collction:表示接口中的方法参数的类型，如果是数组使用array，如果是list集合使用list
		 item：自定义的，表示数组和集合成员的变量
		 open：循环开始时的字符
		 close：循环结束时的字符
		 separator：集合成员之间的分隔符
sql的代码片段：复用部分sql语句
			1.先定义<sql id="自定义名称唯一">sql语句，表名，字段名等</sql>
			2.再使用<include refid="id的值">
mybatis主配置文件
		1.数据库属性配置文件的使用
			1）再resoutces目录中定义一个属性配置文件，xxx.properties，例如:db.properties，在属性文件中，定义数据，格式为 key=value
				driver=com.mysql.jdbc.Driver
				url=jdbc:mysql://localhost:3306/lala?characterEncoding=utf8
				username=root
				password=305828
			2）在mybatis得主配置文件，使用<property>指定文件的位置，${key}
		2.mapper文件的位置指定
			1）<mapper resource="mappers/UserMapper.xml"/>
			2）<package name="com.ah.dao"/>
PageHelp分页：
		功能：实现多种数据库的分页，mysql就是代替limit语句的
		使用步骤：
			1.加入maven的依赖
			<dependency>
            	<groupId>com.github.pagehelper</groupId>
            	<artifactId>pagehelper</artifactId>
           		<version>5.1.10</version>
        	</dependency>
			2.再mybatis主配置文件，加入plugin
			<plugins>
        		<plugin interceptor="com.github.pagehelper.PageInterceptor"/>
   			 </plugins>
			3.在查询方法之前，加入PageHelper方法的调用


```

