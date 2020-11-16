

​	

### 统计购物车总价：

> 查看购物车时：
>
> ```
> 在CartController中统计所有ShopItem明细，并计算总价，发往页面进行展示；
> request.setAttribute("total",计算机结果);
> 
> 将统计总价的方法封装在ShopCart中：
> 	public int getTotalPrice(){
>         Collection<ShopItem> items=cart.values();
>         //遍历items并获得计算总价的结果
>         return 结果；
> 	}
> ```
>
> 修改数量：
>
> ```
> 在controller中再次统计总价：shopCart.getTotalPrice();
> 发往页面时，需要将所有数据定义为一个json串发送；
> ```
>
> 删除一条购物明细时：
>
> ```
> 删除信息后，重新加载页加，此时购物总价会重新计算后再次更新；
> ```
>
> 清空购物车信息时：
>

### 删除购物车明细：

> 删除一条购物车明细：
>
> ```
> 删除session中的信息和数据库中的购物信息；
> 	session中的删除：根据商品编号删除map中的一个值；
> 	数据库中的删除：根据用户编号和商品编号删除一条cart表中的信息；
> ```
>
> 清空购物车信息：

### 验证码：

> **awt包相关类：**
>
> ```
> response.setContentType("设置响应文件类型");
> 
> BufferedImage (宽，高，画笔类型rgb)
> Graphics g=getGraphics(); //实现绘画方法的调用类
> 
> g.setFont(名称，样式，大小)  //设置字体
> g.setColor(Color类) //设置颜色
> g.fillRect(x,y,width,height); //填充矩形，并设置宽度
> g.drawLine(x,y,x1,y1); //画线条，两个坐标一个点，两点一线
> g.drawString("字符串内容",x,y);//画字符串，定起始的坐标
> 
> g.dispose(); //绘画结束
> 
> ImageIo.write(BufferedImage对象，"文件扩展名",reponse.getOutputStream());
> ```
>
> **定义一个方法：**用于生成验证码内容：
>
> ```
> private String source="内容"；
> public String getCode(){
>     //随机取出source的字符，并拼接为一个字符串并返回
> }
> ```
>
> 使用配置初始化参数的方式实现验证码字符的定义：
>
> ```
> web.xml中的配置：
> 	<servlet>
>         <servlet-name>LoadController</servlet-name>
>         <servlet-class>com.qf.controller.LoadController</servlet-class>
>         <init-param>
>             <param-name>rowsPerPage</param-name>
>             <param-value>5</param-value>
>         </init-param>
>     </servlet>
> 注解开发的配置：
> 	@WebServlet(urlPatterns = "/pic",initParams = {@WebInitParam(name="source",value = "ABCDEFGHIJKLMNOPQRSTUVWXYZ")})
> 	
> 读取初始化参数：?????????????
> 	public void init(ServletConfig config){
>         config.getInitParameter("source");
> 	}
> ```
>
>

### 免登录：Cookie

> 在客户端的一种小数据量的存储技术；
>
> 创建：
>
> ```
> Cookie ck=new Cookie(名，值);
> ck.setMaxAge(以秒为单位); //一定要设置生命存活时间，创建之后就开始计时；
> response.addCookie(ck);
> 
> 注：session的生命存活时间，默认30分钟；从最后一次操作开始计时；
> ```
>
> 获得：
>
> ```
> Cookie[] cks=request.getCookies();
> //遍历数组，获得所有cookie的值
> getName()---获得名称
> getValue()---获得值
> ```
>
> cookie中存取中文：
>
> ```
> Cookie ck=new Cookie(URLEncoder.encode("姓名","utf-8"),"haha");
> 
> Cookie[] ck=request.getCookies();
> ck[0].getName(URLDecoder.decode("姓名","utf-8"));
> ```
>
>

购物车生成订单 