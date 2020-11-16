#### ** Cookie**

```java
1.介绍:
	1）Cookie来自于Servlet规范中的一个工具类，存在于Tomcat提供servlet-api.jar中
	2）如果两个servlet来自于同一个网站 并为同一个浏览器/用户提供服务，此时借助于Cookie对象进行数据共享
	3）Cookie存放当前用户的私人数据，在共享数据过程中提高服务质量
	4）在现实生活场景中，Cookie相当于会员卡。
2.原理：
	用户通过浏览器第一次向MyWeb网站发送请求申请OneServlert。One在运行期间创建一个Cookie存储鱼当前用户相关数据OneServlet  	 工作完毕后，将Cookie写入到响应头 交给当前浏览器。 浏览器收到响应包之后，将cookie存储在浏览器的缓存中，一段时间后，用	  户通过【同一个浏览器】再次访问【Myweb网站】发送请求申请TwoServlet时。【浏览器需要无条件地将myWeb网站之前推送过来的	 Cookie,写入到请求头中】发送过去。此时Two在运行时，就可以通过读取请求头中的Cookie中信息来得到ONe提供的共享数据。
3.实现命令：同一个网站One与Two借助于Cookie实现数据共享
	OneServlet{
		public void doGet(HttpServletRequest request,HttpServletResponse response){
			//1.创建一个Cookie对象，保存共享数据
			Cookie card=new Cookie("key1","abc");
            Cookie card1=new Cookie("key2","efg");
            //Cookie相当于一个Map，一个cookie中只能存放一个键值对，而且这个键值对只能是String，键值对中的key不能是中文
            //2.【发卡】 将cookie写入到响应头中
            response.addCookie(card);
            response.addCookie(Card1);
		}
	}
	浏览器向myweb网站发送请求访问Two
     TwoServlet{
        public void doGet(HttpServletRequest request,HttpServletResponse response){
            //1.调用请求对象从请求头中得到浏览器返回的Cookie
            Cookie cookieArray[]=request.getCookies();
            //2.循环遍历数组 得到每一个cookie的key与value
            for(Cookie card:cookieArray){·
               String key= card.getName();//读取key
               String value=card.getValue();//读取值
            }
        }
     }
```

