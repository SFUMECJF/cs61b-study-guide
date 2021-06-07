

##  1.2 

###  exercise

####  C-2

![image-20210607085712782](https://gitee.com/umecjf/figures/raw/master/image-20210607085712782.png)

####  B-1

没有error用T代表的话，则TTFFT

###  Discission

关于最后一题，

3 Writing Your First Program 

两种形式写斐波娜砌数列：

```java
public static int fib(int n) {
 if (n <= 1) {
 return n;
 } else {
 return fib(n - 1) + fib(n - 2);
 }
 }
```

第一种方法是很常见的一种写法，只要做大量的递归的习题，就可以想到。就是指定想要的状态，从这个状态一直倒退到基线的感觉。

第二种方法比较少见，将相加和迭代的运算作为一个表达式放到`fib2(n, k + 1, f1, f0 + f1);`函数的参数里了，另外是从基线往上运算的感觉。

```java
public static int fib2(int n, int k, int f0, int f1) {
 if (n == k) {
 return f0;
 } else {
 return fib2(n, k + 1, f1, f0 + f1);
 }
 }
```





