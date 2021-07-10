

[TOC]

## 0  代码框架

使用一个代码工程，完成对域和修饰符的学习

```tree
-SF_exercise
    -ClassMain.java
    -Scope.java
```

在一个`SF_exercise`文件夹里有两个文件，其中ClassMain.java里执行主函数，Scope.java是为了学习而制造的其他类。

##  1 static and non-static

static表示“全局”或者“静态”的意思，用来修饰成员变量和成员方法

###  1.1  对于类

static表示“全局”或者“静态”的意思，用来修饰成员变量和成员方法。

显然，只有一个类的成员可以用static来修饰。那么，对于我们的代码，显然`Scope.java`里的`Scope`类和`ClassMain.java`类里的`ClassMain`类前面，都不可以有这个修饰符。

####  类中的类

可以将一个类的定义放在另一个类的内部定义，这样的类就被称为嵌套类，包含嵌套类的类被称为外部类(outer class)，也可以叫做封闭类。

嵌套类可以分为两种：

- 静态嵌套类(Static Nested Classes)：使用static声明，一般称为嵌套类(Nested Classes)；
- 非静态嵌套类(Non-static Nested Classes)：非static声明，一般称为内部类(Inner Classes)；

嵌套类是它的外部类的成员。`非静态嵌套类（内部类）可以访问外部类的其他成员，即使该成员是私有的，而静态嵌套类只能访问外部类的静态成员。`


###  1.2  类中的方法

类中的数据也就是属性，可以设置为`static`和`no static`,根据我们代码的结构完成理解：

####  `ClassMain.java`

```java
public class ClassMain {

    public static void main(String[] args) {
        Scope poppa = new Scope();
        poppa.bark();
        Scope.bark();//会报错
        poppa.runFast();
        Scope.runFast();
    }
}
```

####  `Scope.java`

```java
public class Scope{
    static int only_one = 1;
    int maybe_many = 12;
    public void bark(){
        System.out.println("Moo");
    }
    public static void runFast(){
        System.out.println("Ruff Run");
    }
}
```

在主函数中，外部类Scope和Scope的实体都可以调用`static`的成员方法，不会报错。但是一般情况下，类调用static，实体调用non-static,只是如果实体调用static，也可以，语法允许。

但是，只有实体可以调用non-static，类调用non-static会报错。

这是为什么呢？

static是静态修饰符：
什么叫静态修饰符呢？大家都知道，在程序中任何变量或者代码都是在编译时由系统自动分配内存来存储的，`而所谓静态就是指在编译后所分配的内存会一直存在，直到程序退出内存才会释放这个空间，也就是只要程序在运行，那么这块内存就会一直存在。`

也就是说，static在编译的时候分配内存，存在这个static的东西，所以实体和类都可以调用它，但是non-static的东西，没有在编译的时候分配内存，所以需要先生成一个实体，实体里含有这个non-static的东西，再通过实体调用。

###  1.3  类中的属性

基本和方法差不多，不过这里要注意。

如果一个属性是static，那个，不管创建了多少个实体，比方说，上面的代码，`    static int only_one = 1;   int maybe_many = 12;`

不管创建了多少个实体，`   static int only_one`不会重复创建到实体里，只会有一个内存，放这个变量的值，当类和实体去调用only_one 的时候，整个代码，都会访问到这一个变量。only_one 不属性任何一个实体，就是放到一旁，每个类和实体都可以访问它。

而每创建一个实体，`int maybe_many`都会被重复创建，每个实体里都有一个`int maybe_many`.

## 2 public private and protected

这里就是说，一个变量和方法前面，加上范围修饰符后，什么其他的方法可以访问这些他们呢？一张图解决，这里需要去理解包，以及包内类的概念。

比如，我在`Scope.java`和`ClassMain.java`代码里最上一行，加上`package SF_exercise;`表示，这两个函数在一个包内，这个包就是SF_exercise文件夹，这两个类就是同一个包的类。

[官方教程](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html)

![image-20210612115647806](https://gitee.com/umecjf/figures/raw/master/image-20210612115647806.png)



## 互相交流

欢迎大家一起加好友学习！
公众号名称：三丰杂货铺



![在这里插入图片描述](https://img-blog.csdnimg.cn/20200529103009878.gif#pic_center)

