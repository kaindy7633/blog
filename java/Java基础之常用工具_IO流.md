### 异常

> 异常，即非正常情况，通俗的说，异常就是程序出现的错误

异常的顶层是`Throwable`类，它分为`Exception`和`Error`

- `Exception` 表示合理的应用程序可能需要捕获的问题，它是可预料的，如：`NullPointerException`空指针异常

- `Error` 表示合理的应用程序不应该试图捕获的问题，也就是不可预料的，如：`StackOverFlowError`栈内存溢出

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/03/25/8jNpJ1.png" style="zoom:75%" />
</p>

### 异常处理

在 JVM 中有默认的异常处理方式，即在控制台打印错误信息，并终止程序运行

在开发中，处理异常有两种方式：

- `try...catch` 捕获，自己处理

  ```java
  try {
  	// 尝试执行的代码
  } catch (Exception e) {
  	// 出现异常之后的处理代码
  } finally {
  	// 无论是否出现异常都会执行的代码 一般用于关闭资源等
  }
  ```

- `throws` 抛出，交给调用者处理

  ```java
  // 会抛出异常的方法，调用者必须处理它抛出的异常
  public static void show() throws Exception {
  	// 要执行的代码
  }
  ```

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/03/25/8jUGjK.png" style="zoom:75%" />
</p>

### IO 流

IO 流即流入（`Input`）输出（`Output`），IO 流指的是数据像连绵的流体一样进行传输，在`Java`中，IO 流就是数据传输的方式

IO 流按数据流向分为**输入流**和**输出流**两种，如果按照操作方式，就分为**字节流**和**字符流**两种

字节流分为`InputStream`和`OutputStream`，字符流分为`Reader`和`Writer`，它们都是抽象类

**字符流**

字符流即按字符读写数据的 IO 流，它分为`Reader`和`Writer`。

`Reader`字符流有两个子类，一个是`FileReader`，它是一种普通的字符流读取方式，另一种是`BufferedReader`，它是一种高效的字符流读取方式

`Writer`字符流有两个子类，一个是`FileWriter`，它是一种普通的字符流写入方式，另一种是`BufferedWriter`，它是一种高效的字符流写入方式

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/03/25/8jLtrq.png" style="zoom:75%" />
</p>

**字节流**

字节流即按字节读写数据的 IO 流，它分为`InputStream`和`OutputStream`，它们都是抽象类

`InputStream`有两个子类，一个是`FileInputStream`，另一个是高效的`BufferedInputStream`

`OutputStream`有两个子类，一个是`FileOutputStream`，另一个是高效的`BufferedOutputStream`

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/03/25/8jOx76.png" style="zoom:75%" />
</p>

### File 类

在`Java`中，一个`File`对象代表磁盘上的某个文件或文件夹

它的构造方法主要有三个:

- `File(String pathname)` 传入文件路径

- `File(String parent, String child)` 分别传入父目录和子目录

- `File(File parent, String child)` 先将父目录转为`File`对象，然后再跟子目录字符串一起传入

有了`File`对象之后我们就可以调用其方法：

```java
/**
 *	创建文件对象的三种方式
 */
import java.io.File;

// 全路径写法
File file = new File("E:\\test\\test.txt");  // 全路径写法 \\ 表示路径分隔符，需要使用\来转义
File file2 = new File("E:/test/test.txt");   // 使用正斜杠方式

// 文件路径 + 文件名的写法
File file2 = new File("E/test/", "test.txt");

// 文件路径对象 + 文件名写法
File file3 = new File("E/test/");
File file4 = new File(file3, "test.txt");
```

**File 类中创建的方法**

- `createNewFile()` 创建文件

```java
// 创建对象
File file = new File("E:/test.txt");

// 调用createNewFile()方法创建此文件，返回一个布尔值，表示是否成功创建
// 如果创建的文件不存在则创建，如果存在则返回false
boolean b1 = file.createNewFile();
```

- `mkdir()` 或 `mkdirs()` 创建目录

```java
// 创建对象
File file6 = new File("E:/NewDir");

// 调用mkdir()方法创建目录，返回一个布尔值，表示是否创建成功
// mkdir只能创建单级目录
boolean b2 = file6.mkdir();

// 创建对象
File file7 = new File("E:/NewDir1/a/b/c");

// mkdirs()可以创建多级目录,当然也可以创建单级目录，所以它使用的比较多一些
boolean b3 = file7.mkdirs();
```

