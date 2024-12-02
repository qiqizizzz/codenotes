# 附录 一些常见的API

## 1. JOptionPane

[Java Swing 对话框JOptionPane的基本使用 - CSDN App](http://t.csdnimg.cn/MtO1d)

常用的四种消息提示框方法

| 方法                 | 功能             |
| -------------------- | ---------------- |
| showMessageDialog(); | 消息对话框       |
| showConfirmDialog(); | 选择对话框       |
| showOptionDialog();  | 自定义选择对话框 |
| showInputDialog();   | 输入对话框       |



## 2.Object类

Object的构造方法:空参构造。

Object的成员方法：

| 方法名                                    | 说明                                     |
| ----------------------------------------- | ---------------------------------------- |
| public String toSting()                   | 返回对象的字符串表现形式                 |
| public static boolean equals(Object obj)  | 比较两个对象是否相等                     |
| public static boolean isNull(Object obj)  | 判断对象是否为null，为null返回true，反之 |
| public static boolean nonNull(Object obj) | 判断对象是否为null，跟isNull的结果相反   |
| protected Object clone(int a)             | 对象克隆                                 |

**1.toString()方法**

```java
String s="abc"; //String类中有重写的ToString函数
StringBuild ab=new StringBuild("abc");   //StringBuild是自己创造的一个类，没有重写ToString函数


System.out.println(s.equals(sb));  //返回false
//因为equals方法是被s调用的，而s是字符串
//所以equals要看String类中的
//字符串中的equals方法，先判断参数是否为字符串
//如果是字符串，再比较内部的属性
//但是如果参数不是字符串，直接返回false


System.out.println(sb.equals(s));  //返回false
//因为equals方法是被sb调用的，而sb是StringBuild中的equals方法
//那么在StringBuild当中，没有重写equals方法
//使用的是Object中的
//在Object当中默认是使用==号比较两个对象的地址值
//而这里的s和sb记录的地址值是不一样的，所以结果返回false
```

**2.克隆**

[【浅克隆和深克隆 - CSDN App】](https://blog.csdn.net/ChineseSoftware/article/details/122942803?sharetype=blogdetail&shareId=122942803&sharerefer=APP&sharesource=2301_81250551&sharefrom=link)

浅克隆(浅克隆)：不管对象内部的属性是从基本数据类型还是引用数据类型，都完全拷贝过来。

> Object里面的clone()是浅克隆。

深克隆(深拷贝)：基本数据类型拷贝过来，字符串复用，引用数据类型会重新创建新的。

通过重写Clone()方法来替换克隆出来的**地址值**来实现深克隆。

> Java 如果需要实现深克隆，可以通过覆盖Object类的 **clone()** 实现，也可以通过序列化(Serialization)等方式来实现。
>
> 如果引用类型里面还包含很多引用类型，或者内层引用类型的类里面又包含引用类型，使用 clone 方法就会很麻烦。此时可以用序列化的方式来实现对象的深克隆。
>
> 序列化就是将对象写到流的过程，写到流中的对象是源对象的一个拷贝，而源对象仍然存在于内存中。通过序列化实现的拷贝不仅可以复制对象本身，而且可以复制其引用的成员对象，因此通过序列化将对象写到一个流中，再从流里将其读出来，可以实现深克隆。需要注意的是能够实现序列化的对象其类必须实现 Serializable 接口，否则无法实现序列化操作。

## 3.runtime类

| 方法名                              | 说明                                     |
| ----------------------------------- | ---------------------------------------- |
| public static Runtime getRuntime()  | 当前系统的运行环境对象                   |
| public void exit(int status)        | 停止虚拟机                               |
| public int availableProcessors()    | 获得cPu的线程数                          |
| public long maxMemory()             | JVM能从系统中获取总内存大小(单位byte)    |
| public long totalMemory()           | JVM已经从系统中获取总内存大小（单位byte) |
| public long freeMemory()            | JVM剩余内存大小（单位byte)               |
| public Process exec(String command) | 运行cmd命令                              |

```java
Runtime.getruntime.exec("shutdown -s -t 3600");   //3600秒后关机
Runtime.getruntime.exec("shutdown -a");
//cmd命令
//shutdown :关机

//加上下列参数才能执行
//-s:默认在1分钟之后关机
//-s -t指定时间:指定关机时间
//-a :取消关机操作
//-r:关机并重启
```

## 4.System类

| 方法名                                                       | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| public static void exit(int status)                          | 终止当前运行的Java虚拟机     |
| public static long currentTimeMillis()                       | 返回当前系统的时间毫秒值形式 |
| public static void arraycopy(数据源数组，起始索引，目的地数组，起始索引，拷贝个数) | 数组拷贝                     |

## 5.String类

方法略。

**注意：**

如果很多字符串拼接(即用"+"这个符号)，不要直接加。这会在底层创建多个对象，浪费时间，浪费性能。

**1.字符串拼接的底层原理**

如果没有变量参与，都是字符串直接相加，编译之后就是拼接之后的结果，会复用串池中的字符串。如果有变量参与，每一行拼接的代码，都会在内存中创建新的字符串，浪费内存。

**2.StringBuilder提高效率原理图**

所有要拼接的内容都会往StringBuilder中放
不会创建很多无用的空间，节约内存

## 6.StringBuilder类

一个容器，创建之后里面的**内容是可变**的，可以提高字符串的操作效率。(可以使用链式编程)

| 方法名                                | 说明                                                |
| ------------------------------------- | --------------------------------------------------- |
| public StringBuilder()                | 创建一个空白可变字符串对象，不含有任何内容          |
| public StringBuilder(String str)      | 根据字符串的内容，来创建可变字符串对象              |
| public StringBuilder append(任意类型) | 添加数据，并返回对象本身                            |
| public StringBuilder reverse()        | 反转容器中的内容                                    |
| public int lenth()                    | 返回长度(字符出现的个数)                            |
| public String toString()              | 通过toString()就可以实现把StringBuilder转换为String |

> 打印StringBuilder时是属性值，不是地址值(默认没有字符串时也是如此)。

## 7.StringJoiner类

一个容器，创建之后里面的**内容是可变**的，可以提高字符串的操作效率，而且代码编写特别简洁(但是市场上面很少有人用)。

| 方法名                                            | 说明                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| public StringJoiner(间隔符号)                     | 创建一个StringJoiner对象，指定拼接时的间隔符号               |
| public StringJoiner(间隔符号，开始符号，结束符号) | 创建一个StringJoiner对象，指定拼接时的间隔符号，开始符号，结束符号 |
| public StringJoiner add(添加的内容)               | 添加数据，并返回对象的本身                                   |
| public int lenth()                                | 返回长度(字符出现的个数)                                     |
| public String toString()                          | 返回一个字符串(该字符串就是拼接之后的结果)                   |

## 8.BigInteger类

> 主要用于储存较大的数字。

| 方法名                                                 | 说明                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| public BigInteger(int num,Random rnd)                  | 获取随机大整数，范围:[0~2的num次方-1]                        |
| public BigInteger(String val)                          | 获取指定的大整数(字符串必须是整数，否则会报错)               |
| public BigInteger(String val,int radix)                | 获取指定进制的大整数(字符串中的数字必须要跟进制吻合)         |
| public static BigInteger valueOf(long val)             | 静态方法获取BigInteger的对象，内部有优化(能表示的范围较小，在-16~16之间可以节约内存) |
| public BigInteger add(BigInteger val)                  | 加法                                                         |
| public BigInteger subtract(BigInteger val)             | 减法                                                         |
| public BigInteger multiply(BigInteger val)             | 乘法                                                         |
| public BigInteger divide(BigInteger val)               | 除法，获取商                                                 |
| public BigInteger[] divideAndRemainder(BigInteger val) | 除法，获取商和余数                                           |
| public boolean equals(Object x)                        | 比较是否相同                                                 |
| public BigInteger pow(int exponent)                    | 次幂                                                         |
| public BigInteger max/min(BigInteger val)              | 返回较大值/较小值                                            |
| public int intValue(BigInteger val)                    | 转为int类型整数，超出范围数据有误                            |

**关于Biglnteger构造方法**
1.如果BigInteger表示的数字没有超出long的范围，可以用静态方法获取。

2.如果BigInteger表示的超出long的范围，可以用构造方法获取。

3.对象一旦创建，BigInteger内部记录的值不能发生改变。

4.只要进行计算都会产生一个新的BigInteger对象。



# 一、Java基础

## 0.Java语言规范

