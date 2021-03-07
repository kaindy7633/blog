### 面向对象思想概述

对象就是世间万物，面向对象思想就是把关注点放在一件事或一个活动中涉及的人或事物上的思想（思维方式）

除了面向对象，我们还有一种思想就是面向过程，它是把关注点放在一件事或一个活动中涉及到的步骤（过程）。

面向对象思想特点：

- 是一种更符合人们思考习惯的思想
- 把复杂的事情简单化
- 把人们从执行者变成指挥者

面向对象的程序开发，就是不断的找对象、使用对象、指挥对象做事情的过程，如果没有对象，那就创建一个。它有三大特征：封装、继承和多态

### 类与对象

在`Java`中通过"类"来描述事物，它由属性和行为（方法）构成。

类，就是分类，是一系列具有相同属性和行为的事物的统称，把一系列相关事物的共同属性和行为提取出来的过程，我们称之为**抽象**

对象时某一类事物的某个具体存在，类是属性和行为的集合，是一个抽象的概念。

### 类的定义和使用

定义类的过程，就是把一系列相关事物共同的属性和行为抽取出来的过程。

事物的属性在类中叫**成员属性**，事物的行为在类中叫**成员方法**

如何创建一个对象呢？

```java
类名 对象名 = new 类名();

// 使用属性
对象名.属性名

// 调用方法
对象名.方法名
```

```java
public class Student {
	// 成员属性 姓名
	String name;
	// 成员属性 年龄
	int age;

	// 成员方法 学习
	public void study() {
		System.out.println(name + "正在学习...");
	}
}

// Test
public class TestStudent {
	public static void main(String[] args) {
		// 创建学生类对象
		Student stu = new Student();

		// 给成员属性赋值
		stu.name = "张三丰";
		stu.age = 141;

		// 调用成员方法
		stu.study();
	}
}
```

**成员变量与局部变量**

```java
public static void main(String[] args) {
	Student stu = new Student();
	stu.name = "张三丰";	// 成员变量
	stu.age = 141;

	stu.study();
}

public class Student {
	String name;
	int age;
	public void study() {
		String name = "小黑";  // 局部变量
		System.out.println(name + "正在努力学习！");
	}
}
```

成员变量定义在类中，方法之外，而局部变量定义在方法中，或存在于形式参数中。

成员变量有默认的初始化值，而局部变量没有默认初始化值，必须先赋值后使用

成员变量可以作用于类中的任何位置，而局部变量只能在方法中使用

内存中，成员变量定义在堆内存中，而局部变量定义在栈内存中，成员变量的声明周期随着对象的创建而存在，随着对象的销毁而销毁，局部变量则随着方法的调用而存在，随着方法的调用完毕而销毁。

如果成员变量和局部变量重名，则采用就近原则，如果方法内有局部变量，则使用局部变量，如果没有，则使用类中的成员变量，如果没有找到，则报错。

### 封装

> 引申义：封装就是把一系列功能打包到一台设备里，提供使用这些功能的界面，比如汽车、电脑、洗衣机...

封装的好处：

- 提高安全性
- 提高复用性
- 将复杂的事情简单化

在`Java`中，类和方法都提供了封装的体现

方法：

- 安全性：调用者无需知道方法的具体实现
- 复用性：方法可以被重复调用多次
- 简单化：将繁杂的代码以一个方法的形式呈现，通过调用方法就可以实现功能，便于维护

类：

- 安全性：调用者无需知道类的具体实现
- 复用性：类的对象可以被重复调用
- 简单化：类的对象包含了更多功能，方便使用

**private 关键字**

`private`表示私有的，是一种访问权限修饰符，用来修饰类的成员，被它修饰的成员只能在本类中访问

用法：

```java
private 数据类型 变量名;  // 修饰成员
private 返回值类型 方法名(参数列表) {};  // 修饰方法
```

`private`修饰的成员无法被外部访问，所以必须为其提供相应的访问（修改）的公共方法，即`getter`或`setter`方法

```java
public Student {
	private String name;
	private int age;

	public String getName() {
		return this.name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return this.age;
	}

	public void setAge(int age) {
		this.age = age;
	}
}
```

**this 关键字**

`this`表示本类对象的引用，本质是一个对象

每一个普通方法都有一个`this`，谁调用该方法，`this`就指向谁，调用：`this.属性名`

**JavaBean**

构造方法的概念：构造，创造，也叫构造器，它用来帮助创建对象的方法，构造方法也是用来初始化对象的。

在`Java`中通过`new`关键字来创建对象，并在内存中开辟空间，然后使用构造方法（构造器）完成对象的初始化工作

构造方法的格式：

```java
修饰符 构造方法名(参数列表) {
	// 方法体
}
```

```java
public class Student {
	public Student() {}  // 构造方法

	private String name;
	...
}
```

**构造方法注意事项：**

- 构造方法的方法名必须与类名相同
- 构造方法没有返回值
- 构造方法没有返回值类型
- 若未提供任何构造方法，系统会默认给出一个无参构造方法
- 若已提供任何构造方法，系统将不会提供无参构造方法
- 构造方法可以重载

示例：

```java
public class Student {
	// 无参构造方法
	public Student() {}

	// 有参构造方法
	public Student(String name, int age) {
		this.name = name;
		this.age = age;
	}

	private String name;
	private int age;

	...
}
```

在`Java`中编写类的规范，符合`JavaBean`标准的类，必须是具体的、公共的、并且具有无参数的构造方法，提供又来操作成员变量的`set`和`get`方法。
