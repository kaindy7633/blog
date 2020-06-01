# 一文入门Dart

> Flutter使用 Dart 语言开发，Dart是面向对象编程语言。

## 从 Hello World 开始

`Dart` 从 `main()` 函数开始执行

```dart
void main() {
	print("Hello World!");
}
```

点击绿色按钮开始执行，快捷键：`Shift + F10`

## 数据类型

`Dart` 中所有东西都是对象，包括数字、函数等。它们都继承自 `Object`，并且默认值都是 `null`。（数字也是）

`Dart` 支持以下数据类型：

- `Numbers`
- `Strings`
- `Booleans`
- `List` （`Array`）
- `Maps`

```dart
void main() {
	// Dart 中使用 var 声明变量
	// 可以使用单引号或双引号来定义字符串变量
	var str1 = "OK";
	String str2 = "It's OK!";
	
	// 使用三个单引号或双引号来定义多行字符串
	var str3 = """
		Dart Lang
		Hello World!"""；
		
	// assert 是 Dart 中内置的断言函数
	// 断言失败程序则立刻终止
	assert(name == "Wang Jianfei");
	
	// 新版Dart中支持使用 + 符号链接两个字符串
	// 使用 print 函数打印结果
    // 使用 $ 符号插入变量值
	print("Name: $name");
	
	// 声明原始字符串，使用 r
	print(r"换行符： \n");
	
	// Dart中数值是num，它有两个子类型，分别是 int和double
	// int是任意长度整数，double是双精度浮点数
	var hex = 0xDEADBEEF;
}
```

除了 `var` ，`Dart` 还使用 `const` 和 `final` 来定义常量

```dart
var i = 10;
const i = 10;
final i = 10;

int i = 10;
const int i = 10;
final int i = 10;
```

`const` 和 `final` 定义的都是变量，值不能改变，并且声明时必须初始化，它们之间的区别是：

- `const` 定义的是编译时常量 
- `final` 定义的值可以用变量来初始化

```dart
final time = new DateTime.now();   // OK
const time = new DateTime.now();   // Error, new DateTime.now() 不是const常量
```

## 函数

函数也是对象，当没有指定返回值时，函数返回 `null`

```dart
String sayHello(String name) {
	return 'Hello $name!';
}

// is 操作符用于判断对象是否为指定类型，如num、String
assert(sayHello is Function);
```

> 断言函数 assert() 在Debug模式下，当表达式的值为 false 时抛出异常，它还有第二个参数 message，用于在抛出异常时输出具体信息

函数名前面的类型参数表示函数返回的值类型，也可以省略，但建议明确函数的输入类型和返回类型。

如果函数只是返回一个表达式的值，则可以使用箭头语法，所以上面的函数可以改写如下：

```dart
String sayHello(String name) => 'Hello $name!';
```

下面的代码表示了函数闭包的用法，函数也可以返回一个函数

```dart
Function makeSubstract(num n) {
	return (num i) => n - i;
}

void main() {
	var x = makeSubstract(5);
	print(x(2));
}
```

在 `Dart` 中**函数也是对象**

```dart
var callbacks = [];
for (var i = 0; i < 3; i++) {
	callbacks.add(() => print('Save $i'));
}

callbacks.forEach((c) => c());		// 0, 1, 2
```

`Dart` 中支持两种可选参数，命名可选参数和位置可选参数，但这两种不能同时使用

- 命名可选参数使用大括号 `{}`，默认值使用冒号 `:`
- 位置可选参数使用方括号 `[]`，默认值使用等号 `=`

## 操作符和流程控制语句

在 `Dart`中， 操作符和流程控制与 `Java`、`C++` 中差不多，但有一些细节不同

- 取整，`Dart` 中使用 `~/` 操作符进行取整

	```dart
	int a = 3;
	int b = 2;
	print(a ~/ b); // 1
	```

- 级联，当要对一个单一的对象进行一系列操作时，可以使用级联操作符 `..`

	```dart
	class Person {
		String name;
		String country;
		void setCountry(String country) {
			this.country = country;
		}
		String toString() => 'Name: $name\nCountry: $country';
	}

	void main() {
		Person p = new Person();
		p..name = 'Wang'
		 ..setCountry('China');
		print(p);
	}
	```

- `If`语句，`if`语句的判断条件为 `bool` 值

	```dart
	if (i < 0) {
		print('i < 0');
	} else if(i == 0) {
		print('i == 0');
	} else {
		print('i > 0');
	}
	```

- 循环，一般使用`for`循环

	```dart
	for (int i = 0; i < 3; i++) {
		print(i);
	}
	```

	如果迭代的对象是容器，则可以使用`forEach`或`for...in`

	```dart
	var collection = [0, 1, 2];

	collection.forEach((x) => print(x));
	for(var x in collection) {
		print(x);
	}
	```

	`while`和`do...while`

	```dart
	while(boolean) {
		// do something...
	}

	do {
		// do something...
	} while(boolean)
	```