[Java语言规范](https://docs.oracle.com/javase/specs/)

## 1.java需要注意的几点

> Java不使用逗号运算符

### 1.1 Java区分大小写

如果出现了大小写拼写错误(如，将main拼写成Main)，程序将无法运行。

### 1.2 访问修饰符

如关键字public被称为访问修饰符，用于控制程序的其他部分对这段代码的访问级别。

### 1.3 类

Java程序中的所有内容都必须放在类中，且Java中的所有函数都是某个类的方法(标准术语将其称为方法，而不是成员函数)。

- 类名要求

1.类名必须以字母开头，后面可以跟字母与数字的任意组合。长度上基本没有限制。但是不能使用Java保留字(例如，public或class)作为类名。

2.标准命名约定为:类名是以大写字母开头的名词(类名FirstSample就使用了这个命名约定)。如果名字由多个单词组成，每个单词的第一个字母都应该大写。这种在一个单词中间使用大写字母的方式有时称为骆驼命名法。

3.**源代码的文件名必须与公共类的类名相同**，并用.java作为扩展名。

### 1.4 main方法

每个Java应用都必须有一个main方法。

声明格式:

```java
public class ClassName
{
	public static void main(String[] args)
	{
		program statements
	}
}
```

### 1.5 println方法与print方法

```java
System.out.println("We will not use 'Hello,World!'");
System.out.println();                //不带参数的println方法表示只打印一个空行
```

在这个示例中，println方法接收一个字符串参数，这个方法将这个字符串参数显示在控制台上。然后，终止这个输出行，所以每次调用println都会在新的一行上显示输出。且Java与C++/C一样，都使用双引号界定字符串。

```java
System.out.print("Hello");          //print方法不在输出之后增加换行符 
//则下一个输出将紧跟在字母“o”之后。
```

### 1.6 注释

与大多数程序设计语言一样，Java中的注释不会出现在可执行程序中。

```java
//is this too cute? 
                               //1
/* Yes!                        //2
*/

/**
...
*/                             //3
```

第一种和第二种与C++相同。

第三种注释可以用来自动生成文档。这种注释以/** 开始，以

*/结束。

### 1.7 数据类型

在Java中，所有数据类型的大小都与平台无关。

> 整型

| 类型  | 存储需求 | 取值范围                                           |
| ----- | -------- | -------------------------------------------------- |
| int   | 4字节    | -2147 483 648~2147 483 647(略高于20亿)             |
| short | 2字节    | -32 768~32 767                                     |
| long  | 8字节    | -9223 372 036 854 775 808~9223 372 036 854 775 807 |
| byte  | 1字节    | -128~127                                           |

byte和short类型主要用于特定的应用场合，例如，底层的文件处理或者存储空间有限时的大数组。

注意：Java没有无符号(unsigned)形式的int、long、short或byte类型。

> 浮点类型

| 类型   | 存储需求 | 取值范围                                            |
| ------ | -------- | --------------------------------------------------- |
| float  | 4字节    | 大约+-3.402 823 47x10^38(6~7位有效数字)             |
| double | 8字节    | 大约+-1.797 693 134 862 315 70x10^308(15位有效数字) |

float类型的数值有一个后缀F或(例如，3.14F)。没有后缀F的浮点数值总是默认位double类型。可选地，也可以在double数值后面添加后缀D或d(例如，3.14D)。

> char类型

char类型的字面量值要用单引号括起来。(如'A')

> boolean类型

boolean类型有两个值:false和true，用来判定逻辑条件。**整型值和布尔值之间不能进行相互转换。**

### 1.8 变量与常量

与大多数程序设计语言相比，Java中"字母" ”数字“和"货币符号"的范围更大。

字母是指一种语言中表示字母的任何Unicode字符。(如π这种特殊字符)

```java
var vacationDays=12;
//对于局部变量，如果可以从变量的初始值推断出它的类型，就不再需要声明类型。
//只需使用关键字var而无须指定类型，
```

- **关键字final**

在Java中，可以用关键字final指示常量。

```java
final double CM_PER_INCH=2.54;
```

关键词final表示这个变量只能被赋值一次。一旦赋值，就不能再更改了。

```java
//类常量
public statici final double CM_PER_INCH=2.54;
```

注意:类常量的定义位于main方法之外。这样一来，同一个类的其他方法也可以使用这个常量。

> C++注释：const是Java保留的关键字，但目前并没有使用。在Java中，必须使用final声明常量。

- 枚举类型

```java
enum Size{SMALL,MEDIUM,LARGE,EXTRA_LARGE};
Size s=Size.MEDIUM;
```

### 1.9 使用数学函数

Math类中包含你可能会用到的各种数学函数。

```java
double y=Math.sqrt(x);
```

提示：不必在数学方法名和常量名前添加前缀“Math”，只要在源文件最上面加上下面这行代码就可以了。

```java
import static java.lang.Math.*;
System.out.println("The square root of \u03C0 is" +sqrt(PI)); 
```

### 1.10 switch表达式

case标签还可以是字符串或枚举类型常量。

```java
//1
String seasonName=switch (seasonCode)
{
	case 0->"Spring";
	case 1->"Summer";
	case 2->"Fall";
	case 3->"Winter";
	default ->"???";
}
//2
```

使用整数或String操作数的switch表达式必须有一个default，因为不论操作数值是什么，这个表达式都必须生成一个值。

case 标签可以是:

- 类型为char、byte、short 或 int 的常量表达式
- 枚举常量
- 字符串字面量
- 多个字符串，用逗号分隔



注意swtich表达式中的**yield关键字**。与 break 类似，yield会终止执行。但与break不同的是，yield 还会生成一个值，这就是表达式的值。
要在 switch 表达式的一个分支中使用语句而不想有直通行为，就必须使用大括号和yield, 如表中示例所示，这个例子将为一个分支增加日志语句：

```java
case "Spring" ->
（
	System.out.println("spring time!");
	yield 6;
}
```



### 1.11 substring方法

String类的substring方法可以从一个较大的字符串提取出一个子串。

```java
String greeting="Hello";
String s=greeting.substring(0,3);
//会创建一个由字符"Hel"组成的字符串
```

substring方法的第二个参数是你不想复制的第一个位置。

### 1.12 静态join方法

把多个字符串放在一起，用一个界定符分隔。

```java
String all=String.join("/","S","M","L","XL");
//all is the string "S/M/L/XL"
```

### 1.13 repeat方法

```java
String repeated="Java".repeat(3); //repeated is "JavaJavaJava"
```

### 1.14 检测字符串是否相等

```java
s.equals(t);
//若字符串s与t相等，则返回true;否则，返回false。
//注意:s与t可以是字符串变量，也可以是字符串字面量。如下:
"Hello".equals(greeting)
```

要想检测两个字符串是否相等，而不区分大小写，可以用equalsIgnoreCase方法。

```java
"Hello".equalsIgnoreCase("hello")
```

### 1.15 阅读联机API文档

[API文档](https://docs.oracle.com/en/java/javase/17/docs/api)

API（Application Programming Interface，应用程序编程接口）是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节。

### 1.16 构建字符串

如果需要用**许多小字符串**来构建一个字符串，可以采用以下步骤。首先，构建一个空的字符串构建器:

```java
StringBuilder builder = new StringBuilder()；
当每次需要添加另外一部分时，就调用append方法。
builder.append (ch); //appends a single character
builder.append (str); //appends a string
字符串构建完成时，调用 toString 方法。你会得到一个String对象，其中包含了构建器中的字符序列。
String completedString = builder.toString();
```

> StringBuilder类中最重要的方法:

- StringBuilderO

  构造一个空的字符串构建器。

- int length!)

  返回构建器或缓冲器中的代码单元个数。

- StringBuilder append(String str)

  追加一个字符串并返回 this.

- StringBuilder append(char c)

  追加一个代码单元并返回 this。

- StringBuilder appendCodePoint(int cp)

  追加一个码点，将它转换为一个或两个代码单元并返回 this。

- void setCharAtfint ir char c)

  将第i个代码单元设置为c

- StringBuilder insert(int offset, String str)

  在offset 位置插入一个字符串并返回 this.

- StringBuilder insert(int offset, char c)

  在 offset 位置排人一个代码单元井返回 this。

- StringBuilder delete(int startIndex, int endindex)

  删除从 startIndex到endindex-1的代码单元并返回this。

- String toString()

  返回一个字符串，其数据与构建器或缓冲器内容相同。

  

  5557


### 1.17 文本块

利用Java 15新增的文本块(text block)特性，可以很容易地提供跨多行的字符串字面量。

文本块以"""开头 (这是开始"""), 后面是一个换行符，并以另一个"""结尾 (这是结束"""):

```java
String greeting = """
Hello
World
""";

//文本块比相应的字符串字面量更易于读写:
"Hello\nWorld\n"
```

 ### 1.18 var关键字

如果可以从变量的初始值推导出它们的类型, 那么可以用**var关键字**声明局部变量，而无须指定类型。例如，可以不这样声明：

```java
Employee harry = new Employee("Harry Hacker",50000,1989,10,1);
```

只需要写为：

```java
var harry= new Employee ("Harry Hacker",50000,1989,10,1);
```



## 2.输入与输出

### 2.1 读取输入

要想读取控制台输入,首先需要构造一个与“标准输入流" System.in关联的 Scanner对象。

```java
Scanner in=new Scanner(System.in);
```

现在,就可以使用Scanner类的各种方法读取输入了。

```java
System.out.print("What is your name?");
String name=in.nextline();                 //nextLine方法读取一行输入
String firstName=in.next();                //next方法读取一个单词

System.out.print("How old are you?");
int age=in.nextInt();                      //nextInt方法读取一个整数
类似地，nextDouble方法可以读取下一个浮点数...
```

最后，在程序的最前面添加一行代码：

```java
import java.util.*;
```

### 2.2 格式化输出

1.沿用C语言函数库中的古老约定

```java
System.out.printf("%8.2f",x);
```

2.String.format方法

可以使用静态的String.format方法创建一个格式化的字符串，而不打印输出：

```java
String message=String.fomatl("Hello,%s.Next year,you'll be %d",name,age+1);
```

### 2.3 文件输入与输出

- 要想读取一个文件，需要构造一个 Scanner对象，如下所示：

```java
Scanner in = new Scanner(Path.of ("myfile.txt"),StandardCharsets.UTF_8);
//如果文件名中包含反斜线符号，记住要在每个反斜线之前再加一个额外的反斜线转义:"c:\\mydirectory\\myfile.txt"。
```

- 要想写入文件，需要构造一个 PilntWriter 对象: 在构造器 ( comtructor) 中，需要提供文件名和字符编码：

```java
Printwriter out =new PrintWriter("myfile.txt", StandardCharsets.UTF_8);
//如果文件不存在，则创建该文件。可以像输出到System.out一样使用print、printlh以及printf命令
```

 ## 3.大数

> 用于处理基本的整数和浮点数精度不足的情况，存在于java.math包中的两个有用的类:**BigInteger**(实现任意精度的整数运算)和**BigDecimal**(实现任意精度的浮点数运算)。

1.将一个普通的数转换为大数

```java
BigInteger a=BigInteger.valueOf(100);

//对于更长的数
BigInteger reallyBig=new BigInteger("234243222225555555555555554839537453953535374");
```

2.add和multiply方法

注：不能用我们熟悉的算术运算符(如:+和*)来组合大数。

```java
BigInteger c=a.add(b);                                      //c=a+b;
BigInteger d=c.multiply(b.add(BigInteger.valueOf(2)));      //d=c*(b+2)
```

## 4.数组

一种创建数组对象并同时提供初始值的简写形式：

```java
int[] smallPrimes={2,3,5,7,11,13};

//最后一个值后面允许有逗号，如下:
String[] authors=
{
	"Jame Gosling",
	"Bill Joy",
	"Guy Steele",
	
}
```

### 4.1 for each循环

```java
for(variable : collection) statement
```

它将给定变量 (variable) 设置为集合中的每一个元素，然后执行语句 ( statement)(当然，也可以是语句块)。collection 表达式必须是一个数组或者是一个实现了Iterable 接口的类对象 (例如 ArrayList)。

例如：

```java
for(int element :a)
	System.out.println(element);
//会打印数组a的每一个元素，一个元素占一行。
//element是临时变量，名称随意
```

### 4.2 拷贝数组

```java
int[]copieLuckyNumbers=Arrays.copyOf(luckNumbers,luckyNumbers.lenth);
//第二个参数是新数组的长度。
```

### 4.3 random方法

Math.random方法将返回一个0到1之间(包含0、不包含1)的随机浮点数。用n乘以这个浮点数，可以得到0到n-1之间的一个随机数。

```java
int r=(int)(Math.random()*n);
```



# 二、Java面向对象程序设计

## 1.类基础

在 Java 中，最简单的类定义形式为：

```java
class ClassName
{
	field1
	field2
	...
	constructor1
	constructor2
	...
	method1
	method2
	...
}
```

> Java 中构造器的工作方式与 C++ 中相同。但是，要记住所有 Java 对象都是在堆中构造的，构造器总是结合new操作符一起使用电.C++ 程序员最易犯的错误就是忘记 **new 操作符**。

### 1.1 main方法

每一个类都可以有一个main方法。**这是为类增加演示代码的一个技巧**。例如，可以在Employee类中添加一个main方法：

```java
class Employee
{
	public Employee(String n,double s,int year,int month,int day)
	{
		name=n;
		salary=s;
		hireDay=localDate.of(year,month,day);
	}
	public static void main(String[] args) // unit test
	{
	var e= new Employee("Romeo", 50000,2003,3,31);
	e.raiseSalary(10);
	System.out.println(e.getName()+" "+ e.getSalary());
	}
}
```

要看 Employee 类的演示，只需要执行

> java Employee

如果 Employee 类是一个更大的应用的一部分，那么可以使用以下命令运行这个应用：

> java Application

Employee 类的 main 方法永远不会执行。

### 1.2 方法参数

Java程序设计语言总是采用按值调用。在Java中，对象引用是按值传递的。

下面来总结在 Java 中对方法参数能做什么和不能做什么：

- 方法不能修改基本数据类型的参数（即数值型或布尔型）。

- 方法可以改变对象参数的状态。

- 方法不能让一个对象参数引用一个新对象。

```java
public class App {
    public static void main(String[] args) 
    {
    //Test 1:Methods can't modify numeric parameters
       System.out.println("Testing tripleValue:");
       double percent=10;
       System.out.println("Before:percent="+percent);
       tripleValue(percent);
       System.out.println("After:percent="+percent);

	//Test 2:Methods can change the state of object parameters
       System.out.println("\nTesting tripleSalary");
       var harry=new Employee("Harry",50000);
       System.out.println("Before:salary="+harry.getSalary());
       tripleSalary(harry);
       System.out.println("After:salary="+harry.getSalary());

	//Test 3:Methods can't attach new object to object parameters
       System.out.println("\nTesting swap:");
       var a=new Employee("Alice",70000);
       var b=new Employee("Bob",60000);
       System.out.println("Before:a="+a.getName());
       System.out.println("Before:b="+b.getName());
       swap(a,b);
       System.out.println("After:a="+a.getName());
       System.out.println("After:b="+b.getName());
    }

    public static void tripleValue(double x)
    {
        x=3*x;
        System.out.println("End of method:x="+x);
    }

    public static void tripleSalary(Employee x)
    {
        x.raiseSalary(200);
        System.out.println("End of method:salary="+x.getSalary());
    }

    public static void swap(Employee x,Employee y)
    {
        Employee temp=x;
        x=y;
        y=temp;
        System.out.println("End of method:x="+x.getName());
        System.out.println("End of method:y="+y.getName());
    }
}
class Employee{
    private String name;
    private double salary;

    public Employee(String n,double s)
    {
        name=n;
        salary=s;
    }

    public String getName()
    {
        return name;
    }

    public double getSalary()
    {
        return salary;
    }

    public void raiseSalary(double byPercent)
    {
        double raise=salary*byPercent/100;
        salary+=raise;
    }
    
}
```

