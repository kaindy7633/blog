### API简介

Application Programming Interface，即应用程序编程接口，这里指的是API文档，通常叫："Java文档"，是`Java`种提供的类的使用说明书

学习API文档，发挥面向对象思想，找到`Java`提供的对象来实现功能，学习API就是学习`Java`中的类的使用方法

`Java`中组件的层次结构如下：

模块（Module） -->  包（Package） --> 类或接口（Class/Interface）

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/03/24/8bYHzQ.png" style="zoom:50%" />
</p>

**什么是模块**

模块（Module），是从`Java`9起提供的一种新的`Java`基础组件，在包（Package）的基础上又进行了一层封装，是包的容器

- JavaSE Modules 是`Java`语言的核心类库，其下的模块名多以`java`开头

- JDK Modules 是`Java`开发工具相关内容，其下的模块名多以`jdk`开头

### Object类

`Object`类是类层次结构中最顶层的基类，所有类都直接或间接继承自`Object`类，所以，所有的类都是一个`Object`（对象）

`Object`类位于`java.base`模块 --> `java.lang`包 --> `Object`

**构造方法**

`Object`类只有一个空参构造方法，`Object() {}`，构造一个对象，所有子类对象初始化时都会优先调用该方法

**成员方法**

`Object`类中有很多成员方法，其中最常用的以下4种：

- `hashCode()`

	`int hashCode()` 该方法返回对象的哈希码值，该方法通过对象的地址值进行计算，不同对象的返回值不同

	```java
	   /**
         *  Object类位于 java.lang 包下，这个包会被默认导入，无需手动导入
         *  Object类下的方法都是非静态方法
         *  所以这些方法必须使用创建的对象调用
         */
        Object obj1 = new Object();
        Object obj2 = new Object();

        /**
         *  hashCode方法
         *  不同的对象，返回的hashCode不一样
         */
        int code1 = obj1.hashCode();
        int code2 = obj2.hashCode();
        System.out.println(code1);  // 1915910607
        System.out.println(code2);  // 284720968
	```

- `getClass()`

	`Class<?> getClass()` 该方法返回调用此方法对象的运行时对象（调用者的字节码文件对象）

	```java
	   /**
         *  Class<?> getClass() 返回该调用者的字节码文件对象
         *  一个类只有一个字节码文件对象
         *  也就是通过该类创建的所有对象调用此方法返回的值都是一样的
         */
        Class cls1 = obj1.getClass();
        Class cls2 = obj2.getClass();
        System.out.println(cls1);  // class java.lang.Object
        System.out.println(cls2);  // class java.lang.Object
	```

- `toString()`

	`String toString()` 该方法返回该对象的字符串表示

	```java
	   /**
         *  String toString() 该方法返回对象的字符串表示
         *  默认返回的是地址值，不同的对象地址值不一样
         */
        String str1 = obj1.toString();
        String str2 = obj2.toString();
        System.out.println(str1);  // java.lang.Object@723279cf
        System.out.println(str2);  // java.lang.Object@10f87f48
	```

- `equals()`

	`boolean equals()` 该方法返回其他某个对象是否与此对象"相等"，默认情况下比较两个对象的引用，建议重写

	```java
	/**
	 *  boolean equals() 该方法比较两个对象是否相等
	 *  该方法比较的是对象在内存种的地址值，但不同对象的地址值都不一样
	 *  所以一般子类都会重写该方法
	 */
	boolean b1 = obj1.equals(obj2);
	System.out.println(b1);  // false
	```

**重写Object类的方法**

一般在开发种通常需要将对象转成字符串形式进行传输，或者需要对即将使用的对象进行相等的判断，所以我们需要重写`toString`方法和`equals`方法

```java
public class Student {
    private int id;
    private String name;
    private int score;

    public Student() {
    }

    public Student(int id, String name, int score) {
        this.id = id;
        this.name = name;
        this.score = score;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getScore() {
        return score;
    }

    public void setScore(int score) {
        this.score = score;
    }

    // 重写 toString 方法，用来将对象转换成对应的字符串形式
    @Override
    public String toString() {
        return "Student{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", score=" + score +
                '}';
    }

    // 重写 equals 方法
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return id == student.id &&
                score == student.score &&
                Objects.equals(name, student.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, name, score);
    }
}
```