- `isDirectory()` 判断`File`对象是否为目录

```java
// 创建对象
File file = new File("E:/NewDir");

// 判断是否为目录
boolean flag = file.isDirectory();  // true || false
```

- `isFile()` 判断`File`对象是否为文件

```java
// 创建对象
File file = new File("E:/NewDir");

// 判断是否为文件
boolean flag = file.isFile();  // true || false
```

- `exists()` 判断对象是否存在

```java
// 创建对象
File file = new File("E:/NewDir");

// 判断是否存在
boolean flag = file.exists();  // true || false
```

**File 类中获取功能的方法**

- `getAbsolutePath()` 获取文件对象的绝对路径，即以盘符开头的路径，如：`D:/test.txt`

- `getPath()` 获取文件的相对路径，即一般是相对于当前项目路径，如：`test.txt`

- `getName()` 获取文件名

- `list()` 获取指定目录下所有文件或文件夹的名称，返回的是一个数组

- `listFiles()` 获取指定目录下所有文件或文件夹的 File 对象数组

### 字符流读写

字符流读取的顶层类是`Reader`，但它是一个抽象类，所以实例化对象必须使用它的子类`FileReader`

**按单个字符读取**

创建字符流读文件对象
`Reader reader = new FileReader("readme.txt");`

调用`read()`方法读取数据，该方法每次读取一个字符，返回该字符代表的整数，若到达流的末尾，则返回`-1`，这里需要异常处理，通常可以使用`try...catch`或`throws IOException`的方式，最后需要调用`close()`方法关闭读取流

```java
public static void main(String[] args) throws IOException {
	Reader reader = new FileReader("lib/test.txt");
	// int ch1 = reader.read();  // 97 -> a
	while ((ch = reader.read()) != -1) {
		System.out.println(ch);
	}
	reader.close();
}
```

**读取字符数组**

```java
public static void main(String[] args) throws IOException {
	Reader reader = new FileReader("lib/test.txt");
	// 定义字符数组
	char[] chs = new char[3];
	int len1 = reader.read(chs);
	System.out.println(chs);   // abc
	System.out.println(len1);  // 3
	reader.close();
}
```

**字符流写数据**

第一种写法，写入单个字符

- 创建字符流写文件对象，`Writer writer = new FileWrite("dest.txt")`

- 调用`write()`方法写入字符 `writer.write("中")`

- 异常处理： `try...catch` 或 `throws IOException`

- 关闭资源：`writer.close()`

第二种写法，写入字符数组

- 创建字符流写文件对象，`Writer writer = new FileWriter("dest.txt")`

- 调用方法写入数据：

  ```java
  char[] chs = { '中', '国', '人' };
  writer.write(chs);
  ```

- 异常处理：`throw IOException`

- 关闭资源：`writer.close()`

第三种写法，直接写入一个字符串 `writer.write("我是中国人");`

**实现文件内容拷贝**

```java
// 按单个字符进行读写
public static void main(String[] args) throws IOException {
	FileReader fr = new FileReader("lib/1.txt");
	FileWriter fw = new FileWriter("lib/2.txt");

	int len;
	while((len = fr.read()) != -1) {
		fw.write(len);
	}

	fr.close();
	fw.close();
}

// 按字符数组进行读写
public static void main(String[] args) throws IOException {
	FileReader fr = new FileReader("lib/1.txt");
	FileWriter fw = new FileWriter("lib/2.txt");

	char[] chs = new char[1024];
	int len;
	while((len = fr.read()) != -1) {
		fw.write(chs, 0, len);
	}

	fr.close();
	fw.close();
}
```

**通过字符缓冲流拷贝文件**

```java
public static void main(String[] args) throws IOException {
	BufferedReader br = new BufferedReader(new FileReader("lib/1.txt"));
	BufferedWriter bw = new BufferedWriter(new FileWriter("lib/2.txt"));

	int len;
	while((len = br.read()) != -1) {
		bw.write(len);
	}

	br.close();
	bw.close();
}
```

**读取一行数据**