- `Switch...Case`, `switch`的参数可以是`num`或`String`

	```dart
	var command = 'OPEN';
	switch(command) {
		case 'CLOSED':
			break;
		case 'OPEN':
			break;
		default:
			print('Default');
	}
	```

- 异常处理，`Dart`不仅仅可以抛出`Exception`或`Error`，也可以抛出非空对象

	```dart
	throw new Exception('值必须大于0');
	throw '值必须大于0';
	```

	如果需要抛出多种类型的`Exception`，则由第一个`catch`分句来处理，如果`catch`未指定类型，那么它可以处理任意类型的异常

	```dart
	try {
		throw 'This is a Exception!';
	} on Exception catch(e) {
		print('Unkonow excepton: $e');
	} catch(e) {
		print('Unknown type: $e');
	}
	```

	如果希望无论是否发生异常都需要执行的代码语句，可以使用`finally`语句

```dart
try {
	throw 'This is a Exception!';
} catch(e) {
	print('Catch Exception: $e!');
} finally {
	print('Close');
}
```

## 类和对象

> `Dart`是一门使用类和单继承的面向对象语言，所有对象都是类的实例，并且所有类都是`Object`的子类。

### 定义

类的定义使用`class`关键字，如果未显式的声明构造函数，则`Dart`会默认创建一个空的构造函数，使用`new`关键字和构造函数来创建对象

```dart
class Point {
	num x;
	num y;
	num z;
}

void main() {
	var point = new Point();
	print(point.hasCode);
}
```

### 构造函数

使用`this`关键字将参数值直接进行传递，或者在参数后加冒号`:`再赋值

```dart
class Point {
	num x;
	num y;
	num z;

	Point(this.x, this.y, z) {
		this.z = z;
	}

	// 命名构造函数
	Point.fromeList(list):
		x = list[0], y = list[1], z = list[2]{
	}

	String toString() => 'x: $x y: $y z: $z';
}

void main() {
	var p1 = new Point(1, 2, 3);
	var p2 = new Point.fromeList([1, 2, 3]);
	print(p1);  // 默认调用toString函数·
}
```

### Getters & Setters

`Getter`和`Setter`是用来读写一个对象属性的方法，对象中每个字段都对应一个隐式的`Getter`和`Setter`，我们可以使用`get`和`set`关键字扩展功能，如果字段为`final`或`const`，则它只有一个`getter`方法

```dart
class Rectangle {
	num left;
	num top;
	num width;
	num height;

	Rectangle(this.left, this.top, this.width, this.height);

	num get right => left + width;
	set right(num value) => left = value - width;
	num get bottom => top + height;
	set bottom(num value) => top = value - height;
}

void main() {
	var rect = new Rectangle(3, 4, 20, 15);
	assert(rect.left == 3);
	react.right = 12;
	assert(rect.left == -8);
}
```

### 抽象类

在`Dart`中，类和接口是统一的，类就是接口，重写部分功能可以继承一个类，实现某些功能可以实现一个类。

使用`abstract`关键字定义抽象类，且抽象类不能被实例化，只可以被继承，抽象方法不需要关键字。

```dart
// 定义一个 Shape 类/接口
abstract class Shape {
	// 一个抽象方法
	num perimeter();
}

// 下面的Rectangle类实现了 Shape 接口
class Rectangle implements Shape {
	final num height, width;
	// 构造函数
	Rectangle(num this.height, num this.width);
	// 实现方法
	num perimeter() => 2 * height + 2 * width;
}

// 下面定义的Square类继承 Recdtangle类
class Square extends Rectangle {
	Square(num size): super(size, size);
}
```

### 继承和实现

实现的关键字为：`implements`，继承的关键字为：`extends`

```dart
abstract class Person {
	String greet(who);
}

class Student implements Person {
	String name;
	Student(this.name);

	String greet(who) => 'Student: I am $name!';
}

class Teacher implements Person {
	String name;
	Teacher(this.name);

	String greet(who) => 'Teacher: I am $name!';
}

void main() {
	Person student = new Student('Wang');
	Person teacher = new Teacher('Lee');

	print(student.greet('Chen'));
	print(teacher.greet('Chen'));
}
```

`Dart`中的继承是单继承，子类可以继承父类的非私有变量。

## 容器

### StringBuffer

`StringBuffer`并不是容器，它可以高效的构建多个字符串，使用`write`方法写入内容

```dart
StringBuffer sb = new StringBuffer();

sb.write("Use a StringBuffer ");
sb.writeAll(['for ', 'efficient ', 'string ', 'creation ']);
sb..write('if you are ')..write('building lots of string.');

print(sb.toString());
sb.clear();
```

### List

`List`列表，就是常见的数组，它具有添加、索引、删除等方法

