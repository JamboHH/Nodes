### 文件上传：

> **表单：**
> ​	提交方式：post
> ​	修改：enctype="multipart/form-data"
> ​	上传提交按钮：< input type="file" />
>
> **加入上传组件：SmartUpload**
> ​	引入smartUpload.jar
> ​	使用API文档
>
> ```
> 实例化组件： SmartUpload su=new SmartUpload();
> 初始化： su.initialize(ServletConfig，HttpServletRequest,HttpServletResponse)
> 获得一个Request对象：Request request=su.getRequest();  ===此处的request是SmartUpload里的
> 对表单中普通表单元素的处理：
> 	例：request.getParameter("");
> 上传文件的处理：
> 	Files files = su.getFiles();//获得上传文件
>     File file = files.getFile(0);//再获得第一个上传文件
> 上传：su.upload();
> 保存：保存图片的位置 su.save("/");  项目根目录保存方式
> ```
>
> 注：引入SmartUpload后，原来的HttpServletRequest对象失效；
> ​	对于上传文件名称的处理：使用随机字符串重新命名：
> ​			UUID.randomUUID().toString()