### 集合

> 集合简称集，它是用来存储多个元素的容器

集合跟数组很相似，他们的区别如下：

- 集合只能存储引用类型的元素，如果是基本类型会自动装箱，将基本类型转换成对应的包装类，而数组既可以存储基本类型，也可以存储引用类型

- 集合的元素个数（容量）是不固定的，可以任意扩容，而数组从定义之时起就固定了，不能改变容量

- 集合的优势在于不受容器大小的限制，可以随时添加、删除元素，并提供了大量操作元素的方法，如判断、获取等

**Java 的集合体系**

在`Java`中，集合分为单列集合（`Collection`）和多列集合（`Ma`）两种

<p style="text-align:center">
	<img src="https://s1.ax1x.com/2020/03/24/8Ol7jA.md.png" style="zoom:50%" />
</p>

### List

`List`属于单列集合，它的特点就是元素可重复、有序（存取顺序相同）

`List`集合属于接口，要使用它必须创建其子类对象，如： `List list = new ArrayList()`

```java
/**
 * 1. 创建集合对象
 * 2. 创建元素对象
 * 3. 将元素对象添加到集合对象中
 * 4. 遍历集合
 */
List list = new ArrayList();
Student stu1 = new Student("乔峰", 41);
Student stu2 = new Student("乔峰", 41);
Student stu3 = new Student("虚竹", 38);
Student stu4 = new Student("段誉", 26);

// 添加元素对象到List集合中
list.add(stu1);
list.add(stu2);
list.add(stu3);
list.add(stu4);

// 获取List集合中的元素
Object obj = list.get(2);  // Student{name='虚竹', age=38}

// 通过for循环遍历List集合
for (int i = 0; i < list.size(); i++) {
	System.out.println(list.get(i));
}
```

### 增强 For 循环和迭代器

增强`for`循环用来简化数组和集合的遍历操作，格式如下：

```java
for (数据类型 变量名 : 数组或集合对象) {
	// 循环体
}
```

```java
...
for (Object o : list) {
	System.out.println(o);
}
...
```

**迭代器**

迭代就是对过程的重复，迭代器是遍历`Collection`集合的通用方式，可以在对集合遍历的同时进行添加、删除等操作

迭代器中一般有两个常用方法：

- `next()` 该方法返回迭代的下一个元素对象

- `hasNext()` 该方法判断是否仍有元素可以迭代，有则返回`true`，否则返回`false`

```java
// 1. 创建集合对象
List list = new ArrayList();

// 2. 创建元素对象并添加到集合对象中
list.add("a");  // 自动装箱
list.add("b");  // 自动装箱
list.add("c");  // 自动装箱

// 使用迭代器遍历List
Iterator it = list.iterator();
while(it.hasNext()) {
	String s = (String) it.next();  // 向下转型
	System.out.println(s);
}
```

这里有一个开发中常见的需求，需要判断遍历中是否有某个特定的字符，如果有，则进行一系列的操作，比如这里需要判断是否有字符串`b`，如果有则往`List`中插入另外一个字符串

```java
// 在while循环中判断
...

while(it.hasNext()) {
	String s = (String) it.next();
	// 重点：这里的s是个变量，一般使用常量和变量进行比较时，通常我们将它们反转过来
	// 意思就是用常量去调用equals方法
	// if (s.equals("b")) {
	//	// 执行一些操作
	// }

	// 应该这样写：
	// 好处时可以规避空指针异常的问题
	if ("b".equals(s)) {
		// 执行一些操作
	}
}

...
```

当我们进行以上操作时，比如在迭代`List`的同时，还要进行添加、删除等操作，会报并发异常，意思就是说迭代的同时不能做其他的操作，这时我们就需要**列表迭代器**了

**列表迭代器**

它是`List`体系独有的遍历方式，可以在对集合进行遍历的同时，做添加、删除等操作，列表迭代器的方法是：`listIterator()`

```java
...
ListIterator lit = list.listIterator();
while (lit.hasNext()) {
	String s = (String) lit.next();
	if ("b".equals(s)) {
		lit.add("java");
	}
}

System.out.println(list);  // [a, b, java, c]
...
```

> 总结：普通的迭代器在遍历集合的同时不能添加或删除元素，否则会报：并发修改异常，列表迭代器（`listIterator`）在遍历集合的同时可以修改集合中的元素（添加、删除等），但必须使用列表迭代器中的方法

### 泛型