```dart
// 使用 List 构造函数创建
var vegetables = new List();

// 字面量方式创建
var fruits = ['apples', 'oranges'];

// 添加元素
fruits.add('kiwis');

// 添加多个元素
fruits.addAll(['grapes', 'bananas']);

// 获取List长度
assert(fruits.length == 5);

// 利用索引获取元素
assert(fruits[0] == 'apples');

// 查找某个元素的索引
assert(fruits.indexOf('apples') == 0);

// 利用索引删除某个元素
var appleIndex = fruits.indexOf('apples');
fruits.removeAt(appleIndex);
assert(fruits.length == 4);

// 删除所有元素
fruits.clear();
assert(fruits.length == 0);
```

使用`sort`对`List`进行排序，其参数是一个比较两个对象的函数

```dart
var fruits = ['bananas', 'apples', 'orages'];
fruits.sort((a, b) => a.compareTo(b));

print(fruits);  // [apples, bananas, oranges]
```

`List`及其他容器也可以指定其参数（元素）的类型

```dart
// 下面创建的List只能包含String类型的元素
var fruits = new List<String>();

fruits.add('apples');
assert(fruits[0] is String);

fruits.add(5);  // Error，不能添加 int 类型的元素
```

### Set

`Set`集合中的元素是无序的，且所有元素都具有唯一性（无重复元素），因为它是无序的，所以它不能像`List`那样利用索引来访问元素

```dart
var ingredients = new Set();

ingredients.addAll(['gold', 'titanium', 'xenon']);
assert(ingredients.length == 3);

// 添加已存在的元素是无效的
ingredients.add('gold');
assert(ingredients.length == 3);

// 删除元素
ingredients.remove('gold');
assert(ingredients.length == 2);

// 检查Set中是否包含某个元素
assert(ingredients.contains('titanium'));

// 检查Set中是否包含多个元素
assert(ingredients.containsAll(['titanium', 'xenon']));
ingredients.addAll(['gold', 'titanium', 'xenon']);

// 获取两个集合的交集
var nobleGases = new Set.from(['xenon', 'argon']);
var intersection = ingredients.intersection(nobleGases);
assert(intersection.length == 1);
assert(intersection.contains('xenon'));

// 检查一个Set是否是另一个Set的子集
var allElements = ['hydrogen', 'helium', 'lithium', 'beryllium', 'glod', 'titanium', 'xenon'];
assert(ingredients.isSubsetOf(allElements));
```

### Map

`Map`映射，也称之为字典，它是一种无序的键值对容器

```dart
// 声明Map
var hawaiianBeaches = {
	'oahu': ['waikiki', 'kailua', 'waimanalo'],
	'big island': ['wailea bay', 'pololu beach'],
	'kauai': ['hanalei', 'poipu']
};

var serachTerms = new Map();

// 指定键值对的参数类型
var nobleGases = new Map<int, String>();

// Map中的赋值
nobleGase[54] = 'dart';

// 检查Map是否包含某个Key
assert(nobleGases.containsKey(54));

// 删除某个键值对
nobleGases.remove(54);
```

我们可以使用`getKeys`和`getValues`方法获取所有`Key`或所有`Values`的迭代器

```dart
var keys = hawaiianBeaches.getKeys();
assert(keys.length == 3);
assert(new Set.from(keys).contains('oahu'));

var values = hawaiianBeeaches.getValues();
assert(values.length == 3);

// 迭代器中的any和every函数用来检测迭代器中的数据
// 使用any时，如果迭代器中的任意一个元素返回true，则any返回true
// 使用every时，迭代器中所有元素都返回true时才返回true，否则返回false
assert(values.any((v) => v.indexOf('waikiki') !- -1));

// 可以使用forEach来遍历数据
hawaiianBeaches.forEach((k, v) {
	print('I want to visit $k and swim at $v');
});

// 检索是否包含某个Key或Value
assert(hawaiianBeaches.containsKey('oahu'));
```

### 迭代

`List`、`Set`和`Map`都继承自`Iterable`，是可以迭代的

```dart
// 如果目标对象是容器，那么可以使用forEach或for-in进行迭代
var collection = [0, 1, 2];
collection.forEach((x) => print(x));

for(var x in collection) {
	print(x);
}
```

## 库的引用

`Dart`可以导入一个库来使用它所提供的功能，也可以自定义一个库。在`Dart`中任何一个文件都是一个库，即便没有使用关键字`library`声明。

### import

`import`语句用来导入一个库

```dart
// dart:前缀表示Dart的标准库，如果dart:io、dart:html
import 'dart:math';

// 也可以使用路径
import 'lib/student/student.dart';

// Pub包管理系统，使用前缀package
import 'package:args/args.dart';
```

当有命名冲突时，可以使用`as`关键字来使用命名空间

```dart
import 'lib/student/student.dart' as Stu;

Stu.Student s = new Stu.Student();
```

`show`关键字和`hide`关键字可以显示或隐藏库中的某些成员

```dart
import 'lib/student/student.dart' show Student, Person;
import 'lib/student/student.dart' hide Person;
```

### library

`library`用来定义库。

```dart
library person;
```

### export

`export`关键字用于导出一个库

```dart
library math;

export 'random.dart';
export 'point.dart';
```
