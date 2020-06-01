## Java运算符的分类

<img src="https://s1.ax1x.com/2020/03/19/8ybx1S.md.png" style="zoom:75%" />

<img src="https://s1.ax1x.com/2020/03/19/8yOaFI.md.png" style="zoom:75%" />

## 算术运算符

运算符就是程序对常量和变量进行算术运算操作时使用的符号。它包含以下分类：

- `+` 加法运算
- `-` 减法运算
- `*` 乘法运算
- `/` 除法运算
- `%` 取模（取余）运算
- `++` 自增运算
- `--` 自减运算

**特别注意：**

- `/` 除法运算得到两个数据相除的商，在`Java`中整数除以整数的结果还是整数。
- `%` 取模（取余）运算得到两个数据相除的余数，可以用来判断两个数是否能整除。
- 如果相除的操作数有任意浮点数，那么结果就是浮点数 

在`Java`中，`+`运算符有两个作用，当加号两边是数值型数据时，进行数学中的加法运算，而如果操作数是字符型时，则会调用当前字符所对应的`ASCII`码来进行运算

自增（`++`）和自减（`--`）运算

如果是对某个变量进行单独运算，那么这两个运算符放在变量前和变量后都是一样

但如果是参与运算就不同了

- 在变量前，先自增（自减），再进行其他运算
- 在变量后，先以原值进行其他运算，再自增（自减）

``` java
int a = 5;
a++;  // 6
++a;  // 6

int b = a++;
System.out.println(a);  // 6
System.out.println(b);  // 5

int b = ++a;
System.out.println(a);  // 6
System.out.println(b);  // 6
```

## 赋值运算符

赋值运算符就是用于给变量赋值的运算符，它可以分为基本赋值运算符和扩展赋值运算符

<img src="https://s1.ax1x.com/2020/03/20/8gkDPK.png" style="zoom:75%" />

扩展赋值运算符的好处，就是省略了强制类型转换的操作，避免了一些因为类型问题引起的问题

```java
int a = 10;
a += 20;  // 相当于 a = a + 20
System.out.println(a);  // 30
```

## 关系运算符

关系运算符是用来描述两个变量之间关系的，它的运算结果都是布尔（`boolean`）值类型，要么是`true`，要么是`false`

<img src="https://s1.ax1x.com/2020/03/20/8gZcfP.png" style="zoom:75%" />

```java
int a = 10;
int b = 20;
int c = 10;

Systemout.out.println(a == b);  // false
Systemout.out.println(a == c);  // true
Systemout.out.println(a != b);  // true
Systemout.out.println(a != c);  // false
```

## 逻辑运算符

逻辑运算符用于判断"并且"、"或者"、"除非"等逻辑关系，它的两端一般连接的是值为布尔类型的关系表达式

常见的逻辑运算符有：

- `&&` 逻辑与 并且 表示所有表达式都为`true`时计算结果才为`true`，否则为`false`
- `||` 逻辑或 或者 表示所有表达式中，任意一个表达式为`true`，则计算结果就为`true`
- `!` 逻辑非 表示否定 将当前运算表达式计算结果取反

```java
System.out.println(true && true);  // true
System.out.println(true && false);  // false
System.out.println(false && true);  // false
System.out.println(false && false);  // false

System.out.println(true || true);  // true
System.out.println(true || false);  // true
System.out.println(false || true);  // true
System.out.println(false || false);  // false

System.out.println(!true);  // false
System.out.println(!false);  // true
```

## 三元运算符

三元运算符又叫"三目运算符"，它由三部分组成，格式如下：

(关系表达式) ? 表达式1 : 表达式2;

运算流程是，如果关系表达式结果为`true`，则运算后的结果是表达式1，否则如果关系表达式结果为`false`，则运算后的结果是表达式2

```java
// 计算两个整数的最大值
int a;
int b;
return a > b ? a : b;
```