### Scanner类

`Scanner`类就是一个扫描器，能够解析字符串和基本数据类型的数据，它读取用户再设备上的输入，然后将输入值读取到指定的变量中

`Scanner`类的构造方法很多，最常见的是`Scanner(InputStream)`，它构建一个扫描器对象，从指定输入流中获取数据参数`System.in`，对应键盘输入

`Scanner`类的成员方法有：

- `hasNextXxx()` 这是一种泛指的写法，比如：`hasNextInt()`、`hasNextDouble`等，它们用来判断是否还有下一个输入项，其中`Xxx`表示基本数据类型，返回结果为布尔类型

- `nextXxx()` 有判断，就有接收，此方法用来获取下一个输入项，其中`Xxx`表示任意基本数据类型，返回对应类型的数据，如：`nextInt()`、`nextFloat()`等

- `String nextLine()` 用于接收字符串类型的输入，意思是获取下一行数据，以换行符作为分隔符

- `String next()` 也是用于接收字符串类型的输入，意思是获取下一个输入项，以空白字符作为分隔符，空白字符包括空格、tab，回车等。

```java
// 创建Scanner对象
// System.in为标准输入流，意为键盘
Scanner sc = new Scanner(System.in);

// 接收整数
if (sc.hasNextInt()) {  // 判断录入的是否为整数
	int num = sc.nextInt();
	System.out.println(num);
}

// 接收字符串
String str = sc.nextLine();
System.out.println(str);
```

### String类

`String`类表示字符串，每一个字符串对象都时常量。在`Java`中，常量分为自定义常量和字面值常量，自定义常量通过`final`关键字定义，字面值常量包含六种，其中就有`String`类

`String`类位于：`java.base`模块 --> `java.lang`包 --> `String`

`String`类中的构造方法常用的有两种：

- `String(byte[])` 构造一个`String`对象，将指定字节数组中的数据转化成字符串

- `String(char[])` 构造一个`String`对象，将指定字符数组中的数据转化成字符串

```java
/**
 * 使用字节数组构建字符串
 */
byte[] bytes = { 97, 98, 99 };
String s1 = new String(bytes);
System.out.println(s1);  // abc

/**
 * 使用字符数组构建字符串
 */
char[] chars = { 'h', 'e', 'l', 'l', 'o' };
String s2 = new String(chars);
System.out.println(s2);  // hello

/**
 * 在实际开发中，一般可以直接定义字符串对象
 */
String str = "Hello World";
```

**String类的常用成员方法**

- `boolean equals(String)` 判断当前字符串与给定字符串是否相同，区分大小写

- `boolean equalsIgnoreCase(String)` 判断当前字符串与给定字符串是否形同，它时不区分大小写的

- `boolean startsWith(String)` 判断字符串是否以给定的字符串开头

- `boolean isEmpty(String)` 判断给定字符串是否为空

更多`String`类方法可以查看官方API文档 [String类文档](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/lang/String.html "String类文档")

```java
/**
 * 判断两个字符串对象是否相同
 */
String str1 = "abc";
String str2 = "ABC";
boolean b1 = str1.equals(str2);  // 区分大小写 返回false

boolean b2 = str1.equalsIgnoreCase(str2);  // 不区分大小写 返回true

/**
 * 判断字符串对象是否以特定字符串开头
 */
boolean b3 = str1.startsWith("a");  // 是否以a开头，返回 true

/**
 * 判断字符串是否为空
 */
boolean b4 = str1.isEmpty();  // false
```

**String类中包含获取功能的成员方法**

- `int length()` 获取字符串的长度

- `char charAt(int index)` 获取指定索引位置的字符

- `int indexOf(String)` 获取指定字符或字符串在当前字符串中第一次出现的索引，未找到返回`-1`

- `int lastIndexOf(String)` 获取指定字符或字符串在当前字符串中最后一次出现的索引，未找到返回`-1`

