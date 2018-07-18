# HTML

- 概念
  1. 中文问题

     中文乱码问题可以在浏览器上设置编码方式为 **GB2312 或 UTF-8** 或者在 html 代码的最前面加上编码设置

     ```html
     <head> 
     <meta http-equiv="Content-Type" content="text/html; charset=GB2312"> 
     </head>
     
     ```

     

  2. 标签

     HTML是 Hyper Text Markup Language 超文本标记语言 的缩写，HTML是由一套标记标签 （markup tag）组成，通常就叫标签，标签由开始标签和结束标签组成 

     `<p> `这是一个开始标签  

     `</p> `这是一个结束标签  

     `<p>` Hello World `</p> `标签之间的文本叫做内容 

  3. 元素

     元素指的是包括开始标签到结束标签的代码  

     比如  `<p>`HelloWorld`</p>`  

     元素包括

     - 完整的元素
     - 不完整的元素
     - 特殊的元素

  4. 属性

     属性用来修饰标签的，比如要设置一个标题居中 

     `<h1 align="center">`居中标题`</h1>`

     写在开始标签里的 `align="center"` 

     就叫属性 

     `align` 是属性名

     `center` 是属性值

     属性值应该使用双引号括起来

  5. 注释

     html使用`<!-- --> `进行注释 

- 基本元素
  1. 标题

     标题会自动粗体，大写其中的内容，并且带有换行效果   一般会使用 `<h1>` 到 `<h5>` 分别表示不同大小的标题 

  2. 段落

     `<p> `标签即表示段落，是 paragraph 的缩写，自带换行效果 

  3. 粗体

     `<b>`  `<strong> ` 都可以用来实现粗体的效果

     > 区别： b是 bold 的缩写，仅仅表示该文本是粗体的，并不暗示这段文字的重要性 strong 虽然也是粗体，但是更多的是强调语义上的加重，提醒用户该文本的重要性。 在 SEO（搜索引擎优化）的时候，也更加容易帮助用户找到重点的内容 推荐使用 strong 

  4. 斜体

     `<i>`和`<em>`都可以表示斜体效果 

     > 区别： i 是 italic 的缩写，仅仅表示该文本是斜体的，并不暗示这段文字的重要性  em 是 Emphasized 的缩写，虽然也是斜体，但是更多的是强调语义上的加重，提醒用户该文本的重要性。 常常用于引入新的术语的时候使用。 

  5. 预格式

     有时候，需要在网页上显示代码，比如java代码，就需要用到 pre，**保留原有缩进**

  6. 删除效果

     `<del>`即删除标签 delete 的缩写 

  7. 下划线

     `<ins>`即下划线标签

     但是通常来讲，不要给普通文本加下划线，因为用户会误以为是一个超链接

  8. 图像

     `<img>` 即图像标签  需要设置其属性 src 指定图像的路径

     - 同级目录图像
     - 上级目录图像
     - 其他目录图像
     - 设置图像大小
     - 图像居中
     - 异常处理 alt 属性

  9. 超链接

     `<a>`标签即用来显示超链   完整元素是   `<a href="跳转到的页面地址">超链显示文本</a> `

     - 在新的页面打开（涉及安全问题）
     - 超链接上的提示文字
     - 使用图片代替文本作为超链接

  10. 表格

      `<table>`标签用于显示一个表格  

      `<tr>` 表示行  

      `<td>` 表示列又叫单元格 

      - 带边框的表格

        table 标签的 border 属性，默认为 0

      - 设置 table 的宽度

      - 单元格宽度绝对值

      - 单元格宽度相对值（百分比）

      - 单元格水平对齐

      - 单元格垂直对齐

      - 横跨两列，水平合并

      - 纵跨两行，垂直合并

      - 背景色（颜色的两种表示法）

  11. 列表

      列表分无序列表和有序列表，分别用`<ul>`标签和`<ol>`标签表示

      列表中的行元素用`<li>`标签表示

  12. 块

      `<div> `  `<span> `  这两种标签都是布局用的，这种标签本身没有任何显示效果，通常是用来结合 css 进行页面布局 

      div和span的区别 

      > div是块元素，即自动换行  常见的块元素还有 h1,table,p  
      >
      > span 是内联元素，即不会换行  常见的内联元素还有 img,a,b,strong 

  13. 字体

      使用`<font>`标签表示字体

      font常用的属性有 color 和 size, 分别表示颜色和大小  

  14. 内联框架

      `<iframe>`即内联框架   通过内联框架 可以实现在网页中“插入”网页 