### 1.3 调用构造器时的具体处理步骤：

1. 如果构造器的第一行调用了另一个构造器，则基于所提供的参数执行第二个构造器。
2. 否则，
   a) 所有实例字段初始化为其默认值 (0、false或 null）。
   b) 按照在类声明中出现的顺序，执行所有字段初始化方法和初始化块。

3. 执行构造器主体代码。



## 2.继承

使用关键字**extends**表示继承。

同时，关键字super是一个指示编译器调用超类方法的特殊关键字。

### 2.1 特殊的super语法

> 相当于C++中的初始化列表语法

```java
public Manager(String name,double salary,int year,int month,int day)
{	
	super(name,salary,year,month,day);
	bonus=0;
}
//manager是Employee的子类
```

这里的super是“调用超类Employee中带有n、s、year、month和day参数的构造器”的简写形式。

 

### 2.2 instanceof检测

如果所有的子类都有相同的相等性语义，则可以使用 instanceof检测：

```java
if(!(otherObject instanceof ClassName other))return false;
```

也可以用instanceof检测一个对象是否实现了某个特定的接口:

```java
if(anObject instancof Comparable){...}
```



### 2.3 Override标记

```java
@Override public boolean equals(Object other)
```



## 3.对象包装器

有时，需要将int这样的基本类型转换为对象。所有的基本类型都有一个与之对应的类。例如，Integer对应基本类型 int。通常，这些类称为包装器(wrapper)。

### 3.1 自动装箱

一个很有用的特性

```java
list.add(3);
//上述语句将自动转换成
list.add(Integer.valueOf(3));
```

### 3.2 自动拆箱

将一个Integer对象赋给一个int值时，将会自动拆箱。

如：

```java
int n=list.get(i);
//上述语句将自动转换成
int m=list.get(i).intValue();
```

### 3.3 参数个数可变的方法

```java
public static double max(double... value)
{
	double largest=Double.NEGATIVE_INFINTY;
	for(double v:values) if(v>largest) largest=v;
	return largest;
}
//这里的...是Java代码的一部分
```



## 4.抽象类

关键字abstract



## 5.枚举类

枚举的构造器总是私有的。

所有的枚举类型都是抽象类Enum的子类。



## 6.密封类

关键字sealed



## 7.反射

> 反射的几个功能：

- 在运行时分析类的能力。

- 在运行时检查对象，例如，编写一个适用于所有类的toString方法。

- 实现泛型数组操作代码。

- 利用 Method 对象，这个对象很像C++中的函数指针。

 

# 三、接口、lambda表达式与内部类

## 1.接口

为了让类实现一个接口，需要完成下面两个步骤:

1.将类声明为实现给定的接口。

2.对接口中的所有方法提供定义。

```java
public class Employee implements Comparable<Employee>{
    private String name;
    private double salary;
	...
}

//关键字implements
```

### 1.1 接口的属性

可以声明接口变量：

```java
Comparable x;
//接口变量必须引用实现了这个接口的一个类对象
x=new Employee(...);
```

### 1.2 默认方法

可以为任何接口方法提供一个默认实现。用default修饰符得以实现。

```java
public interface Comparable<T>
{
	default int compareTo(T other){return 0;}
}
```

> 默认方法冲突

1. 超类优先。如果超类提供了一个具体方法，同名而且有相同参数类型的默认方法会被忽略。
2. 接口冲突. 如果一个接口提供了一个默认方法. 另一个接口提供了一个同名而且参数类型相同的方法 (不论是否是默认方法)，必须覆盖这个方法来解决冲突。

 ### 1.3 定时器

> API **javax.swing.Timer** 

```java
Timer(int interval, ActionListener listener)
```

构造一个定时器. 每经过interval毫秒通知listener一次。

```java
void start()
```

启动定时器。一旦启动，定时器将调用监听器的actionPerformed

```java
void stop()
```

停止定时器。一旦停止，定时器将不再调用监听器的actionPerformed



> API **java.wat.Toolkit**

```java
static Toolkit getDefaultToolkit()
```

获得默认的工具箱。工具箱包含有关GUI环境的信息。

```java
void beep()
```

发出一声铃响。

### 1.4 对象克隆

对于每一个类，需要确定以下选项是否成立：

1. 默认的clone方法就能满足要求；

2. 可以在可变的子对象上调用clone来弥补默认的clone方法；
3. 不该使用 clone。

实际上第 3 个选项是默认选项。如果选择第1项或第2项，类必须：

1. 实现 Cloneable 接口；

2. 重新定义clone方法, 并指定public访问修饰符。

```java
//1
package clone;


public class CloneTest {
    public static void main(String[] args) throws CloneNotSupportedException
    {
        var original=new Employee("John Q.Public",50000);
        original.setHireDay(2000,1,1);
        Employee copy=original.clone();
        copy.raiseSalary(10);
        copy.setHireDay(2002,12,31);
        System.out.println("origiinal="+original);
        System.out.println("copy="+copy);
    }
}
```

```java
//2
package clone;

import java.util.Date;
import java.util.GregorianCalendar;

public class Employee implements Cloneable{
    private String name;
    private double salary;
    private Date hireDay;

    public Employee(String name,double salary)
    {
        this.name=name;
        this.salary=salary;
        hireDay=new Date();
    }

    public Employee clone() throws CloneNotSupportedException
    {
        Employee cloned=(Employee)super.clone();
        cloned.hireDay=(Date)hireDay.clone();
        return cloned;
    }

    public void setHireDay(int year,int month,int day)
    {
        Date newHireDay=new GregorianCalendar(year,month-1,day).getTime();
        hireDay.setTime(newHireDay.getTime());
    }

    public void raiseSalary(double byPercent)
    {
        double raise=salary*byPercent/100;
        salary+=raise;
    }

    public String toString()
    {
        return "Employee[name=]"+name+",salary="+salary+",hireDay="+hireDay+"]";
    }
}
```



### 1.5 标记接口

Cloneable接口是Java提供的少数标记接口之一。

标记接口不包含任何方法，它唯一的作用就是允许在类型查询中使用instanceof:

```java
if(obj instanceof Cloneable)...
```

**建议你自己的程序中不要使用标记接口。**



### 1.6 Java比较器

> [Java比较器 - CSDN App](http://t.csdnimg.cn/9w1Ax)

自然排序：java.lang.Comparable
定制排序：java.util.Comparato



## 2.lambda表达式

### 2.1 基本样式

一种简单的lambda表达式形式：参数，箭头(->)以及一个表达式。

例如：

```java
(String first,String second)->
    first.lenth()-second.lenth()
```

若表达式无法满足，则将代码放入{}中，并包含**显式的return语句**。

```java
(String first,String second)->
{
	if(first.lenth()<second.lenth()) return -1;
	else if(first.lenth()->second.lenth()) return 1;
	else return 0;
}
```



### 2.2 函数式接口

> 对于**只有一个抽象方法**的接口，需要这种接口的对象时，就可以提供一个lambda表达式。这种接口称为函教式接口。

### 2.3 方法引用

 要用::操作符分隔方法名与对象或类名。主要有 3 种情况：
1.object:;instanceMethad

2.Class::instanceMethod

3.Class::staticMethod

在第1种情况下，方法引用等价于一个lambda表达式，其参数要传递到方法。对于System.out::printin, 对象是 System.out, 所以这个方法表达式等价于 x ->System.out.println(x)。
对于第2种情况，第1个参数会成为方法的隐式参数。例如，String::compareToIgnoreCase等同于(x,y) ->x.compareToIgnoreCase(y)。
在第 3 种情况下，所有参数都传递到静态方法：Math::pow等价于(x,y) ->Math.pow(x, y)。

> 注意，只有当 lambda 表达式的体**只调用一个方法而不做其他操作**时，才能把lambda表达式重写为方法引用。

可以在方法引用中使用this参数。

### 2.4 构造器引用

构造器引用与方法引用很类似，只不过方法名为new。

### 2.5 变量作用域

1.lambda表达式可以捕获外围作用域中变量的值。

> lambda表达式中捕获的变量必须是事实最终变量。事实最终变量是指，这个变量初始化之后就不会再为它赋新值。

2.在lambda表达式中，只能引用**值不会改变**的变量。

3.在一个lambda表达式中使用this关键字时，是指创建这个lambda表达式的方法的this参数。 

4.在lambda表达式中，this的使用并没有任何特殊之处。

### 2.6 处理lambda表达式



## 3.内部类

内部类是定义在另一个类中的类。

- 内部类能直接访问外部的全部资源

- 包括任何私有的成员

- 外部是函数时，只能访问那个函数里final的变量
- 内部类不能有static方法

> 匿名类

- 在new对象的时候给出的类的定义形成了匿名类
- 匿名类可以继承某类，也可以实现某接口
- Swing的消息机制广泛使用匿名类

### 3.1  特殊语法规则

更明确地编写内部类对象的构造器

```java
//语法
outerObject.new InnerClass(construction parameters)
//例子
ActionListener listener=this.new TimePrinter();
```

> 需要注意，在外部类的作用域之外，可以这样引用内部类：
>
> ```java
> OuterClass.InnerClass
> ```

### 3.2 局部内部类

可以在一个方法中局部地定义这个类。

声明局部类时不能有访问说明符 (即public或 private)。局部类的作用域总是限定在声明这个局部类的块中。

```java
public void start()
{
	class TimePrinter implements ActionListener
	{
		public void actionPerformed(ActionEvent event)
	{
		System.out.println("At the tone,the time is "
			+Instant.ofEpochMilli(event.getwhen()));
		if(beep) Toolkit.getDefaultToolkit().beep();
	}
}

	var listener=new TimePrinter();
	var timer=new Timer(interval,listener);
	timer.start();
}
//除start方法之外，没有任何方法知道TimePrinter类的存在。
```

局部类有一个很大的优势，即对外部世界完全隐藏。



与其他内部类相比较，局部类还有另外一个优点: 它们不仅能够访问外部类的字段, 还可以访问局部变量！不过，那些局部变量必须是事实最终变量。

### 3.3 匿名内部类

```java
new SuperType(construction parameters)
{
	inner class methods and data
}
//尽管匿名类不能有构造器，但可以提供一个对象初始块化:
var count=new Person("Dracula")
{
    {initialization}
    ...
};
```

### 3.4 静态内部类

有时候，使用内部类只是为了把一个类隐藏在另外一个类的内部，**并不需要内部类有外部类对象的一个引用**。为此，可以将内部类声明为 static, 这样就不会生成那个引用。

注：只要内部类不需要访问外部类对象，就应该使用静态内部类口 有些程序员用嵌套类 (nested class) 表示静态内部类。

```java
class ArrayAlg
{
	public static class Pair
	{
		...
	}
	...
}
```

## 4. 服务加载器

> java.util.ServiceLoader`<S>` 1.6

- static `<S>` ServiceLoader`<S>` load(Class`<S>` service)

  创建一个服务加载器来加载实现了给定服务接口的类.

- Iterator`<S>` iterator()

- 生成一个以 "懒" 方式加载服务类的迭代器。也就是说，迭代器推进时才会加载类。

- Stream<ServiceLoader.Provider`<S>`> stream()  9

  返回提供者描述符的一个流, 从而可以采用懒方式加载所需类的提供者。

- Optional`<S>` findFirstf)  9

  查找第一个可用的服务提供者 (如果有)

> java.util.ServiceLoader.Provider`<S> `9

- Class<? extends S>type()

  获得这个提供者的类型。

