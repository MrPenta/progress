

## 变量基本类型

1. 整型

| 类型  | 字节 |
| ----- | ---- |
| byte  | 1    |
| short | 2    |
| int   | 4    |
| long  | 8    |



2. 浮点类型

| 类型   | 字节 |
| ------ | ---- |
| float  | 4    |
| double | 8    |

> 判断一个值是不是 NaN

```java
Double.isNaN(value);
```



3. char 类型

| 转义序列 | 名称   |
| -------- | ------ |
| \b       | 退格   |
| \t       | 制表   |
| \n       | 换行   |
| \r       | 回车   |
| \\'      | 单引号 |
| \\"      | 双引号 |
| \\\      | 反斜杠 |

**注意: 转义序列会在解析代码之前得到处理, 而不是编译或运行时 **

4. boolean

| 类型  |      |
| ----- | ---- |
| true  |      |
| false |      |





## 常量

> 使用 final 关键字定义, 只能被赋值一次, 不能更改

```java
final double PRICE = 2.54 ;
```



## 运算符

优先级由高向低

| 运算符                                            | 结合性   |
| ------------------------------------------------- | -------- |
| []  .  ()                                         | 从左向右 |
| !  ~  ++  +(正号)  -(负号)  () (强制类型转换) new | 从右向左 |
| *  /  %                                           | 从左向右 |
| +  -                                              | 从左向右 |
| <<  >>  >>>                                       | 从左向右 |
| <  <=  >  >=  instanceof                          | 从左向右 |
| ==  !=                                            | 从左向右 |
| &                                                 | 从左向右 |
| ^                                                 | 从左向右 |
| \|                                                | 从左向右 |
| &&                                                | 从左向右 |
| \|\|                                              | 从左向右 |
| ? :                                               | 从右向左 |
| =  +=  -=  *=  /=  %=  &= \|=  ^=  <<=  >>=  >>>= | 从右向左 |



### 枚举类型

> 取值只能是集合内的某个值, 可以避免错误的值或不规范的值

```java
enum Size { SMALL , MEDIUM , LARGE , EXTRA . LARCE }
Size s = Size . MEDIUM ;
```



## 字符串

Java没有字符串类型, 提供了一个预定义类 `String`

### 拼接

使用 `+` 拼接, 或者String.join()

### 不可变字符串

字符串是不可变的, 也就是说不能只改变字符串中的某一个字符, 只能重新生成一个字符串. 这样的缺点是会降低运行效率, 好处是字符串可以在多个变量间复用

### 检测字符串是否相等

使用 `equals` 方法, 返回true / false		

```java
s.equals(t)
```



## 数组

> 声明数组

```java
int[] a = new int[100]
// 或
int a[] = new int[100]
```

访问数组之外的下标, 会引发 `array index out of bounds` 异常



> 数组拷贝

```java
Arrays.copyOf()
```



## 对象与类

面向对象与面向过程的区别: 面向对象的方式程序组织更合理, 容易模拟和抽象现实世界, 也更容易排查错误. 

面向对象的方式更适合解决大规模的问题

### 类

类是构造对象的模板

### 封装

隐藏具体实现

### 对象的三个特征

* 行为
* 状态
* 标识

> 一般来说, 一个事物的名词特征, 对应着对象的属性, 而动词特征, 对应着对象的方法
>
> 如狗的颜色, 名字, 品种, 是这个狗的属性, 狗的跑, 叫, 吃, 是狗的行为

### 类之间的关系

* 依赖
* 聚合
* 继承

如果一个类的方法操纵另一个类的对象， 我们就说一个类依赖于另一个类 。即 “uses - a ” 关系 

如果一个类中包含另一个对象, 则是聚合关系, 即 " has - a " 

如果一个类在另一个类的基础上进行了细化, 扩展, 则是继承关系, 即 " is - a"



### 定义类的方式

```java
class ClassName {
    field;
    
    getField(){}
    
    setField(){}
}
```

> 建议: 数据只通过访问器进行读取和修改
>
> 如果需要返回一个可变对象的引用 ， 应该首先对它进行克隆



`static` 修饰的属性或方法将在类的所有实例中共享

> 定义构造函数, 构造函数必须和类同名

```java
class Test {
    // 构造函数
	public Test() {
		
	}
}
```



### 方法参数

* 按值调用 (call by value)
* 按引用调用 (call by reference)

**注意:**

* 一个方法不能修改一个基本数据类型的参数 （ 即数值型或布尔型 ）。
* 一个方法可以改变一个对象参数的状态。
* 一个方法不能让对象参数引用一个新的对象。



### 重载

如果多个方法有相同的名称, 不同的参数, 就构成了 **重载**, 编译器会根据参数判断具体执行哪个方法. 

方法名和参数构成了`函数签名` , 返回值不是函数签名的一部分

如果没有提供任何构造器, 系统会提供一个默认的构造器; 但是如果定义了一个构造器, 则不会再提供构造器



### 包

包类似目录一样, 可以将类组织起来, 方便管理. 

建议将公司的域名逆序作为包名, 如: 公司域名为`sun.com`, 则对应的包名为: `com.sun`

如果引用了不同包中相同类名的类, 需要在类名前加上完整的包名

> 静态导入类, 可以不需要类名直接使用类中的静态方法

```java
import static java.lang.System.*;
out.println("Goodbye , World !") ;
```



### 类设计技巧

1. 一定要保证数据私有
2. 一定要对数据初始化
3. 尽量少使用基本类型
4. 不是所有的域都需要访问器和更改器
5. 单一职责
6. 类名和方法名要见名知意
7. 优先使用不可变的类 ( 可以保证线程安全性 )



## 继承

 #### 语法

使用 `extends` 关键字描述

```java
public class Manager extends Employee
{
	// 添加方法和域
}
```





























