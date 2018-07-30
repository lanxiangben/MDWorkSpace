# 异常的概念

异常定义：导致程序的正常流程被中断的事件，叫做异常。

示例：文件不存在异常（FileNotFoundException）

```java
package exception;
  
import java.io.File;
import java.io.FileInputStream;
  
public class TestException {
  
    public static void main(String[] args) {
          
        File f= new File("d:/LOL.exe");
          
        //试图打开文件LOL.exe，会抛出FileNotFoundException，如果不处理该异常，就会有编译错误
        new FileInputStream(f);
          
    }
}
```

问题：到目前为止，都接触了哪些异常，分别在什么场景出现？

# 异常处理

异常处理常见手段：try catch finally throws

## try catch

1. 将可能抛出 FileNotFoundException 的代码放在 try{} 里；
2. 如果文件存在，就会顺序执行，且不执行 catch{} 中的代码；
3. 如果文件不存在，try{} 里的代码会立即终止，程序流程会运行到对应的 catch{} 中；
4. e.printStackTrace()；会打印出方法的调用轨迹，便于分析和定位哪里出现了异常。

示例：

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
 
public class TestException {
 
    public static void main(String[] args) {
         
        File f= new File("d:/LOL.exe");
         
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
        catch(FileNotFoundException e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
         
    }
}
```

## 使用异常的父类进行 catch

FileNotFoundException 是 Exception 的子类，使用 Exception 也可以 catch 住 FileNotFoundException。

示例：

```java
package exception;
  
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
  
public class TestException {
  
    public static void main(String[] args) {
          
        File f= new File("d:/LOL.exe");
          
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
         
        catch(Exception e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
          
    }
}
```

## 多异常捕捉

### 方法一：使用多个 catch

示例：

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
 
public class TestException {
 
    public static void main(String[] args) {
 
        File f = new File("d:/LOL.exe");
 
        try {
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
            Date d = sdf.parse("2016-06-03");
        } catch (FileNotFoundException e) {
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        } catch (ParseException e) {
            System.out.println("日期格式解析错误");
            e.printStackTrace();
        }
    }
}
```

### 方法二：在一个 catch 中进行判断

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
 
public class TestException {
 
    public static void main(String[] args) {
 
        File f = new File("d:/LOL.exe");
 
        try {
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
            Date d = sdf.parse("2016-06-03");
        } catch (FileNotFoundException | ParseException e) {
            if (e instanceof FileNotFoundException)
                System.out.println("d:/LOL.exe不存在");
            if (e instanceof ParseException)
                System.out.println("日期格式解析错误");
 
            e.printStackTrace();
        }
 
    }
}
```

**这种方法需要JDK1.7及以上版本支持，优点是 catch 代码更紧凑，缺点是不能确定发生了哪种异常。**

## finally

无论是否发生异常，finally 中的代码都会被执行，通常用来关闭数据库连接。

示例：

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
 
public class TestException {
 
    public static void main(String[] args) {
         
        File f= new File("d:/LOL.exe");
         
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
        catch(FileNotFoundException e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
        finally{
            System.out.println("无论文件是否存在， 都会执行的代码");
        }
    }
}
```

## throws

考虑如下情况：

主方法调用 method1，method1 调用 method2。method2 中打开文件，需要经常处理异常，但是 method2 不打算处理异常，而是把这个异常通过 throws 抛出去。那么 method1 就会接到该异常。处理方法也是**两种**：

1. try catch 处理
2. 继续 throws 抛出

一旦选择了方法1，则异常就在 method1 中消化掉了，main 方法中不必在处理。

示例：

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
 
public class TestException {
 
    public static void main(String[] args) {
        method1();
 
    }
 
    private static void method1() {
        try {
            method2();
        } catch (FileNotFoundException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
    }
 
    private static void method2() throws FileNotFoundException {
 
        File f = new File("d:/LOL.exe");
 
        System.out.println("试图打开 d:/LOL.exe");
        new FileInputStream(f);
        System.out.println("成功打开");
 
    }
}
```

## throws 和 throw 的区别

1. throws 出现在方法声明上；throw 出现在方法体内
2. throws 表示出现异常的一种可能性，并不一定会发生这些异常；throw 则是抛出了异常，执行 throw 则一定抛出了某个异常对象。 

## 问题

假设有一个方法 public int method()，返回一个整数。在这个方法中有 try catch 和 finally。

try 里返回1；

catch 里返回2；

finally 里返回3；

那么这个方法到底返回多少？

# 异常分类

# Throwable

# 自定义异常

