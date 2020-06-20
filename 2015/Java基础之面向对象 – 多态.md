<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [多态](#%E5%A4%9A%E6%80%81)
- [抽象类](#%E6%8A%BD%E8%B1%A1%E7%B1%BB)
- [final关键字](#final%E5%85%B3%E9%94%AE%E5%AD%97)
- [static关键字](#static%E5%85%B3%E9%94%AE%E5%AD%97)
- [接口](#%E6%8E%A5%E5%8F%A3)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### 多态

多态即多种状态，是指同一对象在不同情况下表现出不同的状态或行为

`Java`中实现多态，要有继承（或实现）关系，要有方法重写，父类引用指向子类对象

```java
/**
 * 定义父类
 */
public class Animal {
    // 姓名
    private String name;

    // 空参构造
    public Animal() {
    }

    // 全参构造
    public Animal(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    // 成员方法
    public void eat() {
        System.out.println("吃东西");
    }
}

/**
 * Dog类，Animal的子类
 */
public class Dog extends Animal {
    /**
     * 重写 eat 方法
     */
    @Override
    public void eat() {
        System.out.println(this.getName() + "吃骨头...");
    }
}

/**
 * Test Class
 * 1、存在继承关系
 * 2、重写了eat方法
 * 3、父类引用指向子类对象
 */
public class Test {
    public static void main(String[] args) {
        Animal dog = new Dog();  // 多态的表现
    }
}
```

多态的使用场景，父类类型可以作为形参的数据类型，这样，方法可以接收其任意的子类对象

```java
/**
 * 定义父类
 */
public class Animal {
    // 姓名
    private String name;

    // 空参构造
    public Animal() {
    }

    // 全参构造
    public Animal(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    // 成员方法
    public void eat() {
        System.out.println("吃东西");
    }
}

/**
 * Dog类，Animal的子类
 */
public class Dog extends Animal {
    /**
     * 重写 eat 方法
     */
    @Override
    public void eat() {
        System.out.println(this.getName() + "吃骨头...");
    }
}

/**
 * 子类 继承 Animal父类
 */
public class Mouse extends Animal {
    @Override
    public void eat() {
        System.out.println(this.getName() + "吃奶酪");
    }
}

/**
 * 测试类
 */
public class Test {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.setName("哈士奇");
        showAnimal(d);  // 同一个方法传入不同的子类对象，返回不同的结果

        Mouse m = new Mouse();
        m.setName("Jerry");
        showAnimal(m);  // 同一个方法传入不同的子类对象，返回不同的结果
    }

    public static void showAnimal(Animal an) {
        an.eat();
    }
}
```

在类继承中，如果父类和子类有同名的成员变量，那么在多态中，它们的结果不同，并且**成员变量是不能被重写的**

```java
public class Test {
    public static void main(String[] args) {
        Animal animal = new Dog();
        System.out.println(animal.name);  // Animal
        Dog dog = new Dog();
        System.out.println(dog.name);  // Dog
    }
}

class Animal {
    String name = "Animal";
}

class Dog extends Animal {
    String name = "Dog";
}
```

**多态的好处与弊端**

- 可维护性：基于继承关系，只需要维护父类代码，提高了代码的复用性，大大降低了维护程序的工作量
- 可扩展性：把不同的子类对象都当作父类看待，屏蔽了不同子类对象之间的差异，做出通用的diamagnetic，以适应不同的需求，实现了向后兼容

那多态有哪些弊端呢？

不能使用子类特定的成员，但可以通过类型转换来使用子类特定功能

这种类型转换分为两种：

- 向上转型（自动类型转换），子类型转换成父类型，如：`Animal animal = new Dog()`
- 向下转型（强制类型转换），父类型转换成子类型，如：`Dog dog = (Dog) animal`

使用类型转换时应注意：

- 只能在继承层次关系内进行转换，否则会报`ClassCastException`异常
- 将父类对象转换成子类之前，使用`instanceof`进行检查

```java
public static void main(String[] args) {
	Dog dog = new Dog();
	dog.setName("布鲁斯");
	showAnimal(dog);
}

public static void showAnimal(Animal animal) {
	if (animal instanceof Dog) {
		Dog dog = (Dog) animal;
		god.watch();  // 调用Dog类种特有的方法watch
	}
	animal.eat();
}
```

### 抽象类

类和方法都可以被抽象，包含抽象方法的类就是抽象类，抽象用`abstract`关键字修饰

如果方法只有声明，没有方法体，并且用`abstract`修饰，那么它就是一个抽象方法

```java
// 定义抽象类
public abstract class Animal {
	private String name;

	// 定义抽象方法
	public abstract void eat();
}

public class Mouse extends Animal {
	public void eat() {
		System.out.println(getName() + "吃奶酪");
	}
}

public class Dog extends Animal {
	public void eat() {
		System.out.println(getName() + "啃骨头");
	}
}
```

当需要实现一个方法，但在父类中还不明确方法的具体实现时，可以将方法定义为`abstract`，具体的实现到子类中完成

抽象类有以下特点：

- 类和方法都必须使用`abstract`关键字进行修饰

	```java
	修饰符 abstract class 类名 {}
	修饰符 abstract 返回值类型 方法名() {}
	```

- 抽象类不能被实例化，只能创建子类对象

- 抽象类子类要么重写父类所有抽象方法，要么也定义成抽象类

抽象类中可以有普通的成员变量，也可以有成员常量（用`final`修饰的），成员方法可以是普通方法，也可以是抽象方法，所以，抽象类不一定有抽象方法，但又抽象方法的类一定是抽象类或者接口

另外关于构造方法，抽象类可以像普通类一样可以又构造方法，且可以被重载

```java
/**
 * 抽象类
 */
abstract class Animal {
    // 抽象方法
    public abstract void eat();

    // 抽象方法
    public abstract void sleep();
}

/**
 * 子类继承抽象父类，必须重写所有抽象方法
 */
class Cat extends Animal {

    @Override
    public void eat() {
        System.out.println("猫吃鱼");
    }

    @Override
    public void sleep() {
        System.out.println("猫躺着睡");
    }
}

/**
 * 定义抽象子类，继承抽象父类，无需重写抽象方法
 */
abstract class Dog extends Animal {}
```

### final关键字

`final`的意思是最终、最后的

- 使用`final`修饰的类，该类不能被继承，比如系统内置的`String`类、`System`类等

- 父类中使用`final`修饰的方法，在子类中是不能被重写的，所以`final`和`abstract`两个关键字是不能同时出现的

- 使用`final`修饰的变量，表示最终值，即常量，只能赋值一次。这里需要注意，不建议使用`final`来修饰引用类型数据，因为仍然可以通过引用修改对象的内部数据，其意义不大。

```java
/**
 *	员工类
 */
public final class Employee {}

/**
 *	程序猿类
 */
public Coder extends Employee {}  // 报错..Person类不能被继承，因为被final关键字修饰
```

```java
/**
 *	人类
 */
public class Person {}

/**
 *	员工类
 */
public final class Employee extends Person {}  // 被final修饰的类不能被继承，但它可以继承其他的类
```

```java
/**
 *	员工类
 */
public class Employee {
	// 使用final修饰方法
	public final void show() {
		System.out.println("被final修饰的方法不能被子类重写");
	}
}

/**
 *	程序猿类
 */
public Coder extends Employee {
	// 试图重写父类的show方法，会报错
	public void show() {   // Exception...
		// ...
	}
}
```

```java
public class FinalTest {
	final int MAX_NUM = 30;
	// 试图修改被final修饰的常量值，报异常
	// MAX_NUM = 100;   // Exception
}
```

### static关键字

`static`关键字的意思是静态的，它可以用来修饰类的成员，包括成员变量和成员方法，这些成员变量或成员方法被称为类变量或类方法，它们属于类，而不是实例（对象）

调用这些被`static`修饰的成员变量和成员方法，可以通过`类名.成员变量名`或`类名.成员方法名(参数)`的方式

```java
public class Test {
    public static void main(String[] args) {
        Developer d1 = new Developer();
        d1.name = "小黑";
        d1.work = "写代码";

        Developer d2 = new Developer();
        d2.name = "媛媛";
        d2.work = "鼓励师";

        d1.selfIntroduction();  // 我是研发部的小黑，我的工作内容是写代码
        d2.selfIntroduction();  // 我是研发部的媛媛，我的工作内容是鼓励师
    }
}

class Developer {
    String name;
    String work;
    // 使用static关键字修饰，它是一个公共的常量值
    public final static String DEPARTMENT_NAME = "研发部";

    public void selfIntroduction() {
        System.out.println("我是" + DEPARTMENT_NAME + "的" + name + "，我的工作内容是" + work);
    }
}
```

当使用`static`修饰成员方法时，由于静态方法中没有`this`，所以不能访问非静态成员。

它的使用场景主要在值需要访问静态成员时，或者不需要访问对象状态，所需参数都由参数列表显式提供

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = { 1, 2, 3, 4, 5 };
        // 调用ReverseArray类中的静态方法反转数组元素
        ReverseArray.reverse(arr);  // [5, 4, 3, 2, 1]
    }
}

class ReverseArray {
    /**
     * 静态方法，反转一个数组
     */
    public static void reverse(int[] arr) {
        for (int i = 0; i < arr.length / 2; i++) {
            int temp = arr[i];
            arr[i] = arr[arr.length - 1 - i];
            arr[arr.length - 1 -i] = temp;
        }
    }
}
```

### 接口

> 接口技术用于描述类具有什么功能，但并不给出具体实现，类要遵从接口描述的统一规则进行定义，所以，接口是对外提供的一组规则、标准

接口的定义时通过关键字 `interface` 来实现的， `interface 接口名 {}`

类需要实现接口，实现使用关键字`implements`表示，`class 类名 implements 接口名`

```java
// 定义接口
public interface IMyInterface {
    // 定义成员方法myMethod
    public abstract void myMethod();
}

// 定义实现类
public class MyInterface implements IMyInterface {
    @Override
    public void myMethod() {
        System.out.println("实现接口中定义的方法");
    }
}

// 测试实现
public class Test {
    public static void main(String[] args) {
        // 多态实现
        IMyInterface mf = new MyInterface();
        mf.myMethod();
    }
}
```

**接口的特点**

- 接口是不能被实例化的，如果要实现它，必须通过多态的方式实例化子类对象

- 接口的子类（也就是实现类），它可以是抽象类（无需重写其方法），也可以是普通类（必须重写所有方法）

- 类与接口之间是实现的关系（`implements`），而接口与接口之间是继承的关系，也就是接口之间可以实现父子关系（`extends`），并且接口之间支持单继承和多继承，如：`接口 extends 接口1, 接口2, 接口3, ...`

- 继承和实现的区别：

	继承体现的是"is a"的关系，父类中定义共性内容
	实现体现的是"like a"的关系，接口中定义扩展功能

```java
// 定义接口USB
public interface USB {
    // 连接
    public abstract void open();

    // 关闭
    public abstract void close();
}

/**
 * 鼠标类
 * 实现USB接口
 * 需要实现所有的接口方法，包含open和close
 */
public class Mouse implements USB {
    @Override
    public void open() {
        System.out.println("连接鼠标");
    }

    @Override
    public void close() {
        System.out.println("断开鼠标");
    }
}

/**
 * 类 KeyBoard 定义为抽象类，可以不实现接口中的方法
 */
public abstract class KeyBoard implements USB {
}

public class Test {
    public static void main(String[] args) {
        // 测试鼠标类
        // USB usb = new USB();  --> 报错，接口不能被实例化
        USB usb = new Mouse();
        usb.open();  // 连接鼠标
        usb.close();  // 断开鼠标
    }
}
```

**接口中成员的特点**

- 在接口中没有成员变量，只有共有的、静态的常量，如：`public static final 常量名 = 常量值`

- 成员方法，在JDK7以前，接口中只有共有的、抽象方法，如：`public abstract 返回值类型 方法名()`

	在JDK8以后，接口可以有默认方法和静态方法，如：`public default 返回值类型 方法名() {}`，静态方法，如：`static 返回值类型 方法名() {}`

	在JDK9以后，接口中可以有私有方法，如：`private 返回值类型 方法名() {}`

- 构造方法，接口不能被实例化，也没有需要初始化的成员，所以**接口没有构造方法**

```java
public interface IMyInterface {
    /**
     * 接口中只能定义静态常量，其值不能修改
     * public static final 可以省略，如果不写，系统会自动加上
     */
    public static final int NUM = 10;

    /**
     * 成员方法
     * JDK 7 及其之前的写法
     */
    public abstract void methodForJDK7();

    /**
     * JDK 8 之后多了两种写法
     * 静态写法和默认写法
     */
    public static void staticMethod() {
        System.out.println("我是JDK8的新特性，书写静态方法");
    }

    public default void defaultMethod() {
        System.out.println("我是JDK8的新特性，书写默认方法");
    }

    /**
     * JDK 9 之后多了私有方法
     */
    private void privateMethod() {
        System.out.println("我是JDK9的新特性，私有的接口成员方法");
    }
}
```




