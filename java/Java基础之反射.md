> 在`Java`中，反射指的是在程序运行期间，根据类的字节码文件对象来获取类中的成员并使用的一项技术

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/04/06/Gst2R0.md.png" style="zoom:75%" />
</p>

反射的主要内容：

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/04/06/GsNiWt.png" style="zoom:75%" />
</p>

## 反射概述

什么是反射呢？ **反射就是在程序运行过程中分析类的一种能力**

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/04/06/GsNgTH.png" style="zoom:75%" />
</p>

将上图中的流程反过来，无需实例化类，即可访问类中的构造方法、成员属性以及成员方法

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/04/06/GsNb7Q.png" style="zoom:75%" />
</p>

那反射能做些什么呢？

- 分析类：通过类加载器加载并初始化一个类，查看类的所有属性和方法

- 查看并使用对象：查看一个对象的所有属性和方法并使用它们

反射的应用场景一般是：

- 构建通用的工具

- 搭建具有高度灵活性和扩展性的系统框架

## 获取字节码文件对象

**类加载器（`ClassLoader`）**

类加载器负责将类的字节码文件（`.class`文件）加载到内存中，并生成对应的`Class`对象

那`Class`对象又是什么呢？ `Class`对象就是`java.lang.Class`类的对象，也叫字节码文件对象，每个`Class`对象对应一个字节码文件

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/04/06/Gsa8ZF.png" style="zoom:75%" />
</p>

**类的加载时机**

- 创建类的实例，如： `Student stu = new Student()`，只会加载一次

- 访问类的静态成员时，如：`Calendar.getInstance()`

- 初始化子类时，会优先加载其父类

  ```java
  class User extends Person {};
  User user = new User();   // 先加载父类Person
  ```

- 通过反射方式创建类的`Class`对象，如：`Class clazz = Class.forName("类名称")`

  类名称包含包名 + 类名，如：`cn.itcast.demo1.Student`

**获取 Class 对象的三种方式**

- 通过`Object`类中的`getClass()`方法，所有类都具有该方法，如：`Class clazz = 对象名.getClass()`

- 通过类的静态属性，如：`Class clazz = 类名.class`

- 通过`Class`类的静态方法，如：`Class clazz = Class.forName("类名称")`

```java
public class ReflectDemo1 {
    public static void main(String[] args) throws ClassNotFoundException {
        // 通过Object类中的getClass方法获取
        Student stu = new Student();
        Class clazz1 = stu.getClass();

        // 通过类的静态属性获取
        Class clazz2 = Student.class;

        // 通过Class类的静态方法
        Class clazz3 = Class.forName("com.todever.demo17.Student");

		System.out.println(clazz1 == clazz2);  // true
        System.out.println(clazz3 == clazz3);  // true
    }
}

class Student {};
```

## 反射获取构造方法并使用

在`Java`中，`Constructor<T>`属于构造器对象，它属于`java.base`模块，位于`java.lang.reflect`包，我们可以通过`Class`对象获取构造器对象，常用的获取方式有三种

- `getConstructor(Class<?>...parameterTypes)`，该方法返回一个`Constructor`对象，但仅是公共的构造函数

- `getDeclaredConstructor(Class<?>...parameterTypes)`，该方法同样返回一个`Constructor`对象，但它可以获取私有的构造函数

- `getConstructors()`，该方法返回此类的所有构造函数组成的数组，但不含私有构造方法

此时我们有了构造器对象，就可以使用其内部的方法，常用的方法有两个：

- `String getName()`，该方法返回构造函数名

- `T newInstance(Object... initargs)`，使用返回的构造函数和参数一起创建并初始化对象

