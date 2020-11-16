### jQuery

1.jQuery是一个js库。 库：库相当于java的工具类，用来存放东西的。 jQuery是存放js代码的库，放的是用js代码写得函数。

2.dom对象和jQuery对象

​	dom对象使用javaScript的语法创建的对象叫做dom对象，也就是js对象

```js
var obj=document.getElementById("text1");
//obj 是dom对象，也叫做js对象
```

​	jQuery对象：使用jquery语法表示对象叫做jQuery对象。 注意：jQuery表示的对象都是数组。

```js
var jobj=${"text1"};
//jobj就是使用jQuery语法表示的对象，也就是jQuery对象，他是一个数组。
```

dom对象可以和jQuery对象相互转换。

​	dom对象可以转为jQuery对象，语法：$(dom对象)

​	jQuery对象可以转为dom对象，语法： 从数组中获取第一个对象，第一个对象就是dom对象，使用[0]或者get(0)。

#### **3.选择器**：就是一个字符串，用来定位dom对象，定位了dom对象，就可以通过jQuery的函数操作dom

​	常用的选择器：

​	1）：id选择器， 语法：$("#dom对象的id值") 通过dom对象的id找对象，id在页面中是唯一值
​	2）：class选择器，语法：$(".class样式名") class表示css中的样式，使用样式名称定为dom对象

​	3）：标签选择器，语法：$("标签名称") 通过标签的名称定为dom对象

#### **7.each语法**

​	(1).可以对数组，json，dom数组循环处理。数组，json中的每个成员都会调用一次处理函数。

```js
var arr={1,2,3}
var json={"name":"list","age",20}
var obj=${":text"};
```

语法：$.each(循环内容，处理函数)：表示使用jquery的each，循环数组，每个数组成员，都会执行后面的"处理函数"一次

处理函数：function(index,element): 

​			index,element 都是自定义的形参，名称自定义

​			inedx 循环的索引

​			element 数组中的成员

```js
for(var i=0;i<arr.length;i++){
	var item=arr[i];
	print(item);
    shuchu(i,item);
}
function shuchu(index,element){
    //输出index，element
}
```

(2).循环jQuery对象， jQuery对象就是dom数组

​	jquery对象.each( function(index,element){   })

#### 8.jQuery中给dom对象绑定事件

​	1）：$(选择器).事件名称(事件处理函数)

​		$(选择器)：定为dom对象，dom对象可以有多个，这些dom对象都绑定事件了

​		事件名称：就是js中时间去掉on后的部分，例如js中的单击事件 onclick(),事件的处理函数：就是一个function，当事件发生时，执行这个函数的内容

​		例如给id时btn的按钮绑定事件

```js
$("#btn").click(function(){
	alert("btn按钮单击了")
})
```

​	2）：on事件绑定

​	$(选择器).on(事件名称，事件的处理函数)

#### 9.使用jQuery的函数实现ajax请求的处理

jQuery简化了ajax请求的处理。使用三个函数实现：

​	1）$.ajax()：jquery中实现ajax的核心函数。

​	2）$.post()：使用post方式做ajax请求。

​	3）$.get() ：使用get方式发送ajax请求
​	PS：$.post()和$.get()他们内部都是调用了$.ajax()

$.ajax函数的使用，函数的参数表示请求的url，请求方式，参数值等信息。

$.ajax()参数是一个json的结构

例如：$.ajax({名称：值，名称1：值1....})

json结构的参数说明：

1）async：是一个boolean类型的值（xmlHttp.open(get,url,true),第三参数一样的意思。），默认时true，表示异步请求的，可以不写async这个配置项。

2）contentType：一个字符串，表示从浏览器发送服务器的参数的类型。可以不写。

3）data：可以是字符串，数组，json， 表示请求的参数和参数值。常用的是json格式的数据

4）dataType：表示期望从服务器端返回的数据格式；可选的有：xml，thml，text，json，当我们使用$.ajax()发送请求时，会把dataType的值发送给服务器，那我们的servlet能够读取到dataType的值，就知道你的浏览器需要的是json或者xml的数据，那么浏览器就可以返回你需要 的数据格式。

5）error：一个function，表示当请求发送错误时，执行的函数

6）success：一个function，请求成功了，从服务端返回了数据，会执行success指定函数之前使用XMLHttpRequest对象，当readyState==4&&status==200的时候.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               

​	