- S get()

  获得这个提供者的实例。



# 四、异常、断言和日志

## 1.异常分类

异常对象都是派生于 Thromble类的一个类的实例中。

需要注意的是, 所有的异常都是由Throwable继承而来.，但在这个层次结构中，下一层立即分为两个分支：Error和Exception。

Error类层次结构描述了Java 运行时系统的内部错误和资源耗尽问题。你不应该抛出这种类型的对象口 如果出现了这样的内部错误，除了通知用户，并尽力妥善地终止程序之外，你几乎无能为力。这种情况很少出现。

编写Java程序时，要重点关注Exception层次结构。这个Excuption 层次结构又分为两个分支：一个分支派生于RuntimeException；另一个分支包括其他异常，不继承这个类。一般规则是：由编程错误导致的异常属于 RuntimeException ；如果程序本身没有问题,但由于I/O错误之类的问题导致的异常属于其他异常。

> Java 语言规范将派生于Error类或RuntimeException类的所有异常称为非检查型(unchecked)异常，所有其他异常称为检查型(checked)异常。

### 1.1 声明检查型异常

需要记住在遇到下面 4 种情况时会抛出异常：

- 调用了一个抛出检查型异常的方法，例如，FileInputSream构造器。
- 检测到一个错误，并且利用 throw语句抛出一个检查型异常。
- 程序出现错误.，例如，a[-1]=0会抛出一个非检查型异常 (这里会抛出ArraylndexOutOfBoundsException )。
- Java 虚拟机或运行时库出现内部错误.

如果出现前两种情况，则必须告诉使用这个方法的程序员有可能抛出异常。为什么？因为任何一个抛出异常的方法都有可能是一个死亡陷阱。如果没有处理器捕获这个异常，当前的执行线程就会终止。



如果一个方法有可能抛出多个检查型异常类型，那么就必须在方法的首部列出所有的异常类。每个异常类之间用**逗号**隔开。如下面这个例子所示：

```java
class HyAnimation
{
    ...
	public Image loadlmage(String s) throws FileNotFoundExcaption,EOFException
	{
        ...
	}
}
```



但是，不需要声明 Java的内部错误，即从error继承的异常。任何代码都有可能抛出那些异常，而我们对此完全无法控制。

类似地，也不应该声明从RuntimeException继承的那些非检查型异常。



> 注意：如果在子类中覆盖了超类的一个方法，子类方法中声明的检查型异常不能比超类方法中声明的异常更通用 (子类方法可以抛出更特定的异常，或者根本不抛出任何异常) 特别需要说明的是，**如果超类方法没有抛出任何检查型异常，子类也不能抛出任何检查型异常。**



### 1.2 如何抛出异常

```java
throw new EOFException();
//或者
var e=new EOFException();
throw e;
```



### 1.3 创建异常类

我们要做的只是定义一个派生于Exception的类，或者派生于Exception的某个子类，如lOException。

```java
//习惯做法是，自定义的这个类应该包含两个构造器，一个是默认的构造器, 另一个是包含详细描述信息的构造器
class FileFormatException extends OException
{
	public FileFormatException(){}
	public FileFormatException(String gripe)
	{
		super(gripe);
	}
}
```



> java.lang.throwable 1.0

- Throwable()

  构造一个新的Throwable对象，但没有详细的描述信息。

- Throwable(String message)

  构造一个新的Throwable对象，带有指定的详细描述信息。按惯例，所有派生的异常类都支持一个默认构造器和一个带有详细描述信息的构造器。

- String getMessage()

  获得Throwable对象的详细描述信息。



## 2.捕获异常

要想捕获一个异常，需要建立try/catch语句块。

最简单的try语句块如下所示:

```java
try
{
	code
	more code
	more code
}
catch(ExceptionType e)
{	
	handle for this type
}
```

如果 try 语句块中的任何代码抛出了catch子句中指定的一个异常类，那么

1. 程序将跳过try语句块的其余代码。

2. 程序将执行catch子句中的处理器代码。

   如果try语句块中的代码没有抛出任何异常，那么程序将跳过catch子句。

   如果方法中的任何代码抛出了一个异常，但不是catch子句中指定的异常类型，那么这个方法会立即退出 (希望它的调用者为这种类型的异常提供了catch子句)。



> 一般经验是，要捕获那些你知道如何处理的异常，而继续传播那些你不知道怎样处理的异常。
>
> 如果想传播一个异常，就必须在方法的首部添加一个throw说明符，提醒调用者这个方法可能会抛出一个异常。



### 2.1 捕获多个异常

可以为每个异常类型使用一个单独的catch子句。

```java
try
{
	code that might throw exceptions
}
catch (FileNotFoundException e)
{
	emergency action for unknown hosts
}
catch (UnknownHostException e)
{
	emergency action for unknown hosts
}
catch (IOException e)
{
	emergency action for all other I/O problems
}
```

也可以合并catch子句：(只有当捕获的异常类型彼此之间**不存在子类关系**时才需要这个特性！！！)

```java
try
{
	code that might throw exceptions
}
catch (FileNotFoundException | UnknownHostException e)
{
	emergency action for missing files and unknown hosts
}
catch (IOException e)
{
	emergency action for all other I/O problems
}
//可以用e.getMessage()得到详细的错误信息
//e.getClass().getName()得到异常对象的实际类型
```

### 2.2 finally子句

代码抛出一个异常时，就会停止处理这个方法中剩余的代码，并退出这个方法。如果这个方法已经获得了只有它自己知道的一些本地资源，而且这些资源必须清理，这就会有问题。一种解决方案是捕获所有异常，完成资源的清理，再重新抛出异常。但是，这种解决方案比较烦琐，因为需要在两个地方清理资源分配，一个是在正常的代码中，另一个是在异常代码中。finally子句可以解决这个问题。

```java
var in=new FileInputStream(...);
try
{
	code that might throw exceptions
}
catch(IOException e)
{
	show error message
}
finally
{
	in.close();
}
```



注意：

- try 语句可以只有finally子句，而没有catch子句。

- 无论在try语句块中是否遇到异常，finally子句中的in.close()语句都会执行。

- finally子句的体要用于清理资源。不要把改变控制流的语句 (return，throw，break，continue) 放在finally子句中。



### 2.3 try-with-Resources语句

```java
try(resource res=...;resource out=...)
{
	work with res
}
//这个块正常退出时，或者存在一个异常时，都会调用in.close()方法,就好像使用了finally块一样。

//例如：
try(var in=new Scanner(Path.of("in.txt"),StandardCharsets.UTF_8);
   var out=new PrintWriter("out.txt",StandardCharsets.UTF_8))
{
    while(in.hasNext())
        out.println(in.next().toUpperCase());
}
```

### 2.4 分析栈轨迹元素

可以调用Throwable类的printStackTrace方法访问栈轨迹的文本描述信息。

```java
var t=new Throwable();
var out=new StringWriter();
t.printStackTrace(new PrintWriter(out));
String description=out.toString();
```

或者是使用StackWalker类，它会生成一个StackWalker.StackFrame实例流，其中每个实例分别描述一个栈帧。可以利用以下调用迭代处理这些栈帧：

```java
StackWalker walker=StackWalker.getInstance();
walker.forEach(frame->analyze frame)
```



> API java.lang.Throwable 1.0

- Throwable(Throwable cause)  1.4

- Throwable(String message, Throwable cause) 1.4

  用给定的 cause (原因) 构造一个Throwable对象。

- Throwable initCause(Throwable cause) 1.4

  为这个对象设置原因，如果这个对象已经有原因，则抛出一个异常。返回 this。

- Throwable getCause() 1.4

  获得设置为这个对象的原因的异常对象。如果没有设置原因，则返回null。

- StackTraceElement[ ] getStackTrace() 1.4

  获得构造这个对象时调用栈的轨迹。

- void addSuppressed (Throwable t) 7

  为这个异常添加一个“被抑制”的异常。这出现在try-with-resources语句中，其中t是close方法抛出的一个异常。

- Throwable[ ] getSuppressed() 7

  得到这个异常的所有 ”被抑制”的异常。一般来说, 这些是 try-with-resources语句中close方法抛出的异常。

  > API java.lang.Exception 1.0

- Exception(Throwable cause) 1.4

- Exception(String message, Throwable cause)

  用给定的 cause(原因) 构造一个Exception对象。

  > API java Jang.RuntueException 1.0

- RuntimeException(Throwable cause) 1.4

- RuntimeException(String message, Throwable cause) 1.4

  用给定的cause(原因)构造一个RuntineException对象。

  > API java.lang.StackWalker 9

- static StackWalker getlnstance()

- static StackWalker getlnstance(StackWalker.Option option)

- static StackWalker getInstance(Set<StackWalker.Option> options)

  得到一个StackWalker实例。选项包括StackWalker.Option枚举中的 RETAIN_CLASS_REFERENCE、SHOW_HIDDEN_FRAMES和SHOW_REFLECT_FRAHES。

- forEach(Consumer<? super StackWalker.StackFrame> action)

  在每个栈帧上完成给定的动作，从最近调用的方法开始。

- walk(Function<? super Stream<StackWalker.StackFrame>, ? extends T> function)

  对栈帧流应用给定的函数，返回这个函数的结果。



## 3.使用异常的技巧

1.异常处理不能代替简单的测试。(只在异常情况下使用异常)

2.不要过分地细化异常。

3.合理利用异常层次结构。

4.不要压制异常。

5.在检测错误时，"苛刻"要比放任更好。

6.不要羞于传递异常。

7.使用标准方法报告null指针和越界异常。

8.不要向最终用户显示栈轨迹。



## 4.断言

断言 ( assertion) 机制允许你在测试期间在代码中捕人一些检查，而在生产代码中自动删除这些检查。

断言是一种用于测试和调成的战术性工具；与之不同，日志是一种用于程序整个生命周期的战略性工具。

> 关键字assert

```java
//两种形式

//1
assert condition
//2
assert condition : expression;
```



默认情况下，断言是禁用的。

可以在运行程序时用-enableassertions或-ea选项启用断言:

```java
java -ea:MyClass -ea:com.mycompany.mylib MyApp
//这条命令将为MyClass类以及com.mycompany.mylib包及其子包中的所有类打开断言
```

也可以用选项-disableassertions或-da在特定的类和包中禁用断言:

```java
java -ea:MyClass -da:com.mycompany.mylib MyApp
//这条命令将为MyClass类打开断言
    //以及为com.mycompany.mylib包及其子包中的所有类禁用断言
```

> API java.lang.ClassLoader 1.0

- void setDefaultAssertionStatus(boolean b) 1.4

  为通过这个类加载器加载的所有类 (没有显式的类或包断言状态)启用或禁用断言。

- void setClassAssertionStatus(String className,boolean b) 1.4

  为给定的类和它的内部类启用或禁用断言。

- void setPackageAssertionStatus(String packageName, boolean b) 1.4

  为给定包及其子包中的所有类启用或禁用断言.

-  void clearAssertionStatus() 1.4

  删除所有显式的类和包断言状态设置，并禁用通过这个类加载器加载的所有类的断言。



## 5.日志

### 5.1 基本日志

全局日志记录器

简单的日志记录

```java
Logger.getGlobal().info("file->open menu item selected");
```

若在适当的地方(如main的最前面)调用

```java
Logger.getGlobal().setLevel(Level.OFF);
//将会抑制所有日志
```

### 5.2 高级日志

1.对于一个简单的应用，选择一个日志记录器。

```java
Logger logger=logger.getLogger("com.mycompany.myprog");
//通过上述调用得到日志记录器

//为方便起见，最好为其增加静态字段,因为未被任何变量引用的日志记录器可能会被垃圾回收。为了防止这种情况发生，要像下面的例子中一样，用静态变量存储日志记录器的一个引用。
private static final Logger logger=logger.getLogger("com.mycompany.myprog");
```

2.默认的日志配置会把级别等于或高于INFO的所有信息记录到控制台。

