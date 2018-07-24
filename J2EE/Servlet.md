# Servlet

## 基础

### 开发Servlet
Servlet 本身不能独立运行，需要在一个 web 应用中运行的  而一个 web 应用是部署在 tomcat 中的，所以开发一个 Servlet 需要如下几个步骤：
1. 创建web应用项目
2. 编写servlet代码
3. 部署到tomcat中
开发的IDE也有各种选择，有的使用 MyEclipse，有的使用 eclipse 的 EE 版本,有的使用 IDEA 开发。 
本例使用 Eclipse EE 版 结合独立的 tomcat 进行一次 java 普通项目的创建。这样做的好处是，通过最原始的方式创建一个 web 应用，可以掌握最基本的知识。以后再碰到相关问题出错的时候，更加利于解决。 
### 获取参数
本例通过登录行为，演示 Servlet 如何获取从浏览器提交的账号密码
1. 创建 login.html
    创建一个 login.html文件
    然后添加一个form元素
    action="login" 标题会提交到login路径，login路径在后续步骤会映射到LoginServlet
    method="post" post方式表示提交的密码信息在浏览器地址栏看不到
    接着准备账号和密码的input元素
    因为要提交两个数据，在servlet端为了区分哪个是账号，哪个是密码，要给这两个input元素的name属性分别叫做name和password。

  ```html
  <!DOCTYPE html>
  <html>
  <head>
  <meta charset="UTF-8">
  <title>登录页面</title>
  </head>
  <body>
    
  <form action="login" method="post">
  账号: <input type="text" name="name"> <br>
  密码: <input type="password" name="password"> <br>
  <input type="submit" value="登录">
  </form>
    
  </body>
  </html>
  ```

2. 创建 LoginServlet

   创建一个LoginServlet  因为浏览器中的form的method是post,所以LoginServlet需要提供一个doPost方法  在doPost方法中，通过request.getParameter 根据name取出对应的账号和密码  然后用System.out.println() 打印在控制台

   ```java
   import java.io.IOException;
    
   import javax.servlet.ServletException;
   import javax.servlet.http.HttpServlet;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;
     
   public class LoginServlet extends HttpServlet {
       protected void doPost(HttpServletRequest request, HttpServletResponse response)
               throws ServletException, IOException {
           String name = request.getParameter("name");
           String password = request.getParameter("password");
     
           System.out.println("name:" + name);
           System.out.println("password:" + password);
       }
   }
   ```

3. 映射 LoginServlet 到路径 login

   在web.xml中新增映射

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <web-app>
    
       <servlet>
           <servlet-name>HelloServlet</servlet-name>
           <servlet-class>HelloServlet</servlet-class>
       </servlet>
    
       <servlet-mapping>
           <servlet-name>HelloServlet</servlet-name>
           <url-pattern>/hello</url-pattern>
       </servlet-mapping>
        
       <servlet>
           <servlet-name>LoginServlet</servlet-name>
           <servlet-class>LoginServlet</servlet-class>
       </servlet>
    
       <servlet-mapping>
           <servlet-name>LoginServlet</servlet-name>
           <url-pattern>/login</url-pattern>
       </servlet-mapping>   
    
   </web-app>
   ```

4. 在页面提交数据

   首先重启 Tomcat 然后访问页面，
   http://127.0.0.1/login.html
   输入账号密码，提交，然后在tomcat的窗口，就可以看到提交的账号和密码了。

### 返回响应

### 调用流程

### service()

### 中文问题

### 生命周期

### 跳转

### 自启动

### request

### response

### 上传文件

## 动态Web项目

### 创建

### 切换

### 导入

### 无法配置Tomcat

### 无法启动Tomcat

### idea

## CRUD

### 查询

### 增加

### 删除

### 编辑

### 更新

### 弊端

## JSON

### 提交数据

### 获取一个对象

### 获取多个对象