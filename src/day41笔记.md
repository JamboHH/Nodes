

### DOM

> 父节点：parentNode
>
> 子节点：
> ​	所有子节点：children
>
> 兄弟节点：
> ​	前一个兄弟：previousElementSibling
> ​	后一个兄弟：nextElementSibling
>
> ```
> <div>
> 	<p>
> 		<img>
> 		<span></span>
> 		<button></button>
> 	</p>
> </div>
> ```
>
>

### jQuery

> **引入jQuery文件：*****.js
>
> ```
> <script type="text/javascript" src="***.js文件地址"></script>
> ```
>
> **从页面加载开始：**
>
> ```
> $(function(){
>     
> })
> ```
>
> **获得对象**
>
> ```
> $("#id值")--获得一个对象
> $(".class值")---获得一个或多个对象
> $("标签名")---获得一个或多个对象
> ```
>
> **绑定事件**
>
> ```
> 事件以前是以：onXXX命名的属性；
> 在jQuery中事件都是以方法形式定义：
> 	onclick属性----click()方法
> 	onmouseover属性----mouseover()方法
> ```
>
> **jQuery封装的ajax：**
>
> ```
> $.get(请求地址，key/value参数，回调函数，返回结果类型)
> 
> 例：以下的处理结果直接将json结果赋给res
> 	$.get("cart",{name:"add",age:10,gender:true},function(res){
>     	//res即为原先的responseText
> 	},"json")
> ```
>
>

### 购物车功能

> ShopCart类：购物车类
> ​	购物车信息：商品信息、用户信息、购物车商品数量
> ​	属性：cart---private、容器(数组--、集合--list  set  map<商品唯一属性,购物车明细>)
> ​	方法：
> ​		addCart();---操作cart属性
>
> ```
> public int addCart(Goods goods){
>     //当前goods的id是否已经存在于cart属性中
>     //如果含有：取出cart的值，数量加1；
>     //如果不含有：直接将goods添加到cart中；
> }
> ```
>
> ShopItem类：购物车明细类
> ​	属性：商品信息goods/购物车数量nums=1

### session对象

> session是一个由服务器创建的会话对象；可以存放用户状态；可以在会话期间存储数据；
>
> session获取: request.getSession();
>
> 向session中存对象：request.setAttribute(名，值);
>
> 在java代码中取出存储对象：request.getAtribute(名)
>
> 在页面中取出存储对象：${session对象的名}
>
> 注销功能：即使session失效  invilidate()

### 结合session存放购物车信息

> controller层：
>
> ```
> 获得商品的id，查询到一个商品；
> 获得session,并判断session中是否存在ShopCart；----替代了Service层的功能；
>     如果存在：取出；
>     如果不存在：新建
> 调用ShopCart内部的加入购物车方法：addCart方法，并且存入session中去；
> 	session.setAttribute("cart",shopCart对象)
> ```
>
> dao层：
>
> ```
> ShopCart类：
> 	属性：cart属性，是map类型
> 	方法：用来操作属性
> ```
>
>





















