<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [继承的概念](#%E7%BB%A7%E6%89%BF%E7%9A%84%E6%A6%82%E5%BF%B5)
- [继承使用场景](#%E7%BB%A7%E6%89%BF%E4%BD%BF%E7%94%A8%E5%9C%BA%E6%99%AF)
- [继承中的变量使用](#%E7%BB%A7%E6%89%BF%E4%B8%AD%E7%9A%84%E5%8F%98%E9%87%8F%E4%BD%BF%E7%94%A8)
- [this和super](#this%E5%92%8Csuper)
- [父子类中的构造方法](#%E7%88%B6%E5%AD%90%E7%B1%BB%E4%B8%AD%E7%9A%84%E6%9E%84%E9%80%A0%E6%96%B9%E6%B3%95)
- [方法重写](#%E6%96%B9%E6%B3%95%E9%87%8D%E5%86%99)
- [访问修饰符](#%E8%AE%BF%E9%97%AE%E4%BF%AE%E9%A5%B0%E7%AC%A6)
- [方法重载和方法重写](#%E6%96%B9%E6%B3%95%E9%87%8D%E8%BD%BD%E5%92%8C%E6%96%B9%E6%B3%95%E9%87%8D%E5%86%99)
- [Java中继承的特点](#java%E4%B8%AD%E7%BB%A7%E6%89%BF%E7%9A%84%E7%89%B9%E7%82%B9)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### 继承的概念

继承，泛指把前人的作风、文化、知识、财产等接收过来的过程。

`Java`中的继承，就是让类与类之间产生父子关系，被继承的类叫做**父类（基类、超类）**, 继承的类叫做**子类（派生类）**

我们可以通过关键字`extends`来实现这种继承关系

```java
// 父类
class Parent {}

// 子类
class Children extends Parent {
	// ...
}
```

当两个类发生了继承关系后，子类就拥有了父类的**非私有**成员，包括成员属性和成员方法

```java
// 父类
public class Parent {
    // 成员变量
    private String name;
    private int age;

    // 构造方法
    public Parent() {
    }

    public Parent(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter & Setter
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

// 子类继续父类
class Child extends Parent {
}
```

### 继承使用场景

在多个类中，存在**相同的属性和行为**时，可以将这些内容提取出来放到一个新类当中，让这些类和新类产生父子关系，以便实现代码复用。

### 继承中的变量使用

`Java`中使用变量，遵循就近原则，局部位置有则使用，如果没有，则去本类的成员位置找，否则就去父类中找

如果想要在子类方法使用使用类变量，可以使用`this`关键字，如果想使用父类变量，可以使用`super`关键字

```java
class Fruit {
    int price = 20;
}

class Apple extends Fruit {
    int price = 10;
    public void showPrice() {
        int price = 5;
        System.out.println(price);  // 5
        System.out.println(this.price);  // 10
        System.out.println(super.price);  // 20
    }
}
```

### this和super

<img src="https://s1.ax1x.com/2020/03/22/85LHwq.png" style="zoom:75%" />

### 父子类中的构造方法

子类继续父类，实例化子类后，如果父类中定义了无参构造，则会自动执行父类的无参构造，系统会在子类构造中加入`super()`，意思就是调用父类的构造方法，调用父类构造方法的`super()`语句必须在子类构造方法的第一行

```java
class Person {
    public Person() {
        System.out.println("Person类的无参构造方法");
    }
}

class Worker extends Person {
    public Worker() {
        // super();  这行代码系统会自动加上
        System.out.println("Worker子类的无参构造方法");
    }
}
```

但如果父类没有无参构造方法，则子类构造方法会报错，比如我们在父类中指定了一个有参构造方法

```java
class Person {
	// 有参构造方法
    public Person(String name) {
        System.out.println("Person类的无参构造方法");
    }
}

class Worker extends Person {
    public Worker() {
        super("阿振sc");  // 这时必须手动调用父类构造方法并传入参数
        System.out.println("Worker子类的无参构造方法");
    }
}
```

### 方法重写

`Java`中的方法重写（`Override`）是指子类中出现和父类方法定义相同的方法的现象。方法重写也叫方法的复写、覆盖，它要求方法名、参数列表、返回值类型都要相同

```java
class Parent {
    public void pMethod() {
        System.out.println("父类中的pMethod方法");
    }
}

class Child extends Parent {
    // 重写父类中的同名方法
	@Override
    public void pMethod() {
        System.out.println("子类中的pMethod方法");
    }
}
```

**注意：**

- 父类中的私有方法不能被重写
- 子类方法访问权限不能小于父类方法
- 子类不能比父类方法抛出更大的异常

### 访问修饰符

<img src="https://s1.ax1x.com/2020/03/22/8Im2WD.png" style="zoom:75%" />

- `private` 强调的是给自己来使用
- 默认 强调的是给同一个包下的类来使用的
- `protected` 强调的是给子类使用的
- `public` 强调的是给所有类所有的

### 方法重载和方法重写

<img src="https://s1.ax1x.com/2020/03/22/8Inzge.png" style="zoom:75%" />

### Java中继承的特点

- 单继承, `Java`中只支持类的**单继承**,但支持多层（重）继承

	`Java`中是支持**接口**的多继承的，比如：`接口A extends 接口B, 接口C, 接口D, ...`

- 父类的私有成员是不能被继承的，私有成员包含成员变量和成员方法

- 构造方法不能被继承，构造方法用于初始化本类对象，创建子类对象时，需要调用父类构造方法进行初始化

- 继承体现了一种 `is a`的关系，子类符合`is a`父类的情况下，才使用继承


