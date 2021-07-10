

[TOC]



##  1

```shell
.\StdDraw.java:299: 错误: 编码GBK的不可映射字符
 *  You save your image to a file using the <em>File 鈫? Save</em> menu option.
                                                      ^
.\StdDraw.java:433: 错误: 编码GBK的不可映射字符
 *       from (0.5, 鈥?&infin;) to (0.5, &infin;) may not be visible even in the
                     ^
.\StdDraw.java:1190: 错误: 编码GBK的不可映射字符
     * (<em>x</em><sub><em>n</em>鈥?1</sub>, <em>y</em><sub><em>n</em>鈥?1</sub>).
                                  ^
.\StdDraw.java:1190: 错误: 编码GBK的不可映射字符
     * (<em>x</em><sub><em>n</em>鈥?1</sub>, <em>y</em><sub><em>n</em>鈥?1</sub>).
                                                                      ^
.\StdDraw.java:1219: 错误: 编码GBK的不可映射字符
     * (<em>x</em><sub><em>n</em>鈥?1</sub>, <em>y</em><sub><em>n</em>鈥?1</sub>).
                                  ^
.\StdDraw.java:1219: 错误: 编码GBK的不可映射字符
     * (<em>x</em><sub><em>n</em>鈥?1</sub>, <em>y</em><sub><em>n</em>鈥?1</sub>).
                                                                      ^
6 个错误

```

解决方案：

```shell
javac -encoding utf-8 NBody.java
java NBody 157788000.0 25000.0 data/planets.txt
```





### 拷贝构造

`Dog fido = new Dog("Fido", "Poodle", 1);`

1. JVM创造空构造函数，分配足够容纳所有变量的空间，但是是默认值。

   ![constructor1](https://sp18.datastructur.es/materials/proj/proj0/constructor1.png)

2. JVM执行构造函数

#### 创造两个构造函数

```java
public Dog(String name, String breed, int age) {
    System.out.println("_name: " + _name + ", _breed: " + _breed + ", _age: " + _age);
    _name = name;
    _breed = breed;
    _age = age;
}

public Dog(String name, String breed1, String breed2, int age) {
    Dog dog = new Dog(name, breed1 + breed2, age);
}

// 正确的构造函数
public Dog(String name, String breed1, String breed2, int age) {
    this(name, breed1 + breed2, age);
}

public Dog(String name, String breed1, String breed2, int age) {
    _name = name;
    _breed = breed1 + breed2;
    _age = age;
}


// 调用：
Dog tommy = new Dog("Tommy", "Poodle", "Golden Retriever", 1);
```



![constructor5](https://sp18.datastructur.es/materials/proj/proj0/constructor5.png)







## 互相交流


读者你好！如果你对本文内容感兴趣，我十分希望能够和你互相学习，可以扫码和我联系！一起进步



![在这里插入图片描述](https://img-blog.csdnimg.cn/20200529103009878.gif#pic_center)

