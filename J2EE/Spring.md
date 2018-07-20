# Spring

1. ## IOC/DI

   > Spring是一个基于IOC和AOP的结构J2EE系统的框架  IOC 反转控制 是Spring的基础，Inversion Of Control  简单说就是创建对象由以前的程序员自己new 构造方法来调用，变成了交由Spring创建对象  DI 依赖注入 Dependency Inject. 简单地说就是拿到的对象的属性，已经被注入好相关值了，直接使用即可。 

   - pojo 类

     ```java
     package com.how2java.pojo;
      
     public class Category {
      
         public int getId() {
             return id;
         }
         public void setId(int id) {
             this.id = id;
         }
         public String getName() {
             return name;
         }
         public void setName(String name) {
             this.name = name;
         }
         private int id;
         private String name;
     }
     ```

   - applicationContext.xml 配置文件

     > applicationContext.xml 是 Spring 的核心配置文件，通过关键字 c 即可获取 Category 对象，该对象获取的时候，即被注入了字符串"category 1“到 name 属性中 

     ```xml
     <?xml version="1.0" encoding="UTF-8"?>
     <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:aop="http://www.springframework.org/schema/aop"
         xmlns:tx="http://www.springframework.org/schema/tx"
         xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
        http://www.springframework.org/schema/aop
        http://www.springframework.org/schema/aop/spring-aop-3.0.xsd
        http://www.springframework.org/schema/tx
        http://www.springframework.org/schema/tx/spring-tx-3.0.xsd
        http://www.springframework.org/schema/context     
        http://www.springframework.org/schema/context/spring-context-3.0.xsd">
       
         <bean name="c" class="com.how2java.pojo.Category">
             <property name="name" value="category 1" />
         </bean>
       
     </beans>
     ```

   - 测试类 TestSpring

     > 测试代码，演示通过 Spring 获取 Category 对象，以及该对象被注入的 name 属性。 

     ```java
     package com.how2java.test;
      
     import org.springframework.context.ApplicationContext;
     import org.springframework.context.support.ClassPathXmlApplicationContext;
      
     import com.how2java.pojo.Category;
      
     public class TestSpring {
      
         public static void main(String[] args) {
             ApplicationContext context = new ClassPathXmlApplicationContext(
                     new String[] { "applicationContext.xml" });
      
             Category c = (Category) context.getBean("c");
              
             System.out.println(c.getName());
         }
     }
     ```

    - 运行结果

      > 如图所示，可以打印出通过Spring拿到的Category对象的name属性
![运行结果](C:\Users\向奔\Desktop\GitHub\MarkDownNoteBook\J2EE\img\214.png)

2. ## 注入对象

   - pojo 类

     ```java
     package com.how2java.pojo;
      
     public class Category {
      
         public int getId() {
             return id;
         }
         public void setId(int id) {
             this.id = id;
         }
         public String getName() {
             return name;
         }
         public void setName(String name) {
             this.name = name;
         }
         private int id;
         private String name;
     }
     ```

   - Product 类

     >  Product 类中有对 Category 对象的 setter 和 getter 

     ```java
     package com.how2java.pojo;
      
     public class Product {
      
         private int id;
         private String name;
         private Category category;
         public int getId() {
             return id;
         }
         public void setId(int id) {
             this.id = id;
         }
         public String getName() {
             return name;
         }
         public void setName(String name) {
             this.name = name;
         }
         public Category getCategory() {
             return category;
         }
         public void setCategory(Category category) {
             this.category = category;
         }
     }
     ```

   - applicationContext 配置文件

     > 在创建 Product 的时候注入一个 Category 对象 注意，这里要使用 ref 来注入另一个对象 

     ```xml
     <?xml version="1.0" encoding="UTF-8"?>
     <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:aop="http://www.springframework.org/schema/aop"
         xmlns:tx="http://www.springframework.org/schema/tx" xmlns:context="http://www.springframework.org/schema/context"
         xsi:schemaLocation="
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
        http://www.springframework.org/schema/aop
        http://www.springframework.org/schema/aop/spring-aop-3.0.xsd
        http://www.springframework.org/schema/tx
        http://www.springframework.org/schema/tx/spring-tx-3.0.xsd
        http://www.springframework.org/schema/context     
        http://www.springframework.org/schema/context/spring-context-3.0.xsd">
      
         <bean name="c" class="com.how2java.pojo.Category">
             <property name="name" value="category 1" />
         </bean>
         <bean name="p" class="com.how2java.pojo.Product">
             <property name="name" value="product1" />
             <property name="category" ref="c" />
         </bean>
      
     </beans>
     ```

   - TestSpring 测试类

     ```java
     package com.how2java.test;
      
     import org.springframework.context.ApplicationContext;
     import org.springframework.context.support.ClassPathXmlApplicationContext;
      
     import com.how2java.pojo.Product;
      
     public class TestSpring {
      
         public static void main(String[] args) {
             ApplicationContext context = new ClassPathXmlApplicationContext(new String[] { "applicationContext.xml" });
      
             Product p = (Product) context.getBean("p");
      
             System.out.println(p.getName());
             System.out.println(p.getCategory().getName());
         }
     }
     ```

    - 运行效果

      > 通过 Spring 拿到的 Product 对象已经被注入了 Category 对象了 

      ![avatar](C:\Users\向奔\Desktop\GitHub\MarkDownNoteBook\J2EE\img\217.png)

3. ## 注解方式 IOC/DI

   

4. ## AOP

   

5. ## 注解方式AOP

   

6. ## 注解方式测试

   

7. ## Spring MVC

   