```java
//以下代码确保将所有的信息记录到应用特定的一个文件中。可以将这段代码放置在应用程序的main方法中。
if(System.getProperty("java.util.logging.config.class")==null
  		&& System.getProperty("java.util.logging.config.file")==null)
{
    try
    {
        Logger.getLogger("").setLevel(Level.ALL);
        final int LOG_ROTATION_COUNT=10;
       	var handler=new FileHandler("%h/myapp.log",0,LOG_ROTATION_COUNT);
        Logger.getLogger("").addHandler(handler);	
    }
    catch(IOException e)
    {
       Logger.log(Level.SEVERE,"Can't creat log file handler",e);
    }
}
```

3.现在，可以记录自己想要的内容了。需要牢记：所有级别为INFO、WARNING和SEVERE的消息都将显示到控制台上。因此, 要记录对程序用户有意义的消息，可以使用这几个级别。对于程序员想要的日志消息，FINE级别是一个很好的选择。



## 6.调试技巧

1.可以用下面的代码打印或记录任意变量的值：

```java
System.out.println("x="+x);
//或
Logger.getGlobal().info("x="+x);
```

2.可以在每一个类中放置一个单独的main方法。这样就可以提供一个单元测试桩 (stub), 允许你独立地测试类。

3.如果喜欢使用前面介绍的那个技巧. 可以在http://junit.org 网站上查看JUnit。JUnit是一个非常流行的单元测试框架，利用它可以很容易地组织测试用例套件。只要对类做了修改，就需要运行测试。一旦发现 bug， 则要再补充另一个测试用例。

4.日志代理 (loggingproxy) 是一个子类的对象，它可以截获方法调用，将这些调用记人日志，然后调用超类中的方法。

5.利用 Throwable 类的 printStackTrace 方法，可以从任意的异常对象获得栈轨迹。

或者直接用此语句:

```java
Thread.dumpStack();
```

6.一般来说，栈轨迹显示在System.err上。如果想要记录或显示栈轨迹，可以如下将它捕获到一个字符串中:

```java
var out=new StringWriter();
new Throwable().printStackTrace(new PrintWriter(out));
String description=ouy.toString();
```

7.-Xlint选项告诉编译器找出常见的代码问题。

```
javac -Xlint sourceFiles
```

# 五、集合

分为单列集合和双列集合

List系列集合：添加的元素是有序、可重复、有索引

Set系列集合：添加的元素是无序、不重复、无索引

## 1.单列集合顶层接口Collection

Collection是单列集合的祖宗接口，它的功能是全部单列集合都可以继承使用的。

| 方法名称                            | 说明                             |
| ----------------------------------- | -------------------------------- |
| public boolean add(E e)             | 把给定的对象添加到当前集合中     |
| public void clear()                 | 清空集合中所有的元素             |
| public boolean remove(E e)          | 把给定的对象在当前集合中删除     |
| public boolean contains(object obj) | 判断当前集合中是否包含给定的对象 |
| public boolean isEmpty()            | 判断当前集合是否为空             |
| public int size()                   | 返回集合中元素的个数/集合的长度  |

关于contains函数：

contains方法在底层是依赖equals方法判断对象是否一致的。如果存的是自定义对象(结构体)，没有重写equals方法，那么默认使用Object类中的equals方法进行判断，而Object类中的equals方法，依赖地址值进行判断。





## 2.Collection的遍历方式

### 1.迭代器Iterator

> 集合专用的遍历方式。

Collection集合获取迭代器

| 方法名称                 | 说明                                    |
| ------------------------ | --------------------------------------- |
| `Iterator<E> iterator()` | 返回迭代器对象，默认指向当前集合的O索引 |

lterator中的常用方法

| 方法名称          | 说明                                                      |
| ----------------- | --------------------------------------------------------- |
| boolean hasNext() | 判断当前位置是否有元素，有元素返回true ,没有元素返回false |
| E next()          | 获取当前位置的元素，并将迭代器对象移向下一个位置。        |

**注意：**

1，迭代器遍历完毕，指针不会复位

2，循环中只能用一次next方法（若用了两次，且指针已指向null后再次调用迭代器继续遍历，则报错NoSuchElementException）

3，迭代器遍历时，不能用集合的方法(add方法等)进行增加或者删除

```java
Collection<String> coll=new ArrayList<>();
coll.add("aaa");
Interator<String> it=coll.iterator();    //使用迭代器
while(it.hasNext())
{
	String a=it.next();
	System.out.println(a);
}
```



### 2.增强for遍历--foreach

- 增强for的底层就是迭代器，为了简化迭代器的代码书写的。
- 它是JDK5之后出现的，其内部原理就是一个lterator迭代器。
- 所有的单列集合和数组才能用增强for进行遍历。

语法：

```java
for(元素的数据类型 变量名 :数组或者集合){
    
}
```

修改增强for中的变量，不会改变集合中原本的元素。

### 3.lambda表达式

| 方法名称                                          | 说明               |
| ------------------------------------------------- | ------------------ |
| default void foreach(Consumer<? super T> action): | 结合lambda遍历集合 |

例：

```java
Collection<String> coll=new ArrayList<>();
            coll.add("aaa");
            coll.add("bbb");
            coll.add("ccc");
coll.forEach(s->{System.out.println(s);});
```

## 3.List系列集合

- collection的方法List都继承了
- List集合因为有索引，所以多了很多索引操作的方法。

| 方法名称                      | 说明                                   |
| ----------------------------- | -------------------------------------- |
| void add(int index,E element) | 在此集合中的指定位置插入指定的元素     |
| E remove(int index)           | 删除指定索引处的元素，返回被删除的元素 |
| E set(int index,E element)    | 修改指定索引处的元素，返回被修改的元素 |
| E get(int index)              | 返回指定索引处的元素                   |

遍历方式：

迭代器遍历--在遍历的过程中需要删除元素，请使用迭代器。

增强for遍历--仅仅想遍历，那么使用增强for或Lambda表达式

Lambda表达式遍历--仅仅想遍历，那么使用增强for或Lambda表达式

普通for循环(因为List集合存在索引)--如果遍历的时候想操作索引，可以用普通for。

列表迭代器遍历--在遍历的过程中需要添加元素，请使用列表迭代器

### Collections.addAll() 的使用 以及和list.addAll() 的区别

 Collections 是java.util 下的一个类 ,可以直接使用

下面下一个往list 里面添加数据的方法

**1.普通的写法**

```java
   ArrayList<String> list = new ArrayList<>();
        list.add("河南");
        list.add("郑州");
        list.add("开封");
        list.add("周口");
        list.add("商丘");
```

**2.使用:Collections.addAll()**

```java
  ArrayList<String> list = new ArrayList<>();
        Collections.addAll(list, "河南", "郑州", "开封", "周口", "商丘");
```

**3.或者定义一个数组添加到list 中**

```java
  String[] arr = {"河南", "郑州", "开封", "周口", "商丘"};
        ArrayList<String> list = new ArrayList<>();
        Collections.addAll(list, arr);
```

**4.list.addAll 无法直接添加多个元素,也不能直接添加一个数组, 需要转换下**

当数量过多的时候 建议使用Collections.addAll() ,数量少的时候,使用哪个都可以,看个人习惯吧.

```java
  String[] arr = {"河南", "郑州", "开封", "周口", "商丘"};
        ArrayList<String> list = new ArrayList<>();
        list.addAll(Arrays.asList(arr));
 
// 或者
 String[] arr = {"河南", "郑州", "开封", "周口", "商丘"};
        ArrayList<String> list = new ArrayList<>(Arrays.asList(arr));
```



### 列表迭代器遍历--ListIterator

```java
ListIterator<String> it2=list.listIterator();
        while (it2.hasNext()) {
            System.out.println(it2.next());
        }
```

## 4.泛型

> 泛型的细节
>
> - 泛型中不能写基本数据类型
> - 指定泛型的具体类型后，传递数据时，可以传入该类类型或者其子类类型
> - 如果不写泛型，类型默认是Object

**1.泛型方法**
方法中形参类型不确定时，可以使用类名后面定义的泛型`<E>`

```java
public class MyArrayList {
	public <E> boolean add(E e){
	obj[size]=e;
	size++;
	return true;
}
```

**2.泛型接口**

```java
//格式
修饰符 interface 接口名<类型>{
	
}
//举例
public interface List<E>{
    
}
```

**3.泛型类**

```java
//格式
修饰符 class 类名<类型>{
    
}
//举例
public class ArrayList<E>{
    
}
```

## 5.Set系列集合

> Set、LinkedHashSet

```java
Set<Integer> s=new HashSet<>();
LinkedHashSet<Integer> s2=new LinkedHashSet<>();
```



## 6.双列集合顶层接口Map

Map是双列集合的顶层接口，它的功能是全部双列集合都可以继承使用的

| 方法名称                            | 说明                                 |
| ----------------------------------- | ------------------------------------ |
| V put(K key,V value)                | 添加元素                             |
| V remove(obiect key)                | 根据键删除键值对元素                 |
| void clear()                        | 移除所有的键值对元素                 |
| boolean containsKey(object key)     | 判断集合是否包含指定的键             |
| boolean containsValue(Obiect value) | 判断集合是否包含指定的值             |
| boolean isEmpty()                   | 判断集合是否为空                     |
| int size()                          | 集合的长度，也就是集合中键值对的个数 |

### 6.1 遍历方式

**1.键找值--增强for循环**

方法KeySet()：获得所有的键。

方法get()：获得键所对应的值。

```java
Map<String,String> m=new HashMap<>();
        m.put("qiqi", "77");
        m.put("java", "lg");
        m.put("c++", "sz");
        Set<String> keys=m.keySet();     //得到所有的键

//增强for循环--1       
for(String key:keys)
        {
            String value=m.get(key);
            System.out.println(key+"="+value);
        }
//Iterator迭代器--2
Iterator<String> it=keys.iterator();
        while(it.hasNext())
        {
            String key=it.next();
            String value=m.get(key);
            System.out.println(key+"="+value);
        }
//lambda表达式方法遍历--3
m.forEach((key,value)->{System.out.println(key+"="+value);
```

**2.键值对--迭代器/lambda表达式**

方法entrySet()：其主要作用是返回了一个`Set<Map.Entry<K,V>>`类型的集合，即创建一个对象使`entrySet `**不为`null`**

```java
Map<String,String> m=new HashMap<>();
        m.put("qiqi", "77");
        m.put("java", "lg");
        m.put("c++", "sz");
//键值对方法--
//m.entrySet()返回一个空Set
        Set<Map.Entry<String,String>> set=m.entrySet();

//Iterator迭代器--1    
		Iterator<Map.Entry<String,String>> it=set.iterator();
        while(it.hasNext()){
            Map.Entry<String,String> entry=it.next();
            System.out.println(entry.getKey()+"="+entry.getValue());
//增强for循环--2
        for(Entry<String, String> map:set)
        {
            System.out.println(map);
        }
//lambda表达式进行遍历--3
         m.forEach((key,value)->{System.out.println(key+" "+value);});
```

### 6.2 HashMap

HashMap的特点

1.HashMap是Map里面的一个实现类。

2.没有额外需要学习的特有方法，直接使用Map里面的方法就可以了。

3.特点都是由键决定的:**无序**、不重复、无索引。

4.HashMap跟Hashset底层原理是一模一样的，都是哈希表结构。

5.如果键存储的是自定义对象，需要重写hashcode和equals方法。

如果值存储自定义对象，不需要重写hashcode和equals方法

### 6.3 LinkedHashMap

由键决定:**有序**、不重复、无索引。

这里的有序指的是保证存储和取出的元素顺序一致。

原理:底层数据结构是依然哈希表，只是每个键值对元素又额外的多了一个双链表的机制记录存储的顺序。

# 六、Stream流

## 1.使用方式

