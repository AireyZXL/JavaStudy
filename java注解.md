# Java注解

## 一、注解概述

1.能够读懂别人写的代码，特别是框架代码

2.让编程更加简洁，代码更加清晰

3.让别人高看一眼

## 二、注解的分类

按照运行机制分：

1.源码注解

注解只在源码中存在，编译成.class文件就不存在了

2.编译时注解

注解在源码和.class文件中都存在。

@Override @Deprecated @Suppvisewarnings

3.运行时注解

在运行阶段还起作用，甚至会影响运行逻辑的注解

@Autowired


## 三、自定义注解

### 3.1 自定义注解的语法要求

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

### 3.2 注解的注解（元注解）

1.@Target({ElementType.METHOD,ElementType.TYPE})

@Target 注解的作用域

```java
public enum ElementType {
  
    /** 类，接口 */
    TYPE,

    /** 字段声明  */
    FIELD,

    /** 方法声明 */
    METHOD,

    /** 参数声明 */
    PARAMETER,

    /** 构造方法声明 */
    CONSTRUCTOR,

    /** 局部变量声明 */
    LOCAL_VARIABLE,

    /** Annotation type declaration */
    ANNOTATION_TYPE,

    /** 包声明 */
    PACKAGE,

    /**
     * Type parameter declaration
     *
     * @since 1.8
     */
    TYPE_PARAMETER,

    /**
     * Use of a type
     *
     * @since 1.8
     */
    TYPE_USE
}
```

2.@Retention 注解的生命周期

```java
public enum RetentionPolicy {
    /**
     * Annotations are to be discarded by the compiler.
     *  只有在源码显示，编译时会丢弃
     */
    SOURCE,

    /**
     * Annotations are to be recorded in the class file by the compiler
     * but need not be retained by the VM at run time.  This is the default
     * behavior.
     * 编译时会记录到class中，运行时忽略
     */
    CLASS,

    /**
     * Annotations are to be recorded in the class file by the compiler and
     * retained by the VM at run time, so they may be read reflectively.
     * 运行时存在，可以通过反射读取
     * @see java.lang.reflect.AnnotatedElement
     */
    RUNTIME
}

```

3.@Inherited 允许子类继承

4.@Documented 生成javadoc时会包含注解

### 3.3使用自定义注解

使用注解的语法

@ <注解名>（<成员名1>=<成员值1>,<成员名2>=<成员值2>，....）

```java

  @Description(desc = "I am eyeColor",author = "Mooc boy",age = 18)
    public String eyeColor(){
        return "red";
    }


```

### 3.4 解析注解