泛型即泛指任意类型，又叫参数化类型（`ParameterizedType`），对具体类型的使用起到辅助作用，类似于方法的参数

这里要了解一下集合类泛型，它表示该集合中存放指定类型的元素，比如，我们给一个`List`集合添加泛型`String`，表示该集合中，只能添加`String`类型的元素，如：

```java
List<String> list = new ArrayList<String>();
```

由此可以看出，集合类泛型的好处在于类型更安全，且避免了类型转换

```java
// 1. 创建带有泛型的集合对象
List<String> list = new ArrayList<String>();

// 2. 创建元素对象并添加到集合对象中
list.add("a");
list.add("b");
list.add("c");
// list.add(10);  报错...

// 3. 遍历集合
for (String s : list) {
	System.out.println(s);  // a b c
}
```

**注意：** 泛型一般只和集合类结合使用，它是 JDK5 的新特性，在 JDK7 之后，后面的泛型可以不写，如：

`List<String> list = new ArrayList<>();`

### Collections 工具类

`Collections`工具类是针对集合进行操作的一系列工具类，使用它主要是使用它内置的各种方法，它们都是静态方法

- `sort(List<T>)` 该方法根据元素的自然顺序，将指定列表按升序进行排列

- `max(Collection<T>)` 该方法返回集合中的最大的元素

- `reverse(List<T>)` 该方法反转`List`中的集合元素

- `shuffle(List<T>)` 该方法使用默认的随机源随机置换指定的列表

```java
// 1. 创建集合对象
List<Integer> list = new ArrayList<>();
// 2. 添加元素
list.add(1);
list.add(3);
list.add(3);
list.add(4);
list.add(8);
list.add(6);
list.add(9);
list.add(2);

System.out.println(list);  // [1, 3, 3, 4, 8, 6, 9, 2]

// 获取集合中最大的元素
Integer max = Collections.max(list);  // 9

// 对集合进行升序排列
Collections.sort(list);  // [1, 2, 3, 3, 4, 6, 8, 9]

// 对集合元素进行翻转操作
Collections.reverse(list);  //  [2, 9, 6, 8, 4, 3, 3, 1]

// 随机置换，相当于洗牌操作
Collections.shuffle(list);  // [2, 3, 4, 9, 8, 6, 3, 1]
```

### Set

`Set`集合是单列集合，它的特点是元素不可重复，且是无序的

它是一个接口，所以若要使用它，必须创建其子类对象`HashSet`，如：`Set<T> set = new HashSet<>()`

当`Set`集合创建完成后，就可以使用`add`方法向集合中添加元素，并使用迭代器遍历集合

```java
// 1. 创建Set集合对象
Set<Student> set = new HashSet<>();

// 2. 向Set集合中添加Student元素
set.add(new Student("1", "张三丰"));
set.add(new Student("2", "张无忌"));
set.add(new Student("3", "章子怡"));

// 3. 遍历集合
Iterator<Student> it = set.iterator();
while (it.hasNext()) {
	Student stu = it.next();
	System.out.println(stu);
}

/**
 * Student{id='1', name='张三丰'}
 * Student{id='3', name='章子怡'}
 * Student{id='2', name='张无忌'}
 */
```

### Map

`Map`是一种双列集合，元素由键值对（`Entry`）构成，包含了`key`和`value`，`key`是不能重复的，但`value`是可以重复的

`Map`是一个接口类型，所以使用时需要创建其子类对象`HashMap`，如：

```java
Map<T1, T2> map = new HashMap<>();
```

泛型`T1`表示键的类型，泛型`T2`表示值得类型

当创建完`Map`集合之后，就可以往集合中添加元素了，在`Map`中添加元素使用`put()`方法，遍历`Map`,需要先获取所有的`key: keySet()`，也就是由所有的键组成的单列集合，然后通过`key`，并使用方法`get()`，获取到对应的`value`

```java
// 1. 创建Map集合
Map<Integer, Student> map = new HashMap<>();

// 2. 向map集合中添加元素
map.put(1, new Student("1", "张三"));
map.put(2, new Student("2", "李四"));
map.put(3, new Student("3", "王五"));

System.out.println(map);  // {1=Student{id='1', name='张三'}, 2=Student{id='2', name='李四'}, 3=Student{id='3', name='王五'}}

// 根据键，获取值
Student s1 = map.get(2);  // Student{id='2', name='李四'}

// 遍历Map集合，双列集合不能直接遍历，需要先把键转换成单列集合
Set<Integer> keys = map.keySet();
// 使用迭代器获取key组成的Set集合
Iterator<Integer> it = keys.iterator();
while (it.hasNext()) {
	Integer key = it.next();
	// 根据键获取值
	Student stu = map.get(key);
	System.out.println(stu);
	/**
     * Student{id='1', name='张三'}
     * Student{id='2', name='李四'}
     * Student{id='3', name='王五'}
     */
}
```