```java
public static void main(String[] args) throws IOException {
	BufferedReader br = new BufferedReader(new FileReader("lib/1.txt"));
	BufferedWriter bw = new BufferedWriter(new FileWriter("lib/2.txt"));

	String str;
	// readline() 读取一行数据
	while((str = br.readline()) != null) {
		bw.write(str);
		bw.newLine();  // 跨平台写入换行符
	}

	br.close();
	bw.close();
}
```

### 字节流读写

在字节流中有两个关键类：`InputStream`和`OutputStream`，分别是字节输入流和字节输出流，它们都是抽象类，在实际应用中，必须使用它们的实现类，即`FileInputStream`和`FileOutputStream`，它们是普通字节流读写

**普通字节流-按单个字节读写**

按单个字节进行读写流程如下：

- 创建字节流读文件对象：

  ```java
  InputStream is = new FileInputStream("abc.jpg");
  ```

- 创建字节流写文件对象：

  ```java
  OutputStream os = new FileOutputStream("D:\\abc_copy.jpg");
  ```

- 使用`while`循环读写数据：

  ```java
  int b;
  while((b = is.read()) != -1) {
  	os.write(b);
  }
  ```

- 添加异常处理： `throws IOException`

- 关闭资源：

  ```java
  is.close();
  os.close();
  ```

利用字节流读写完成图片的拷贝，代码如下：

```java
public static void main(String[] args) throws IOException {
	// 创建字节流读对象
	FileInputStream fis = new FileInputStream("lib/abc.jpg");
	// 创建字节流写对象
	FileOutputStream fos = new FileOutputStream("lib/abc_copy.jpg");
	// 循环读取字节并写入新文件
	int len;
	while ((len = fis.read()) != -1) {
		fos.write(len);
	}
	// 关闭资源
	fis.close();
	fos.close();
}
```

**普通字节流-按字节数组读写**

字节流按字节数组进行读写的操作与上面按单字节进行读写的操作有两点不同

- 需要额外创建一个字节数组，如： `byte[] b = new byte[2048]`，字节数组的长度必须是`1024`的整数倍

- 在进行写操作调用目标对象的`write`方法时，必须传入 3 个参数，分别是定义的字节数组，如上面的`b`，从哪一个索引位置开始写，这里是`0`，写入的终止位置，即读写到的`len`

  ```java
  int len;
  while ((len = is.read(bys)) != -1) {
  	os.wirte(bys, 0, len);
  }
  ```

其他操作都是一样的，演示代码如下：

```java
public static void main(String[] args) throws IOException {
	// 创建字节流读对象
	FileInputStream fis = new FileInputStream("lib/abc.jpg");
	// 创建字节流写对象
	FileOutputStream fos = new FileOutputStream("lib/abc_copy.jpg");
	// 创建字节数组
	byte[] bys = new byte[1024];
	// 循环读取并写入新文件
	int len;
	while ((len = fis.read(bys)) != -1) {
		fos.write(bys, 0, len);
	}
	// 关闭资源
	fis.close();
	fos.close();
}
```

**高效字节流-字节缓冲流读写**

字节缓冲流读写操作，使用的是`InputSteam`和`OutputStream`的实现类`BufferedInputSteam`和`BufferedOutputStream`，此方式与上面不同的是，创建新文件是根据目标文件动态生成的，且是高效的

与上面的创建方式不同的在于创建读写对象：

- 创建字节缓冲流读读文件对象：

  ```java
  BufferedInputStream bis = new BufferedInputStream(
  	new FileInputStream("lib/abc.jpg");
  )
  ```

- 创建字节缓冲流写文件对象：

  ```java
  BufferedOutputStream bos = new BufferedOutputStream(
  	new FileOutputStream("lib/abc_copy.jpg")；
  )
  ```

演示如下：

```java
public static void main(String[] args) throws IOException {
	// 创建字节缓冲流读对象
	BufferedInputStream bis = new BufferedInputStream(
		new FileInputStream("lib/abc.jpg")
	);
	// 创建字节缓冲流写对象
	BufferedOutputStream bos = new BufferedOutputStream(
		new FileOutputStream("lib/abc_copy.jpg")
	);
	// 循环读写文件
	int len;
	while ((len = bis.read()) != -1) {
		bos.write(len);
	}
	// 关闭资源
	bis.close();
	bos.close();
}
```
