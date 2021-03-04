<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Scanner类](#scanner%E7%B1%BB)
- [流程控制结构](#%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6%E7%BB%93%E6%9E%84)
- [流程控制之选择结构](#%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6%E4%B9%8B%E9%80%89%E6%8B%A9%E7%BB%93%E6%9E%84)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Scanner类

先来看看`Scanner`类吧，使用`Scanner`可以从外部接收用户在控制台输入的数据，它就像一个扫描器，并将扫描到的数据存入我们定义的变量中。

使用`Scanner`类一般分为三步：

```java
// 第一步：导入包
import java.util.Scanner;

public class ScannerDemo {
	public static void main(String[] args) {
		// 第二步：创建scanner对象
		Scanner sc = new Scanner(System.in);

		// 第三步：接收数据
		int i = sc.nextInt();  // nextInt只能接收整数类型的值
	}
}
```

## 流程控制结构

程序的结果跟代码的执行顺序紧密相关，通过使用一些特定的语句控制代码的执行顺序从而完成特定的功能，这就是流程控制结构。

流程控制结构的分类：

- 顺序结构

  顺序结构按照代码的顺序从上往下、从左往右一次执行代码结构，它是最简单的流程控制结构，不需要特定的语句，大多数代码都是这样执行的。

- 选择（判断）结构
- 循环结构

## 流程控制之选择结构

选择结构根据不同的条件选择不同的代码来执行代码结构，它需要先判断条件是否成立，如果成立执行一部分代码，反之执行另外一段代码，所以，选择结构也称为判断结构。

选择结构的分类：

- `if` 做区间值得判断
  ```java
  // 第一种格式
  if(关系表达式) {
	  // 语句体1
  }

  // 第二种格式
  if(关系表达式) {
	  // 语句体1
  } else {
	  // 语句体2
  }

  // 第三种格式
  if(关系表达式1) {
	  // 语句体1
  } else if(关系表达式2) {
	  // 语句体2
  }
  ...
  else {
	  // 语句体n+1
  }
  ```
- `switch` 做固定值的判断
  ```java
  switch(表达式) {
	  case 值1:
		  语句体1；
		  break;
	  case 值2：
		  语句体2；
		  break;
	  ...
	  default:
		  语句体n+1;
		  break;
  }
  ```



