

### JSTL标准标签库

> **循环：**
>
> ```
> <c:forEach items="集合" var="">
> 
> </c:forEach>
> <c:forEach begin="起始值" step="步长值" end="结束值" var="变量">
> 	${变量}
> </c:forEach>
> 
> ```
>
> **判断**
>
> ```
> 单分支：
> 	<c:if test="表达式">
> 	
> 	</c:if>
> 多分支：
> 	<c:choose>
> 		<c:when test="表达式">
> 		</c:when>
> 		<c:when test="表达式">
> 		</c:when>
> 		<c:otherwise>
> 		</c:otherwise>
> 	</c:choose>
> ```
>
>

### javascript

> javascript 网页技术，实现(与用户交互、动态特效、校验)
>
> 语法：
>
> ​	变量：用var声明，可以接收不同的数据类型；变量没有类型，根据赋值决定变量的类型；
>
> ​	类据类型：
> ​		基本类型：number  string  boolean  undefined  null  NaN(非数值not a number)
> ​		引用类型：{属性名 ：值，属性名：值，。。。}
> ​		数组类型：[元素, 元素,  元素, ..... ]
>
> ​	输出语句：
> ​		document.write(内容)
> ​		弹框：
> ​			alert(内容);
> ​			confirm(内容)
> ​			prompt(内容);
> ​		控制台输出：console.log(内容)
>
> ​	for循环：
>
> ```
> 
> ```
>
> ​	DOM模型：
>
> ```
> 把所有标签列为一个dom模型，使用节点之间的包含与被包含关系形成一个模型；
> 父节点：包含其它节点； 例：<div><a></a></div>
> 子节点：被其它节点包含的节点：  例：<div><a></a></div>
> 兄弟节点：有同一个父节点的节点；例：<div><a></a><img></div>
> 
> 获得对象： document.getElementById(id名称);
> 修改对象的内容：对象名.innerHTML
> 修改属性：
> 	<img src="" width="" />   对象名.src=""
> 	<div></div>   对象名.style.属性名  
> 					border-color  对象名.style.borderColor
>                     color   对象名.style.color
> ```
>
> 函数：
>
> ```
> 定义：
> 	function 函数名(参数列表){
>         //JS
> 	}
> 调用：
> 	直接调用；---意义不大
> 	结合事件调用；---常用
> 	定时器中调用；
> ```
>
> 事件：
>
> ```
> 
> ```
>
> 正则表达式：用来验证字符串格式
>
> ```
> 格式定义：var reg=/^规则$/
> 	^ 代表字符的开始；
> 	$ 代表字符的结束；
> 	定义规则：
> 		\w :代表一个任意数字、字母、下划线
> 		\d：代表任一个数字
> 		{m,n}：左边元字符的重复次数，至少m次，至多n次；
> 		{m,}：左边元字符的重复次数，至少m次
> 		{m}：左边元字符的重复m次；
> 获得被验证对象：
> 	获得表单的元素：value属性，代表表单元素的值；
> 	获得双标签的内容：innerHTML属性
> 验证：
> 	调用 test()方法：如果格式验证正确，则返回true；否则返回false;
> 		reg.test(被验证对象.value);
> 		reg.test(被验证对象.innerHTML);
> ```
>
>

### 作业

> 1. 表单中的正则验证；(注册表单、登录表单、修改数据的表单) bingo
> 2. 完成JS特效
>    在密码框添加“显示”|"隐藏"的功能： bingo
>    在商品的详情页面实现切换图片的功能；
>    删除按钮的“确定删除"功能；
> 3. 模糊查询功能；
> 4. 两种分页；



