- `String substring(int)` 获取指定索引位置（含）之后的字符串

- `String substring(int, int)` 获取从索引`start`位置（含）起至索引`end`位置（不含）的字符串

**String类中操作字符串的成员方法**

- `byte[] getByte()` 将字符串转换成字节数组

- `char[] toCharArray()` 将字符串转换成字符数组

- `static String valueOf()` 将指定类型数据转换成字符串

- `String replace(old, new)` 将指定字符（串）替换成新的字符（串）

- `String[] split(String)` 切割字符串，返回切割后的字符串数据，源字符串不变

- `String trim()` 去除字符串两端的空白字符

### StringBuilder和StringBuffer类

`StringBuilder`和`StringBuffer`类都是可变字符序列，用于构造字符串对象，它们内部使用自动扩容的数组操作字符串数据，它们也使用相同的API

在实际应用场景中，`StringBuilder`由于效率更高，所以一般都使用`StringBuilder`

**构造方法**

- `StringBuidler()` 空参构造方法，构造一个空的`StringBuilder`容器

- `StringBuidler(String)` 构造一个`StringBuilder`容器，并添加指定字符串

```java
/**
 * 创建StringBuilder容器
 */
StringBuilder sb = new StringBuilder();
sb.append("abc");  // 返回自身

/**
 * 使用带参构造
 */
StringBuilder sb2 = new StringBuilder("abc");
System.out.println(sb2);  // abc
```

**成员方法**

- `StringBuidler append(...)` 将任意数据添加到`StringBuilder`容器中

- `String toString()` 将当前`StringBuilder`容器转换成字符串

### Date和Calendar类

`Date`类和`Calendar`类分别用于处理日期和日历，都是用于操作日期相关信息的

**Date类的构造方法**

- `Date()` 空参构造，构造一个日期对象，值为系统时间，精确到毫秒

- `Date(long)` 带参构造，构造一个日期对象，值为自"1970年1月1日 00:00:00"起至指定参数的毫秒数

**Date类和Caleander类的成员方法**

- `long getTime()` 该方法将日期对象转换成对应时间的毫秒值

- `static Calendar getInstance()` 该方法根据当前系统时区和语言环境获取日历对象

- `int get(int field)` 该方法返回给定日历字段的值

- `void set(int field, int value)` 该方法将给定的日历字段设置为指定的值

```java
/**
 *  Date类
 */
Date date = new Date();
System.out.println(date);  // Tue May 17 19:07:31 CST 2015

// 获取毫秒值
System.out.println(date.getTime());  // 1431860869000

/**
 *  指定时间
 */
Date l = new Date(1431860869000L);
System.out.println(l);  // Sun May 17 19:07:49 CST 2015
```

```java
/**
 *  通过静态方法getInstance创建Caleandar对象
 */
Calendar cd = Calendar.getInstance();

// 通过get方法获取年月日等信息
int year = cd.get(Calendar.YEAR);
int month = cd.get(Calendar.MONTH);
int day = cd.get(Calendar.DATE);
```

### 基本类型的包装类

由于基本类型不是对象，不能通过它来调用方法，所以`Java`针对基本类型提供了对应的包装类，以对象的形式来使用

| 基本类型 | 所对应包装类 |
| --- | --- |
| `byte` | Byte |
| `short` | Short |
| `int` | Integer |
| `long` | Long |
| `char` | Character |
| `float` | Float |
| `double` | Double |
| `boolean` | Boolean |

包装类有两个概念要了解：

- 装箱： 装箱就是把基本类型转换成包装类型（对象类型）

- 拆箱： 拆箱就是把包装类型转换成基本类型

**成员方法**

包装类的功能就是将字符串类型的数据转换成对应的基本类型，如：`static 基本类型 parseXxx(String)`

```java
/**
 * 装箱操作，将基本数据类型转换成引用类型
 */
// Integer it = new Integer(100);  此方式已过时，使用下面的方式
Integer it = 100;

/**
 * 拆箱操作
 */
int newIt = it.intValue();  // 100

/**
 * 将字符串类型的值转换成整数
 */
String s = "100";
int num = Integer.parseInt(s);
```