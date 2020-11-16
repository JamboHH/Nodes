### 复习

> ajax异步通讯：
>
> 步骤：
> ​	创建对象：XMLHttpRequest对象
> ​	发送请求：
> ​		open(请求方式，请求地址);
> ​		send();
> ​	处理响应：
> ​		onreadystatechange=function(){
> ​			 //判断请求状态  readyState==4 
> ​			 //响应状态码 status==200  
> ​			//处理响应结果  responseText---处理字符串类型结果/json结果
> ​		}
>
> json：
> ​	JS中：{属性名:值}--对象
>
> ​	java中："{\ "属性名\ ":值}"
>
> ​	解析方式--转换：java类对象与json字符串
> ​		FastJson方式： 引入jar包；
> ​			类对象-->字符串：JSON.toJSONString(类对象)
> ​			字符串-->类对象：JSON.parseObject(String串, Class对象);
>
> 页面处理json
>
> ​	JSON---JS中的对象；
> ​		处理结果时将responseText字符串转换为页面中的对象：JSON.parse(字符串)

### DOM操作对象

> 创建节点：document.createElement(标签名)
>
> 给标签添加内容：innerHTML属性设置双标签内容
>
> 添加节点：父节点.appendChild(子节点);

### 补充jsp

```
<jsp:include page="被引入jsp页面的地址" />
```

### 使用bootstrap

> 引入环境
>
> ```
> 引入css： 
> <link type="text/css" rel="stylesheet" href="static/bootstrap/css/bootstrap.min.css"/>
> 引入jQuery：
> <script type="text/javascript" src="static/bootstrap/jquery-3.4.1.min.js"></script>
> 引入bootstrap的js文件：
> <script type="text/javascript" src="static/bootstrap/js/bootstrap.min.js"></script>
> ```
>
> 每个bootstrap页面都是一个容器，并且列包含在行中，那么：
>
> ```
> <div class="container">
> 	<div class="row">
> 		.....栅格布局
> 	</div>
> </div>
> ```
>
> 栅格系统：将一行分为12个列
>
> ```
>  例：下面是6列，每列占2个列宽
>  <div class="row">
>  	<div class="col-md-2"></div>
>  	<div class="col-md-2"></div>
>  	<div class="col-md-2"></div>
>  	<div class="col-md-2"></div>
>  	<div class="col-md-2"></div>
>  	<div class="col-md-2"></div>
>  </div>   
> ```
>
>

### 补充mysql外键关联

> 外键
>
> ```
> alter table 从表名 add constraint 外键名 foreign key(从表外键字段名) references 主表名(主表主键字段)
> ```
>
>