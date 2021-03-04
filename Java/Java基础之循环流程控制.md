<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [循环结构](#%E5%BE%AA%E7%8E%AF%E7%BB%93%E6%9E%84)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 循环结构

循环就是事物周而复始的变化，循环结构使得一部分代码按照次数或一定条件反复执行。

循环结构一般分为三大类：

- `for`循环
- `while`循环
- `do...while`循环

`for`循环的格式如下：

```java
for(初始化语句;判断条件语句;控制条件语句) {
	// 循环体
}
```

`while`循环语句的格式：

```java
while(判断条件语句) {
	循环体语句;
	控制条件语句;
}
```

`do...while`循环语句的格式：

```java
do {
	循环体语句;
	控制条件语句;
} while(判断条件语句);
```

**注意：** `while`小括号后的分号不可以省略，`do...while`循环至少会执行一次。

`break`表示中断语句执行，它可以直接跳出循环。
`continue`表示中断本次循环，直接进行下一次循环