- 表单元素

  1. 文本框

     `<input type="text">` 即表示文本框   并且只能够输入一行   如果要输入多行   使用[文本域](http://how2j.cn/k/html/html-textarea/196.html)   注： `<input>` 标签很特别，一般是不需要写成`<input />`或者`<input></input> `这样的。  并且`<input>` 这样的写法也是满足标准的 

     - size 属性：设置文本框长度
     - value 属性：设置初始值
     - placeholder 属性：设置背景文字

  2. 密码框

     `<input type="password"> `即表示密码框  

  3. 表单

     - `<form>`用于向服务器提交数据，比如账号密码  

     ```html
     <form action="http://how2j.cn/study/login.jsp">
     账号：<input type="text" name="name"> <br/>
     密码：<input type="password" name="password" > <br/>
     <input type="submit" value="登陆">
     </form>
     ```

     - method="get"  

       使用 method="get" 提交数据 是常用的提交数据的方式  如果 form 元素没有提供 method 属性，默认就是 get 方式提交数据 ，get 方式的一个特点就是，可以在浏览器的地址栏看到提交的参数，即便是密码也看得到 

       ``` html
       <form method="get" action="http://how2j.cn/study/login.jsp">
       账号：<input type="text" name="name"> <br/>
       密码：<input type="password" name="password" > <br/>
       <input type="submit" value="登陆">
       </form>
       ```

     - method="post"

       使用 method="post" 也可以提交数据  post 不会在地址栏显示提交的参数  如果要提交二进制数据，比如上传文件，必须采用 post 方式 

       ```html
       <form method="post" action="http://how2j.cn/study/login.jsp">
       账号：<input type="text" name="name"> <br/>
       密码：<input type="password" name="password" > <br/>
       <input type="submit" value="登陆">
       </form>
       ```

     - get 和 post 的区别

       get  是 form 默认的提交方式  如果通过一个超链访问某个地址，是 get 方式  如果在地址栏直接输入某个地址，是 get 方式  提交数据会在浏览器显示出来  不可以用于提交二进制数据，比如上传文件  

       post  必须在 form 上通过 method="post" 显示指定  提交数据不会在浏览器显示出来  可以用于提交二进制数据，比如上传文件 

  4. 单选框

     `<input type="radio">` 表示单选框

     - checked 属性：默认选中
     - 分组：分组即：多个单选框，都在一个分组里，同一时间，只能选中一个单选框  设置 name 属性相同即可 

  5. 复选框

     `<input type="checkbox"> `即表示复选框 

  6. 下拉列表

     `<select>` 即下拉列表  需要配合`<option>`使用 

     ```html
     <select >
      <option >苍老师</option>
      <option >高树玛利亚</option>
      <option >遥美</option>
     </select>
     ```

     - size 属性：设置高度

     ```html
     <select  size="2">
      <option >苍老师</option>
      <option >高树玛利亚</option>
      <option >遥美</option>
     </select>
     ```

     - multiple 属性：设置多选

     ```html
     <select size="3" multiple="multiple">
      <option >苍老师</option>
      <option >高树玛利亚</option>
      <option >遥美</option>
     </select>
     ```

     - selected 属性：默认选中

     ```html
     <select size="3" multiple="multiple">
      <option >苍老师</option>
      <option selected="selected">高树玛利亚</option>
      <option selected="selected">遥美</option>
     </select>
     ```

  7. 文本域

     `<textarea> `即文本域，与文本框不同的是，文本域可以有多行，并且可以有滚动条 

     ```html
     <textarea>abc
     def
     </textarea>
     ```

     - cols 和 rows 属性：设置宽度和行数

     ```html
     <textarea cols="30" rows="8">123456789012345678901234567890
     1234567890
     1234567890
     1234567890
     1234567890
     1234567890
     1234567890
     1234567890</textarea>
     ```

  8. 普通按钮

     `<input type="button">` 即普通按钮，不具备提交效果

     ```html
     <input type="button" value="一个按钮">
     ```

  9. 提交按钮

     `<input type="submit">` 即为提交按钮  用于提交 form，把数据提交到服务端 

     ```html
     <form action="/study/login.jsp" method="get">
     账号：<input type="text" name="name"> <br/>
     密码：<input type="password" name="password" > <br/>
     <input type="submit" value="登陆">
     </form>
     ```

  10. 重置按钮

      `<input type="reset">` 重置按钮 可以把输入框的改动复原  

      ```html
      <form action="/study/login.jsp">
      账号：<input type="text" name="name"> <br/>
      密码：<input type="password" name="password" > <br/>
      <input type="submit" value="提交">
      <input type="reset" value="重置">
      </form>
      ```

  11. 图像提交

      `<input type="image" >` 即使用图像作为按钮进行 form 的提交 

      - src 属性：

      ```html
      <form action="/study/login.jsp">
      账号：<input type="text" name="name"> <br/>
      密码：<input type="password" name="password" > <br/>
      <input type="image" src="http://how2j.cn/example.gif">
      </form>
      ```

  12. 按钮

      `<button></button>`即按钮标签  与`input type="button">`不同的是，`<button>`标签功能更为丰富，按钮标签里的内容可以是文字也可以是图像，如果 button 的`type=“submit” `，那么它就具备提交 form 的功能 

      - button 里是文字

        ```html
        <button>按钮</button>
        ```

      - button里是图片

        ```html
        <button><img src="http://how2j.cn/example.gif"/></button>
        ```

      - 提交数据

        ```html
        <form action="/study/login.jsp">
        账号：<input type="text" name="name"> <br/>
        密码：<input type="password" name="password" > <br/>
         
        <button type="submit">登陆</button>
         
        </form>
        ```

        