```java
public class ReflectDemo2 {
    public static void main(String[] args) throws Exception {
        // 获取Student类的字节码文件
        Class clazz1 = Class.forName("com.todever.demo17.Person");
        // 通过字节码文件获取无参构造
        Constructor con1 = clazz1.getConstructor();
        System.out.println(con1);  // public com.todever.demo17.Person()
		// 通过字节码文件获取有参构造
        Constructor con2 = clazz1.getConstructor(String.class);
        System.out.println(con2);  // public com.todever.demo17.Person(java.lang.String)
		// 通过字节码文件获取私有构造
        Constructor con3 = clazz1.getDeclaredConstructor(int.class);
        System.out.println(con3);  // private com.todever.demo17.Person(int)

		// 获取Person类所有的构造方法数组(私有除外)
        Constructor[] cons = clazz1.getConstructors();
        for (Constructor con : cons) {
            System.out.println(con);
            // public com.todever.demo17.Person()
            // public com.todever.demo17.Person(java.lang.String)
        }

		// 通过getName获取类名
        String _name = con2.getName();
        System.out.println(_name);  // com.todever.demo17.Person

		// 通过newInstance方法获取到Student类的对象
        Person p = (Person) con2.newInstance("张三");
        System.out.println(p);
        // name: 张三
        // com.todever.demo17.Person@27973e9b
    }
}

class Person {
    // 公共无参构造
    public Person() {}

    // 公共有参构造
    public Person(String name) {
        System.out.println("name: " + name);
    }

    // 私有有参构造
    private Person(int age) {
        System.out.println("age: " + age);
    }
}
```

## 反射获取成员方法并使用

`Method`对象，即方法对象，属于`java.base`模块，`java.lang.reflect`包

它通过`Class`对象获取方法

- `getMethod(String name, Class<?>... parameterTypes)`，该方法返回一个`Method`对象，仅包含公共成员方法，`name`是方法名，`parameterTypes`是方法的参数列表

- `getDeclaredMethod(String name, Class<?>... parameterTypes)`，该方法返回一个`Method`对象，可以获取私有成员方法

- `getMethods()`，该方法返回该类中所有方法的数组，但不包含私有方法

`Method`对象的常用方法：

- `String getName()`，该方法返回方法名

- `Object invoke(Object obj, Object... args)`，在指定对象上调用此方法，参数为`args`

```java
public class Test {
    public static void main(String[] args) throws Exception {
        // 获取Person类的字节码文件对象
        Class clazz = Class.forName("com.todever.demo18.Person");
        // 获取该类的构造器对象
        Constructor con = clazz.getConstructor();
        // 调用newInstance方法获取该类的实例对象，需要返回一个Person类型的
        Person person = (Person) con.newInstance();
        System.out.println(person);  // com.todever.demo18.Person@10f87f48

        // 调用公共的空参方法
        Method show1 = clazz.getMethod("show1");
        System.out.println(show1); // public void com.todever.demo18.Person.show1()
        // 如果只想看方法名，可以使用getName方法
        System.out.println(show1.getName());  // show1

        // 通过invoke调用方法
        show1.invoke(person);  // 我是公共的空参方法

        // 获取公共的带参方法
        Method show2 = clazz.getMethod("show2", int.class);
        // 调用方法
        show2.invoke(person, 100);  // 我是公共的带参方法，传入的参数是a, 其值为： 100

        // 获取私有带参方法
        Method show3 = clazz.getDeclaredMethod("show3", int.class, int.class);
        // 调用私有方法，必须做向下转型，invoke返回Object类型
        // 但这样调用会失败，因为目标方法是私有的
        //int sum = (int) show3.invoke(person, 10, 20);
        // 我们可以通过开启暴力反射，打开对私有方法的调用
        show3.setAccessible(true);
        int sum = (int) show3.invoke(person, 10, 20);
        System.out.println(sum);  // 30

        // 获取类中所有的成员方法，但不包含私有方法
        Method[] methods = clazz.getMethods();
        for (Method method : methods) {
            System.out.println(method);
        }
        // public void com.todever.demo18.Person.show1()
        // public void com.todever.demo18.Person.show2(int)
        // public final native void java.lang.Object.wait(long) throws java.lang.InterruptedException
        // public final void java.lang.Object.wait(long,int) throws java.lang.InterruptedException
        // public final void java.lang.Object.wait() throws java.lang.InterruptedException
        // public boolean java.lang.Object.equals(java.lang.Object)
        // public java.lang.String java.lang.Object.toString()
        // public native int java.lang.Object.hashCode()
        // public final native java.lang.Class java.lang.Object.getClass()
        // public final native void java.lang.Object.notify()
        // public final native void java.lang.Object.notifyAll()
    }
}

class Person {
    public Person() {}

    // 公共的空参方法
    public void show1() {
        System.out.println("我是公共的空参方法");
    }

    // 公共的带参方法
    public void show2(int a) {
        System.out.println("我是公共的带参方法，传入的参数是a, 其值为： " + a);
    }

    // 私有的带参方法
    private int show3(int a, int b) {
        System.out.println("我是私有的带参方法");
        return a + b;
    }
}
```