| 获取方式     | 方法名                                          | 说明                     |
| ------------ | ----------------------------------------------- | ------------------------ |
| 单列集合     | `default Stream<E> stream()`                    | Collection中的默认方法   |
| 双列集合     | 无(需要通过keySet和EntrySet中转一下)            | 无法直接使用stream流     |
| 数组         | `public static <T> Stream<T> stream(T[] array)` | Arrays工具类中的静态方法 |
| 一堆零散数据 | `public static<T> Stream<T> of(T...values)`     | Stream接口中的静态方法   |

**1.单列集合**

> 用stream()方法

```java
ArrayList<String> list=new ArrayList<>();
Collections.addAll(list, "a","b","c");
list.stream().forEach(s->System.out.println(s));
```

**2.双列集合**

```java
HashMap<String,Integer> hm=new HashMap<>();
hm.put("aaa",111);
hm.put("bbb",222);
hm.put("ccc",333);
hm.put("ddd",444);
//第一种获取stream流
//hm.keySet().stream().forEach(s->System.out.println(s));
//第二种获取stream流
hm.entrySet().stream().forEach(s->System.out.println(s));
```

**3.数组**

```java
int[] arr={1,2,3,4,5,6,7};
Arrays.stream(arr).forEach(s->System.out.println(s));
```

**4.一堆零散数据**

```java
int[] arr1={1,2,3,4,5,6,7};
String[] arr2={"a","b","c"};
Stream.of(arr1).forEach(s->System.out.println(s));       //打印arr1的地址
Stream.of(arr2).forEach(s->System.out.println(s));       //正常打印
```

of方法的形参是一个可变参数，可以传递一些零散的数据，也可以传递数组。

但是数组里面的数据必须是引用数据类型(比如字符串`“awa”`)的，如果传递基本数据类型，则会把整个数组当作一个元素，放到Stream中。

## 2.中间方法

| 名称                                               | 说明                                 |
| -------------------------------------------------- | ------------------------------------ |
| `Stream<T> filter(Predicate<? super T> predicate)` | 过滤                                 |
| `Stream<T> limit(long maxSize)`                    | 获取前几个元素                       |
| `Stream<T> skip(long n)`                           | 跳过前几个元素                       |
| `Stream<T> distinct()`                             | 元素去重，依赖(hashcode和equals方法) |
| `static<T>Stream<T>concat(Stream a, Stream b)`     | 合并a和b两个流为一个流               |
| `Stream<R> map(Function<T ,R> mapper)`             | 转换流中的数据类型                   |

**注意**：

中间方法，返回新的stream流，原来的Stream流只能使用一次，建议使用链式编程。

修改Stream流中的数据，**不会影响原来集合或者数组中的数据。**

### split方法

在日常编写代码时，我们经常遇到需要将一串字符串中的数据进行分析摘取，从中获得分隔符外的数据，此时便不得不提`split`方法。

分隔符可以是任意字符、符号、数字、字符串等。

**1.单个分隔符**

```java
        String str="2024,text,今天";
        //单个分隔符用引号括起来即可
        String[] data = str.split(",");
        for(int i=0;i< data.length;i++)
            System.out.println(data[i]);
```

**注意**：

如果分隔符本身就是"`|`"，那么就需要使用转义字符`\`让其产生效果，否则结果相反。

```java
String str="a|bc|8";
        //java中\\表示一个普通\,\+特殊字符表示字符本身
        String[] data = str.split("\\|");
        for(int i=0;i< data.length;i++)
            System.out.println(data[i]);
```

**2.多个分隔符**

```java
String str="2024年11月20日;英语,数学,语文;";
        //多个分隔符用引号括起来，并且用“|”进行分割
        String[] data = str.split(",|;");
        for(int i=0;i< data.length;i++)
            System.out.println(data[i]);
```

**3.正则表达式表示分隔符**

```java
String str="2018年11月18日abcd85gg688";
        //正则表达式中\d+表示一个或多个数字,java中\\表示一个普通\
        String[] data = str.split("\\d+");
        for(int i=0;i< data.length;i++)
            System.out.println(data[i]);
```

> 实例1：

```java
List<String> l=new ArrayList<>();
l.add("张无忌");
l.add("周芷若");
l.add("赵敏");
l.add("张强");
l.add("张三丰");
l.add("张翠山");
l.add("张良");
l.add("王二麻子");
l.add("谢广坤");
l.add("赵敏");   //增强重复数据以测试去重方法
l.add("赵敏");
l.add("赵敏");
l.add("赵敏");
//链式编程--使用filter方法
l.stream()
     .filter(s->s.startsWith("张"))
     .filter(s->s.length()==3)
     .forEach(s->System.out.println(s));
//使用limit方法、skip方法
l.stream().limit(4).forEach(s->System.out.println(s));
l.stream().skip(4).forEach(s->System.out.println(s));
//使用distinct方法
l.stream().distinct().forEach(s->System.out.println(s));
//使用concat方法
Stream.concat(l.stream(), l.stream()).forEach(s->System.out.print(s+" "));
```

> 实例2：

```java
 List<String> l=new ArrayList<>();
            l.add("张无忌-12");
            l.add("周芷若-14");
            l.add("赵敏-16");
            l.add("张强-18");
            l.add("张三丰-20");
            l.add("张翠山-22");
            l.add("张良-24");
            l.add("王二麻子-26");
            l.add("谢广坤-28");
            l.add("赵敏-30");
            l.add("赵敏-32");
            l.add("赵敏-34");
            l.add("赵敏-24");
            System.out.println("========================");
            l.stream()
                .map(s->Integer.parseInt(s.split("-")[1]))      //"-"作为分隔符
                .forEach(s->System.out.println(s));
```

> 实例3：(**字符串过滤并收集**)

```java
//题目：创建一个ArrayList集合，并添加以下字符串，字符串中前面是姓名，后面是年龄
//("zhangsan,23","lisi,24","wangwu,25")
//保留年龄大于等于24岁的人，并将结果收集到Map集合中，姓名为键，年龄为值
ArrayList<String> a=new ArrayList<>();
            Collections.addAll(a,"zhangsan,23","lisi,24","wangwu,25");
            Map<String,Integer> map=a.stream()
            .filter(s->Integer.parseInt(s.split(",")[1])>=24)   //Integer.parseInt是类型转换
            .collect(Collectors.toMap(
                    s->s.split(",")[0],
                    s->Integer.parseInt(s.split(",")[1])));
                    System.out.println(map);
```

> 实例4：(**自定义类型过滤并收集**)

```java
/* 
现在有两个ArrayList集合
第一个集合中:存储6名男演员的名字和年龄。第二个集合中:存储6名女演员的名字和年龄
姓名和年龄中间用逗号隔开。比如:张三,23
要求完成如下的操作:
1，男演员只要名字为3个字的前两人
2，女演员只要姓杨的，并且不要第一个
3，把过滤后的男演员姓名和女演员姓名合并到一起
4，将上一步的演员信息封装成Actor对象
5，将所有的演员对象都保存到List集合中
备注:演员类Actor，属性有:name，age
*/
ArrayList<String> t1=new ArrayList<>();
            ArrayList<String> t2=new ArrayList<>();
            Collections.addAll(t1, "张亮,18","李亮,20","三岁岁,29","李浩天,21","张三,12","李四天,21");
            Collections.addAll(t2, "杨熙,21","赵梅,21","李每美,33","萧苏胡,12","李曦,19","杨随天,21");
            Stream<String> stream1 = t1.stream()
            .filter(s->(s.split(",")[0]).length()==3)
            .limit(2);
            Stream<String> stream2 = t2.stream()
            .filter(s->s.split(",")[0].startsWith("杨"))
            .skip(1);
            List<Actor> list=Stream.concat(stream1, stream2)
                    .map(s->new Actor(s.split(",")[0],Integer.parseInt(s.split(",")[1])))
                    .collect(Collectors.toList());
```



## 3.终结方法

| 名称                          | 说明                       |
| ----------------------------- | -------------------------- |
| void forEach(Consumer action) | 遍历                       |
| long count()                  | 统计                       |
| toArray()                     | 收集流中的数据，放到数组中 |
| collect(Collector collector)  | 收集流中的数据，放到集合中 |

实例：

```java
List<String> l=new ArrayList<>();
l.add("张无忌");
l.add("周芷若");
l.add("赵敏");
l.add("张强");
l.add("张三丰");
l.add("张翠山");
l.add("张良");
l.add("王二麻子");
l.add("谢广坤");
l.stream().forEach(s->System.out.println(s));             //遍历--forEach
System.out.println("==========================");
long count=l.stream().count();
System.out.println(count);                                //统计--count
System.out.println("==========================");
Object[] arr1=l.stream().toArray();                       //收集流中的数据，放在数组中--toArray
System.out.println(Arrays.toString(arr1));
```

```java
//收集流中的数据，放到集合中--Collect
ArrayList<String> strings = new ArrayList<>();
    strings.add("张无忌");
    strings.add("周芷若");
    strings.add("赵敏");
    strings.add("张强");
    strings.add("张三丰");
    strings.add("张三丰");


    // 1、获取流中姓"张"的并转化为set集合
    Set<String> set = strings.stream().filter(s -> s.startsWith("张")).collect(Collectors.toSet());
    System.out.println(set);
    System.out.println("-----------------------------------");
    // 2、获取流中姓"张"的并转化为list集合
    List<String> list = strings.stream().filter(s -> s.startsWith("张")).collect(Collectors.toList());
    System.out.println(list);
    System.out.println("-----------------------------------");
    // 2、获取流中姓"张"的并转化为数组
    String[] arr = strings.stream().filter(s -> s.startsWith("张")).toArray(String[]::new);
    for (String s : arr) {
      System.out.println(s);
    }
```



# 七、方法引用

## 1.基础概念

方法引用是把已经存在的方法拿过来用，当做函数式接口中抽象方法的方法体，`::`是什么方法引用符。

方法引用时要注意的点：

- 需要有函数式接口
- 被引用方法必须已经存在
- 被引用方法的形参和返回值需要跟抽象方法保持一致
- 被引用方法的功能要满足当前的需求

## 2.引用静态方法

**格式：**类名`::`静态方法

**范例：**`Integer::parseInt`

> 实例：

```java
ArrayList<String> list=new ArrayList<>();
            Collections.addAll(list,"1","2","3","4","5");		
list.stream()
        .map(Integer::parseInt)
        .forEach(s->System.out.println(s));
```

## 3.引用成员方法

格式：对象`::`成员方法

- 其他类：其他类对象`::`方法名
- 本类：this`::`方法名
- 父类：super`::`方法名

**1.其他类对象**

```java
//主.java文件
package mycode;
import java.util.ArrayList;
import java.util.Collections;

public class mycodetext{
        public static void main(String[] args){
            ArrayList<String> list=new ArrayList<>();
            Collections.addAll(list,"张无忌","周芷若","赵敏","张强","张三丰");
            list.stream().filter(new StringOperation()::stringJudge)
                    .forEach(s->System.out.println(s));
        }
    }

//另一个.java文件
package mycode;
public class StringOperation {
    public boolean stringJudge(String s) {
        return s.startsWith("张") && s.length() == 3;
    }
}
```

**2.本类**

 **格式：**this`::`成员方法

> **注：**如果是在静态方法中，是没有this的，只能用对象名

```java
public static void main(String[] args) {
    ArrayList<String> list = new ArrayList<>();
    Collections.addAll(list,  "张无忌",  "张强", "张三丰", "张翠山", "张良", "王二麻子", "谢广坤");
 
    List<String> collect= new Demo4().method(list);
    System.out.println(collect);
}
 
public List<String> method(List<String> list){
    return list.stream().filter(this::stringJudge).collect(Collectors.toList());
}
 
public boolean stringJudge(String s){
    return s.startsWith("张") && s.length() == 3;
}
```

**3.父类**

**格式：**super`::`成员方法

> **注：**如果是在静态方法中，是没有super的，只能用对象名

```java
public class Demo5 {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        Collections.addAll(list,  "张无忌",  "张强", "张三丰", "张翠山", "张良", "王二麻子", "谢广坤");
 
        List<String> collect = new Son().method(list);
        System.out.println(collect);
    }
}
 
