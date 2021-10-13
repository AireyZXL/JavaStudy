# Java注解

## 一、注解概述

1.能够读懂别人写的代码，特别是框架代码

2.让编程更加简洁，代码更加清晰

3.让别人高看一眼

## 二、自定义注解

### 自定义注解的语法要求

```java

/**
 * @author Airey
 * @date 2021/10/13 15:36
 * ----------------------------------------------
 * 自定义注解的语法要求
 * 1.使用@interface关键字定义注解
 * 2.成员以无参无异常方式声明
 * 3.可以用default为成员指定一个默认值
 * 4.成员类型时受限的，合法的类型包括原始类型及String,Class，Annotation,Enumeration
 * 5.如果注解只有一个成员，则成员名必须取名为value(),在使用时可以忽略成员名和赋值号( = )
 * 6.注解类可以没有成员，没有成员的注解称为标识注解
 * ----------------------------------------------
 */
@Target({ElementType.METHOD,ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Inherited
@Documented
public @interface Description {


    String desc();

    String author();

    int age() default 18;

}


```


### 注解的注解（元注解）

### 使用自定义注解

### 解析注解