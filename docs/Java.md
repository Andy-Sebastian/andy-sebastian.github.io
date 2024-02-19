# Java

## 接口中的默认方法和静态方法

Java8中在接口引入了默认方法和静态方法

```java
public interface MyInterface {
    default void myMethod() {
        // 默认方法的实现代码
    }
}
```

实现接口的子类可以不用实现接口中的默认方法

```java
public interface MyInterface {
    static void myStaticMethod() {
        // 静态方法的实现代码
    }
}
```

实现接口的子类不能实现接口中的静态类  
静态方法可以作为接口的工具方法，通过接口名调用

## 异常

java中所有的异常类都继承与Throwable类，Throwable类主要包括了两个类：Error类 和 Exception类  

- Error类：错误类，Error类表示那些严重的问题，它们在正常情况下不应该被应用程序捕获
- Exception类：异常类
  - RuntimeException:运行时异常
  - NullPointerException:空指针

Java的异常可分为两类

- CheckedException:检查型异常，Exception类中除了RuntimeException类及其子类的其他类
- UnCheckedException:非检查型异常，RuntimeException类及其子类、Error类及其子类