class Son extends Father {
    public List<String> method(List<String> list){
        return list.stream().filter(super::stringJudge).collect(Collectors.toList());
    }
}
 
class Father{
    public boolean stringJudge(String s){
        return s.startsWith("张") && s.length() == 3;
    }
}
```

## 4.引用构造方法

**格式：**类名`::`new

**范例：**`Student::new`

```java
//第一个文件--获得Student类中的所有值并打印出来
package mycode;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.function.Function;
import java.util.stream.Collectors;

public static void main(String[] args) {
    ArrayList<String> list = new ArrayList<>();
    Collections.addAll(list, "张无忌,32", "张强,29", "张三丰,56", "张翠山,48", "张良,25", "王二麻子,28", "谢广坤,39");
 
    List<Student> collect = list.stream().map(Student::new).collect(Collectors.toList());
 
    System.out.println(collect);
}
//第二个文件
package mycode;

public class Student {
  private String name;
  private int age;

  public Student() {
  }

  public Student(String s) {
    this.name = s.split(",")[0];
    this.age = Integer.parseInt(s.split(",")[1]);
  }

  public Student(String name, int age) {
    this.name = name;
    this.age = age;
  }
  public String toString() {
    return "Student{name='" + name + "', age=" + age + "}";
}

}
```

## 5.其他调用方式

**1、使用类名引用成员方法**

**格式**：类名`::`成员方法

**范例**：`String::substring`

> 特有规则： 
>

- 引用处必须是函数式接口

- 被引用的方法必须已经存在
- **被引用方法的形参，需要跟抽象方法的第二个形参到最后一个形参保持一致，返回值需要保持一致**
- 被引用方法的功能要满足当前需求

> 抽象方法形参的详解：

- 第一个参数：表示被引用方法的调用者，决定了可以引用哪些类中的方法，在stream 流当中，第一个参数一般都表示流里面的每一个数据。假没流里面的数据是字符串，那么使用这种方式进行方法引用，只能引用 string 这个类中的方法
- 第二个参数到最后一个参数：跟被引用方法的形参保持一致，如果没有第二个参数，说明被引用的方法需要是无参的成员方法

> 局限性：

不能引用所有类中的成员方法。是跟抽象方法的第一个参数有关，这个参数是什么类型的，那么就只能引用这个类中的方法。

```java
ArrayList<String> list = new ArrayList<>();
Collections.addAll(list, "aaa", "bbb", "ccc", "ddd");
 //引用String中的toUpperCase方法并收集到collect中
List<String> collect = list.stream().map(String::toUpperCase).collect(Collectors.toList());
System.out.println(collect);
```

**2、引用数组的构造方法**

**格式：**类名`::`new

**范例：**`Student::new`

```java
ArrayList<Integer> list = new ArrayList<>();
Collections.addAll(list, 1, 2, 3, 4, 5);
 //引用数组的构造方法将list放入数组arr中
Integer[] arr = list.stream().toArray(Integer[]::new);
// List<Integer> l=list.stream().collect(Collectors.toList());           //此语句和上一条语句的作用相同
System.out.println(Arrays.toString(arr));
```

# 八、文件

## 1.基础概念与常用类

- File对象就表示一个路径，可以是文件的路径、也可以是文件夹的路径
- 这个路径可以是存在的，也允许是不存在的

| 方法名称                                | 说明                                               |
| --------------------------------------- | -------------------------------------------------- |
| public File(String pathname)            | 根据文件路径创建文件对象                           |
| public File(String parent,String child) | 根据父路径名字符串和子路径名字符串创建文件对象     |
| public File(File parent,String child)   | 根据父路径对应文件对象和子路径名字符串创建文件对象 |

```java
//--1
String str="C:\\Users\\wuqian\\Desktop\\dzyszz.txt";
File f1=new File(str);
System.out.println(f1);
//--2
String parent="C:\\Users\\wuqian\\Desktop";
String child="dzyszz.txt";
File f2=new File(parent,child);
System.out.println(f2);
//--3
File f3=new File(parent+"\\"+child);
System.out.println(f3);
```

## 2.File的常见成员方法

### 1.判断、获取

| 方法名称                        | 说明                               |
| ------------------------------- | ---------------------------------- |
| public boolean isDirectory()    | 判断此路径名表示的File是否为文件夹 |
| public boolean isFile()         | 判断此路径名表示的File是否为文件   |
| public boolean exists()         | 判断此路径名表示的File是否存在     |
| public long length()            | 返回文件的大小(字节数量)           |
| public string getAbsolutePath() | 返回文件的绝对路径                 |
| public string getPath()         | 返回定义文件时使用的路径           |
| public string getName()         | 返回文件的名称，带后缀             |
| public long lastModified()      | 返回文件的最后修改时间(时间毫秒值) |

```java
File f1=new File("C:\\Users\\wuqian\\Desktop\\dzyszz.txt");
System.out.println(f1.isDirectory());       //false
System.out.println(f1.isFile());            //true
System.out.println(f1.exists());            //true
```

### 2.创建、删除

| 方法名称                       | 说明                 |
| ------------------------------ | -------------------- |
| public boolean createNewFile() | 创建一个新的空的文件 |
| public boolean mkdir()         | 创建单级文件夹       |
| public boolean mkdirs()        | 创建多级文件夹       |
| public boolean delete()        | 删除文件、空文件夹   |

### 3.获取并遍历

| 方法名称                  | 说明                     |
| ------------------------- | ------------------------ |
| public File[] listFiles() | 获取当前该路径下所有内容 |

## 实例

> **1.在当前模块下的aaa文件夹中创建一个a.txt文件**

```java
File f1=new File("INTERFACE\\aaa");
f1.mkdirs();
String child="a.txt";
File src=new File(f1,child);
boolean b=src.createNewFile();
if(b)
{
    System.out.println("创建成功");
}
else {
    System.out.println("创建失败");
}
```

> **2.定义一个方法找某一个文件夹中，是否有以avi结尾的电影**

```java
public static void main(String[] args) {
                File file=new File("D:\\aaa\\bbb");
                boolean a=haveAVI(file);
                System.out.println(a);
            }
    public static boolean haveAVI(File file) {
        File[] files=file.listFiles();
        for(File f: files)
        {
            if(f.isFile()&&f.getName().endsWith(".avi"))
            return true;
        }
        return false;
    }
```

> **3.遍历硬盘查找文件夹**

```java
public static void main(String[] args) {
                File file=new File("D:\\");
                digui(file);
            }
            public static void digui(File file) {
                File [] files=file.listFiles();
                if(files!=null){
                for(File f:files)
                {
                    if(f.isFile())
                    {
                        if(f.getName().endsWith(".avi"))
                        {
                            System.out.println("存在avi "+f.getName());
                    }
                    }
                    else{
                        digui(f);
                    }
                }
            }
            }
```

> **4.删除一个多级文件夹**

```java
public static void main(String[] arg)
    {
        File files=new File("D:\\aaa");
        digui(files);
    }
    public static void digui(File file)
    {
        File [] s=file.listFiles();
        for(File f:s) {
            if(f.isFile())
            {
                f.delete();
                System.out.println("删除成功");
            }
            else {
                digui(f);
            }
        }
        file.delete();     //删除自己
    }
```

> **5.统计文件数量**

```java
public class mycodetext{
    static int a=0;
    static int b=0;
    static int c=0;
    public static void main(String[] arg) throws IOException {
        File files=new File("D:\\aaa");
        digui(files);
        System.out.println("txt:"+a+"个");
        System.out.println("doc:"+b+"个");
        System.out.println("jpg:"+c+"个");
    }
    public static void digui(File file)
    {
        File[] files=file.listFiles();
        for(File f:files)
        {
            if(f.isFile())
            {
                if(f.getName().endsWith(".txt"))
                    a++;
                if(f.getName().endsWith(".doc"))
                    b++;
                if(f.getName().endsWith("jpg"))
                    c++;
            }
            else
                digui(f);
        }
    }
}
```

# 九、IO流

用于读写文件中的数据(可以读写文件，或网络中的数据)

> **IO流按照操作文件的类型可以分类为：**

- 字节流：可以操作所有类型的文件
- 字符流：只能操作纯文本文件(用windows系统自带的记事本打开并且能读懂的文件,如txt文件,md文件,xml文件,lrc文件等)

> **按照流向分类为：**

- 输出流：程序-->文件
- 输入流：文件-->程序

## 1.FileOutputStream

> 创建字节输出流对象

- 细节1:参数是字符串表示的路径或者File对象都是可以的
- 细节2:如果文件不存在会创建一个新的文件，但是要保证父级路径是存在的。
- 细节3:如果文件已经存在，则会清空文件

> 写数据

细节: write方法的参数是整数，但是实际上写到本地文件中的是整数在ASCII上对应的字符

> 释放资源

每次使用完流之后都要释放资源

**实例：**

```java
FileOutputStream f=new FileOutputStream("D:\\aaa\\a.txt");
f.write(97);
f.close();
```

### write()方法

| 方法名称                             | 说明                         |
| ------------------------------------ | ---------------------------- |
| void write(int b)                    | 一次写一个字节数据           |
| void write(byte[] b)                 | 一次写一个字节数组数据       |
| void write(byte[] b,int off,int len) | 一次写一个字节数组的部分数据 |

```java
FileOutputStream f=new FileOutputStream("D:\\aaa\\a.txt");
f.write(98);         //--1
byte[] bytes={97,98,99,100,101};
f.write(bytes);             //--2
f.write(bytes,2,3);         //--3 从索引2开始，写3个数据进入文件中
f.close();
```

### 换行和续写

```java
FileOutputStream f=new FileOutputStream("D:\\CCodes\\vscodebase\\JAVA\\INTERFACE\\src\\mycode\\a.txt",true);
//这里的true是打开续写开关的意思，默认是false。
String str="qiqizishikalabiqiugaoshou\r\n";   //'\r\n'是回车换行
String str2="QWQ";
byte[] bytes=str.getBytes();      //字节数组
byte[] bytes1=str2.getBytes();
f.write(bytes);
f.write(bytes1);
f.close();
```

## 2.FileInputStream

> 创建字节输入流对象

细节1:如果文件不存在，就直接报错。

> 读取数据

- 细节1: 一次读一个字节，读出来的是数据在ASCII上对应的数字
- 细节2:读到文件末尾了，read方法返回-1。

> 释放资源

细节1:每次使用完流必须要释放资源。

**实例：**

```java
//普通读取一个字符
FileInputStream fis=new FileInputStream("D:\\CCodes\\vscodebase\\JAVA\\INTERFACE\\src\\mycode\\a.txt");
int b1=fis.read();
System.out.println((char)b1);
int b2=fis.read();
System.out.println(b2);
fis.close();

//循环读取
FileInputStream fis=new FileInputStream("D:\\CCodes\\vscodebase\\JAVA\\INTERFACE\\src\\mycode\\a.txt");
int b;
while((b =fis.read())!=-1)
{
      System.out.print((char)b);
}
 fis.close();