### 综合示例：斗地主发牌

```java
import java.util.*;

public class SendPokerTest {
    public static void main(String[] args) {
        // 第一步： 创建一副牌
        // 定义双列集合，键是编号，值是牌的名称
        Map<Integer, String> pokers = new HashMap<>();

        // 定义单列集合，用于存放所有牌的编号
        List<Integer> list = new ArrayList<>();

        // 定义牌的编号，从0开始
        int num = 0;

        // 创建具体的牌
        String[] colors = { "♠", "♥", "♣", "♦" };  // 4种花色
        String[] numbers = { "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A", "2" };

        // 通过嵌套循环，创建普通牌
        for (String number : numbers) {     // 外循环，获取所有的点数
            for (String color : colors) {   // 内循环，获取素有的花色
                String poker = color + number;
                // 将牌的编号和具体的牌放入双列集合种
                pokers.put(num, poker);
                // 将牌的编号放入单列集合中
                list.add(num);
                // 编号自增
                num++;
            }
        }

        // 添加小大王，并让num自增
        pokers.put(num, "小王");
        list.add(num++);
        pokers.put(num, "大王");
        list.add(num);

        // 第二步：洗牌
        // 使用集合类Collections中的shuffle方法，随机打乱list
        Collections.shuffle(list);

        // 第三步： 发牌
        // 使用list集合中的元素的索引与3取余，如果是0，发给第1个玩家、如果是1发给第二个玩家，如果是3发给第三个玩家
        // 创建4个List集合，分别存放玩家1、玩家2、玩家3和底牌
        List<Integer> player1 = new ArrayList<>();
        List<Integer> player2 = new ArrayList<>();
        List<Integer> player3 = new ArrayList<>();
        List<Integer> lastPocker = new ArrayList<>();

        // 遍历pokers集合，根据索引进行发牌操作
        for (int i = 0; i < list.size(); i++) {
            Integer pokerNum = list.get(i);
            if (i >= list.size() - 3) {  // 最后三张牌
                lastPocker.add(pokerNum);
            } else if (i % 3 == 0) {
                player1.add(pokerNum);
            } else if (i % 3 == 1) {
                player2.add(pokerNum);
            } else if (i % 3 == 2) {
                player3.add(pokerNum);
            }
        }

        // 第四步：看牌
        System.out.println("玩家1的牌面是： " + printPoker(player1, pokers));
        System.out.println("玩家2的牌面是： " + printPoker(player2, pokers));
        System.out.println("玩家3的牌面是： " + printPoker(player3, pokers));
        System.out.println("底牌的牌面是： " + printPoker(lastPocker, pokers));

        /**
         * 玩家1的牌面是： ♥5 ♣5 ♦5 ♥6 ♣6 ♠7 ♦7 ♣8 ♠9 ♦9 ♣10 ♣J ♦J ♦Q ♣K ♣A 小王
         * 玩家2的牌面是： ♥3 ♦3 ♥4 ♣4 ♥7 ♣7 ♥8 ♥9 ♣9 ♠10 ♦10 ♠J ♥K ♥A ♦A ♠2 ♦2
         * 玩家3的牌面是： ♠3 ♣3 ♠4 ♦4 ♠5 ♦6 ♠8 ♦8 ♥10 ♥Q ♣Q ♠K ♦K ♠A ♥2 ♣2 大王
         * 底牌的牌面是： ♠6 ♥J ♠Q
         */
    }

    /**
     * 看牌方法
     * @parmas List<Integer>
     * @parmas Map<Integer, String>
     * @return String
     */
    public static String printPoker(List<Integer> nums, Map<Integer, String> pokers) {
        //定义字符串序列，展示拿到的牌
        StringBuilder pokerList = new StringBuilder();

        // 对序号列表中元素进行升序排列
        Collections.sort(nums);

        // 遍历编号列表，在Map中查找
        for (Integer num : nums) {
            String poker = pokers.get(num);
            pokerList.append(poker + " ");
        }
        String str = pokerList.toString();
        return str.trim();
    }
}
```
