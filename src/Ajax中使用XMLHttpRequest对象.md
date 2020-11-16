### Ajax中使用XMLHttpRequest对象

1）创建异步对象

```java
var xmlHttp=new XMLHttpRequest();
```

2）给异步对象绑定事件。

​		onreadystatechange:当异步对象发起请求，获取了数据 都会触发这个事件。

```java
btn.onlick=funl()
function funl(){
	alert("按钮单击");
}
```

例如：

```java
xmlHttp.onreadystatechange=function(){
	处理请求的状态变化
        if(xmlHttp.readyState==4,status==200){
            //可以处理服务器端的数据，更新当前页面
            var data=xmlHttp.responseText;
            document.getElementById("name").value=data;
        }
}
```

**异步对象的属性** readyState 表示异步对象请求的状态变化

​	0：创建异步对象时， new XMLHttpRequest（）;

​	1：初始化异步请求对象，xmlHttp.open（）；

​	2：发送请求，xmlHttp.send（）；

​	3：从服务器端获取数据，此时为3 . 注意3是异步对象内部使用，表示获取了原始数据。

​	4：异步对象把接收的数据处理完成后。此时开发人员在4的时候来处理数据。在4的时候开发人员  更新当前页面。

**异步对象的status属性**，表示网络请求的状况的。200，404，500， 当status==200时，表示网络请求是成功的。

3）初始异步请求对象

​	异步的方法open（）

​	xmlHttp.open(请求方式get | post)，“服务器端的访问地址”，同步 | 异步（默认时true 异步请求）

例如：

```java
xmlHttp.open("get","loginServlet?name=zs&pass=123",true);
```

4）使用异步对象发送请求

​	xmlHttp.send()

获取服务器端返回的数据，使用异步对象的属性 responseText

使用例子：xmlHttp.responseText

回调：当请求状态变化时，异步对象会自动调用onreadystatechange时间对应的函数。

### Json

json分类：

​	1.json对象，JSONObject，这种对象的格式  名称：值，也可以看成 key:value格式

​	2.json数组,JSONArray,基本格式  [{name:"河北",jiancehng:"冀",shenghui:"石家庄"}] 

为什么用json:

​	1）json格式好理解

​	2）json格式数据再多语言中，比较容量处理/

​	3）json格式数据占用的空间下，在网络中传输快，用户体验好

再js中的，可以把json格式的字符串，转为json对象， json中的key，就是json队形的属性名。