```

### read()方法

| 方法名称                       | 说明                   |
| ------------------------------ | ---------------------- |
| public int read()              | 一次读一个字节数据     |
| public int read(byte[] buffer) | 一次读一个字节数组数据 |

**注意：**一次读一个字节数组的数据，每次读取会尽可能把数组装满



## 3.文件拷贝

**1.基本语法**

```java
//拷贝小文件
FileInputStream fis=new FileInputStream("D:\\CCodes\\vscodebase\\JAVA\\INTERFACE\\src\\mycode\\a.txt");
FileOutputStream fos=new FileOutputStream("D:\\CCodes\\vscodebase\\JAVA\\INTERFACE\\aaa\\a.txt");
int b;
while((b=fis.read())!=-1)
{
      fos.write((char)b);
}
fis.close();
fos.close();
```

**2.拷贝大文件**

```java
FileInputStream fis=new FileInputStream("D:\\CCodes\\vscodebase\\JAVA\\INTERFACE\\src\\mycode\\a.txt");
FileOutputStream fos=new FileOutputStream("D:\\CCodes\\vscodebase\\JAVA\\INTERFACE\\aaa\\a.txt");
byte[] bytes=new byte[1024*1024*5];
int len;
while((len=fis.read())!=-1)
{
      fos.write(len);
}
fis.close();
fos.close();
```

## 4.字符集

1.在计算机中，任意数据都是以二进制的形式来存储的

2.计算机中最小的存储单元是一个字节

3.ASCII字符集中，一个英文占一个字节

4.简体中文版Windows，默认使用GBK字符集

5.GBK字符集完全兼容ASCII字符集

- 一个英文占一个字节，二进制第一位是0
- 一个中文占两个字节，二进制高位字节的第一位是1

**1.Unicode字符集**

UTF-8编码格式

- 一个英文占一个字节，二进制第一位是0，转成十进制是正数
- 一个中文占三个字节，二进制第一位是1，第一个字节转成十进制是负数

**2.如何不产生乱码**

1，不要用字节流读取文本文件

2，编码解码时使用同一个码表，同一个编码方式

**3.编码与解码**

Java中编码的方法

| String类中的方法                           | 说明                 |
| ------------------------------------------ | -------------------- |
| public byte[] getBytes()                   | 使用默认方式进行编码 |
| public byte[] getBytes(string charsetName) | 使用指定方式进行编码 |

Java中解码的方法

| String类中的方法                       | 说明                 |
| -------------------------------------- | -------------------- |
| String(byte[] bytes)                   | 使用默认方式进行解码 |
| String(byte[]bytes,String charsetName) | 使用指定方式进行解码 |

## 5.FileReader

**1.创建字符输入流对象**

| 构造方法                           | 说明                       |
| ---------------------------------- | -------------------------- |
| public FileReader(File file)       | 创建字符输入流关联本地文件 |
| public FileReader(String pathname) | 创建字符输入流关联本地文件 |

细节:如果文件不存在，就直接报错。

**2.读取数据**

| 成员方法                      | 说明                         |
| ----------------------------- | ---------------------------- |
| public int read()             | 读取数据，读到末尾返回-1     |
| public int read(char[lbuffer) | 读取多个数据，读到末尾返回-1 |

细节1:按字节进行读取A遇到中文，一次读多个字节，读取后解码，返回一个整数。

细节2:读到文件末尾了，read方法返回-1

> 实例

```java
//空参read()
public static void main(String[] arsg) throws IOException {
        FileReader fr=new FileReader("D:\\aaa\\a.txt");
        int ch;
        while((ch= fr.read())!=-1)
        {
            System.out.print((char)ch);
        }
        fr.close();
    }
```

```java
//有参read()
public static void main(String[] arsg) throws IOException {
        FileReader fr=new FileReader("D:\\aaa\\a.txt");
        char[] chars=new char[2];
        int ch;
        while((ch= fr.read(chars))!=-1)
        {
            System.out.print(new String(chars,0,ch));       //把数组中的数据变成字符串再进行打印
        }
        fr.close();
    }
```

**3.释放资源**

| 成员方法           | 说明          |
| ------------------ | ------------- |
| public int close() | 释放资源/关流 |

## 6.FileWriter

**1.创建字符输出流对象**

| 构造方法                                          | 说明                             |
| ------------------------------------------------- | -------------------------------- |
| public FileWriter(File file)                      | 创建字符输出流关联本地文件       |
| public FileWriter(string pathname)                | 创建字符输出流关联本地文件       |
| public FileWriter(File file, boolean append)      | 创建字符输出流关联本地文件，续写 |
| public FileWriter(String pathname,boolean append) | 创建字符输出流关联本地文件，续写 |

细节1:参数是字符串表示的路径或者File对象都是可以的

细节2:如果文件不存在会创建一个新的文件，但是要保证父级路径是存在的

细节3:如果文件已经存在，则会清空文件，如果不想清空可以打开续写开关

**2.写数据**

| 成员方法                               | 说明                   |
| -------------------------------------- | ---------------------- |
| void write(int c)                      | 写出一个字符           |
| void write(string str)                 | 写出一个字符串         |
| void write(string str,int off,int len) | 写出一个字符串的一部分 |
| void write(char[] cbuf)                | 写出一个字符数组       |
| void write(char[]cbuf,int off,int len) | 写出字符数组的一部分   |

细节: 如果write方法的参数是整数，但是实际上写到本地文件中的是整数在字符集上对应的字符

**3.释放资源**

每次使用完流后都要释放资源

### 实例

> **拷贝文件夹(包含子文件夹)**

```java
public static void main(String[] arsg) throws IOException {
        File fr=new File("D:\\aaa");
        File fw=new File("C:\\Users\\wuqian\\Desktop\\text");
        copy(fr,fw);
    }
    public static void copy(File fr,File fw) throws IOException {
        fw.mkdirs();
        File[] files=fr.listFiles();
        int ch;
        for(File file:files)
        {
            if(file.isFile())
            {
                FileInputStream fis=new FileInputStream(file);
                FileOutputStream fos=new FileOutputStream(new File(fw,file.getName()));
                byte[] bytes=new byte[1024];
                int len;
                while ((len=fis.read(bytes))!=-1)
                {
                    fos.write(bytes,0,len);
                }
                fis.close();
                fos.close();
            }
            else{
                copy(file, new File(fw,file.getName()));
            }
        }
    }
```

> 加密和解密文件夹

```java
//加密文件夹使2.jpg不可见
public static void main(String[] args) throws IOException {
        FileInputStream fis=new FileInputStream("C:\\Users\\wuqian\\Desktop\\text\\1.jpg");
        FileOutputStream fos=new FileOutputStream("C:\\Users\\wuqian\\Desktop\\text\\2.jpg");
        int b;
        while((b=fis.read())!=-1)
        {
            fos.write(b^2);
        }
        fis.close();
        fos.close();
    }

//解密2.jpg文件夹--redu.jpg
public static void main(String[] args) throws IOException {
        FileInputStream fis=new FileInputStream("C:\\Users\\wuqian\\Desktop\\text\\2.jpg");
        FileOutputStream fos=new FileOutputStream("C:\\Users\\wuqian\\Desktop\\text\\redu.jpg");
        int b;
        while((b=fis.read())!=-1)
        {
            fos.write(b^2);
        }
        fis.close();
        fos.close();
    }
```

> 修改文件中的数据并排序

```java
public static void main(String[] args) throws IOException {
        FileReader fr=new FileReader("C:\\Users\\wuqian\\Desktop\\text\\q.txt");  //2-1-9-4-7-8
        StringBuilder sb=new StringBuilder();
        int ch;
        while ((ch= fr.read())!=-1){
            sb.append((char)ch);
        }
        fr.close();
        System.out.println(sb);

        String str=sb.toString();
        String[] arrStr=str.split("-");
		
    	//排序
        ArrayList<Integer> list=new ArrayList<>();
        for(String s:arrStr){
            int i=Integer.parseInt(s);
            list.add(i);
        }
        Collections.sort(list);
        System.out.println(list);

        FileWriter fw=new FileWriter("C:\\Users\\wuqian\\Desktop\\text\\q.txt");
        for(int i=0;i<list.size();i++){
            if(i==list.size()-1){
                fw.write(list.get(i)+"");
            }else {
                fw.write(list.get(i)+"-");
            }
        }
        fw.close();
    }
```

## 7.字节缓冲流

> 提升了速度，实际上用的还是基本流

| 方法名称                                     | 说明                                     |
| -------------------------------------------- | ---------------------------------------- |
| public BufferedInputStream(InputStream is)   | 把基本流包装成高级流，提高读取数据的性能 |
| public BufferedOutputStream(OutputStream os) | 把基本流包装成高级流，提高写出数据的性能 |

```java
//拷贝文件--一次读写一个字节
public static void main(String[] args) throws IOException {
        BufferedInputStream bis=new BufferedInputStream(new FileInputStream("D:\\aaa\\b.txt"));
        BufferedOutputStream bos=new BufferedOutputStream(new FileOutputStream("D:\\aaa\\c.txt"));
        int b;
        while ((b=bis.read())!=-1)
        {
            bos.write(b);
        }
        bos.close();     //基本流的关闭在字节缓冲流的底层代码中关闭
        bis.close();
    }
```

```java
//拷贝文件--一次读写多个字节
public static void main(String[] args) throws IOException {
        BufferedInputStream bis=new BufferedInputStream(new FileInputStream("D:\\aaa\\b.txt"));
        BufferedOutputStream bos=new BufferedOutputStream(new FileOutputStream("D:\\aaa\\c.txt"));
        byte[] bytes=new byte[1024];
        int len;
        while ((len=bis.read(bytes))!=-1)
        {
            bos.write(bytes,0,len);
        }
        bos.close();
        bis.close();
    }
```

## 8.字符缓冲流

| 方法名称                        | 说明               |
| ------------------------------- | ------------------ |
| public BufferedReader(Reader r) | 把基本流变成高级流 |
| public BufferedWriter(Writer w) | 把基本流变成高级流 |

**特有方法**

| 字符缓冲输入流特有方法   | 说明                                         |
| ------------------------ | -------------------------------------------- |
| public String readLine() | 读取一行数据，如果没有数据可读了，会返回null |

```java
//循环输出数据
public static void main(String[] args) throws IOException {
    BufferedReader br=new BufferedReader(new FileReader("D:\\aaa\\b.txt"));
    String line;
    while((line=br.readLine())!=null){       //注意这里是null
        System.out.println(line);
    }
}
```

| 字符缓冲输出流特有方法 | 说明                                                        |
| ---------------------- | ----------------------------------------------------------- |
| public void newLine()  | 跨平台的换行(不同的平台如Windows系统、Linux系统、Mac系统等) |

```java
//1.创建字符缓冲输出流的对象
BufferedWriter bw = new BufferedWriter(new FileWriter("b.txt",true));
//2.写出数据
bw.write("123");
bw.newLine();
bw.write("456");
bw.newLine();
//3.释放资源
bw.close();
```

### 实例

> 根据序号排序，以`.`分隔序号和文字

```java
//方法1
public static void main(String[] args) throws IOException {
        BufferedReader br=new BufferedReader(new FileReader("D:\\aaa\\b.txt"));
        String line;
        ArrayList<String> list=new ArrayList<>();
        while ((line= br.readLine())!=null){
            list.add(line);
        }
        br.close();

        Collections.sort(list, new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                int i1=Integer.parseInt(o1.split("\\.")[0]);
                int i2=Integer.parseInt(o2.split("\\.")[0]);
                /* 在split方法中，分隔符应该是转义的，否则会造成错误。在Java中，点号.是一个正则表达式中的特殊字符，代表任何字符。你应该使用 "\\." 来分割字符串。*/
                return i1-i2;
            }
        });

        BufferedWriter bw=new BufferedWriter(new FileWriter("D:\\aaa\\q.txt"));
        for(String str:list){
            bw.write(str);
            bw.newLine();
        }
        bw.close();
    }
/*
	排序前：
	2.qiqizizzz是卡拉彼丘高手
	1.我喜欢玩csgo
	3.你是谁啊
*/

/*
	排序后：
	1.我喜欢玩csgo
	2.qiqizizzz是卡拉彼丘高手
	3.你是谁啊
*/
```

```java
//方法2
public static void main(String[] args) throws IOException {
        BufferedReader br=new BufferedReader(new FileReader("D:\\aaa\\b.txt"));
        String line;
        TreeMap<Integer,String> tm=new TreeMap<>();
        while ((line= br.readLine())!=null){
            String[] arr=line.split("\\.");
            tm.put(Integer.parseInt(arr[0]),arr[1]);
        }
        br.close();

        BufferedWriter bw=new BufferedWriter(new FileWriter("D:\\aaa\\q.txt"));
        Set<Map.Entry<Integer,String>> entries=tm.entrySet();
        for(Map.Entry<Integer,String> entry:entries){
            String value=entry.getValue();
            bw.write(value);
            bw.newLine();
        }
        bw.close();
    }
```

