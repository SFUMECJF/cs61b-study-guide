

[TOC]

关于scope的理解，类内部的数据和函数：public和protected,private

static和no-static

对于类内部的类，这两个关系：

##  1  discussion

第一题那个this到底怎么理解？

如果两个属性都是static的，那么实例的属性和static前期是一样的嘛？

下方的代码，我们可以知道：如果类内部的属性都是static，那么只有一块地址是储存这两个变量的，无论多少个实例，无论通过类还是实例调用它，都会是同一个变量。

```java
public class Shock {
 public static int bang;
 public static Shock baby;
 public Shock() {
 this.bang = 100;
 }
 public Shock (int num) {
 this.bang = num;
 baby = starter();
 this.bang += num;
 }
 public static Shock starter() {
 Shock gear = new Shock();
 return gear;
 }
 public static void shrink(Shock statik) {
 statik.bang -= 1;
 }
 public static void main(String[] args) {
 Shock gear = new Shock(200);
 System.out.println(gear.bang); //300
     Shock test = new Shock();
     System.out.println(gear.bang); 
 shrink(gear); shrink(starter());
 System.out.println(gear.bang); //99
    Shock test2 = new Shock();
 System.out.println(gear.bang); 
 System.out.println(gear.bang); 
 System.out.println(gear.bang); 
 }
 }
```

####  第2题

主要是作用域，因为same是实例本身的一个属性，在if判断里又创建了一个same变量，所以当结束作用域后，明白这个same调用的是哪个。

```java
public Horse same(Horse horse) {
	 if (same != null) {
	 Horse same = horse;
	 same.same = horse;
	 same = horse.same;
	 }
	 return same.same;
	 }
```

###  第3题

不难，放java visualizier里看看就行。

传函数，传的是引用，如果没有对引用里的值更改，那么是不会改变的。

```java
public class Foo {
 public int x, y;

 public Foo (int x, int y) {
 this.x = x;
 this.y = y;
 }

 public static void switcheroo (Foo a, Foo b) {
 Foo temp = a;
 a = b;
 b = temp;
 }

 public static void fliperoo (Foo a, Foo b) {
 Foo temp = new Foo(a.x, a.y);
 a.x = b.x;
 a.y = b.y;
 b.x = temp.x;
 b.y = temp.y;
 }

 public static void swaperoo (Foo a, Foo b) {
 Foo temp = a;
 a.x = b.x;
 a.y = b.y;
 b.x = temp.x;
 b.y = temp.y;
 }

 public static void main (String[] args) {
 Foo foobar = new Foo(10, 20);
 Foo baz = new Foo(30, 40);
 switcheroo(foobar, baz); //foobar.x: 10 foobar.y: 20 baz.x: 30 baz.y: 40
 fliperoo(foobar, baz); //foobar.x: 30 foobar.y: 40 baz.x: 10 baz.y: 20
 swaperoo(foobar, baz); //foobar.x: 10 foobar.y: 20 baz.x: 10 baz.y: 20
 }
 }
```

###  第4题

放可视化里运行运行：

```java
public class QuikMaths {
 public static void multiplyBy3(int[] A) {
 for (int x: A) {
 x = x * 3;
 }
 }

 public static void multiplyBy2(int[] A) { int[] B = A;
 for (int i = 0; i < B.length; i+= 1) {
 B[i] *= 2;
 }
 }

 public static void swap (int A, int B ) {
 int temp = B;
 B = A;
 A = temp;
 }

 public static void main(String[] args) {
 int[] arr;
 arr = new int[]{2, 3, 3, 4};
 multiplyBy3(arr);

 /* Value of arr: {2, 3, 3, 4} */

 arr = new int[]{2, 3, 3, 4};
 multiplyBy2(arr);

 /* Value of arr: {4, 6, 6, 8} */

 int a = 6;
 int b = 7;
 swap(a, b);
 /* Value of a: 6 Value of b: 7 */
 }
 }
```

##  2  lab

lab主要练习debug，我觉得DebugExercise1.java没有bug

DebugExercise1.java重新写一下很简单的max和sum函数就可以。

DebugExercise1.java中使用resume（从该断点执行一直到下次这个断点）和条件断点（达到某条件才停止）加快调试过程。

解决bug就是找到`-387128732`把负号去掉。

#### Application: IntLists

这里主要是可以在debug的时候使用cs61b老师的插件，超级好用。理解这种`Non-destructive`和`destructive`的设计原理。

建议使用递归的方法，而不是迭代的方法，迭代的方法要创建一个新的对象用于迭代，不如递归。

### 实现两种函数

这里需要考虑nullptr，空指针。怎么办呢。特判吧。

## 微信公众号

欢迎大家关注我的个人公众号，现阶段主要总结为进入大厂总结的各类知识：Qt，C++，CMake,OpenCV等等
公众号名称：三丰杂货铺



![在这里插入图片描述](https://img-blog.csdnimg.cn/20200529103009878.gif#pic_center)