## 反射获取 setter 方法并使用

通过反射我们可以获取类的`setter`方法，并使用该方法为属性赋值

- `setter`方法的方法名由`set`和属性名（首字母大写）组成，如：`setName`，`setAge`

- `setter`方法有且只有一个参数，参数类型为属性的类型，如：`setName(String name)`

- `setter`方法为`public`修饰的方法，发射获取该方法可以使用`getMethod(String, Class<?>...)`

```java
public class Test {
    public static void main(String[] args) throws Exception {
        // 获取Person类的字节码文件
        Class clazz = Class.forName("com.todever.demo19.Person");
        // 通过反射获取Person类的构造方法，并创建该类的对象
        Constructor constructor = clazz.getConstructor();
        // 需要转型到Person
        Person person = (Person) constructor.newInstance();
        // 通过getMethod方法获取setter方法
        Method setName = clazz.getMethod("setName", String.class);
        setName.invoke(person, "Kaindy");

        System.out.println(person.getName());  // kaindy

    }
}

class Person {
    // 成员变量
    private String name;

    // 空参构造方法
    public Person() {};

    // 带参构造方法
    public Person(String name) {
        this.name = name;
    }

    // getter和setter
    public String getName() {
        return this.name;
    }

    public void setName(String name) {
        this.name = name;
    }

    // 重写toString

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

## 反射获取成员变量并使用

`Field`对象是域（属性、成员变量）对象，属于`java.base`模块下的`java.lang.reflect`包

我们可以通过`Class`对象获取属性

- `getField(String name)` 该方法返回一个`Field`对象，但仅仅包含公共属性，参数为想要获取的属性名

- `getDeclaredField(String name)` 该方法返回一个`Field`对象，它可以获取私有属性

- `getDeclaredFields()` 该方法返回类的所有属性组成的数组，它可以返回私有属性

`Field`常用的方法：

- `void set(Object obj, Object value)` 该方法设置`obj`对象的指定属性值为`value`

- `void setAccessible(boolean flag)` 该方法可以将属性的可访问性设置为指定的布尔值，即开启暴力反射

```java
public class Test {
    public static void main(String[] args) throws Exception {
        // 获取Person类的字节码文件对象
        Class clazz = Class.forName("com.todever.demo20.Person");
        // 获取空参构造方法
        // Constructor con = clazz.getConstructor();
        // 创建对象
        // Person person = (Person) con.newInstance();
        // 上面的两行代码可以合并成一行，我们叫做链式编程
        Person person = (Person) clazz.getConstructor().newInstance();

        // 获取name属性
        Field name = clazz.getField("name");
        // 通过set方法设置值
        name.set(person, "Kaindy");

        // 设置年龄，它是私有属性
        Field age = clazz.getDeclaredField("age");
        // 私有属性赋值需要开启暴力反射
        age.setAccessible(true);
        // 设置值
        age.set(person, 100);

        System.out.println(person);  // Person{name='Kaindy', age=100}

    }
}

class Person {
    // 公共属性
    public String name;

    // 私有属性
    private int age;

    // 空参构造方法
    public Person() {};

    // 重写toString方法
    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```
