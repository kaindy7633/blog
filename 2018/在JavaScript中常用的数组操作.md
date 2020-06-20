<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [改变原始数据的操作方法](#%E6%94%B9%E5%8F%98%E5%8E%9F%E5%A7%8B%E6%95%B0%E6%8D%AE%E7%9A%84%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95)
- [不会修改原始数组的操作方法](#%E4%B8%8D%E4%BC%9A%E4%BF%AE%E6%94%B9%E5%8E%9F%E5%A7%8B%E6%95%B0%E7%BB%84%E7%9A%84%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95)
- [使用](#%E4%BD%BF%E7%94%A8)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 数组操作在前端工程师的日常工作中随处可见，下面来总结一些常见的数组操作

## 改变原始数据的操作方法

- `push` 向数组末尾添加元素，并返回新的长度
- `pop` 删除数组最后一个元素并返回删除的元素
- `unshift` 向数组开头添加元素，并返回数组新的长度
- `shift` 将第一个元素删除并返回删除的元素，空则为`undefined`
- `reverse` 将数组元素倒序
- `sort` 对数据排序
- `splice` 增删、替换数组元素，返回被删除数组元素，无删除则不返回

## 不会修改原始数组的操作方法

- `concat` 连接多个数组，并返回新的数组
- `join` 将数组中所有元素以参数作为分隔符放入一个字符串中
- `slice` 返回选定的元素
- `map` 将数组映射为新的数组
- `filter` 数组过滤，返回所有通过方法判断为true的结果组成的新数组
- `forEach` 数组遍历，没有返回值
- `every` 对数组中的每一项运行给定的函数，如果每一项都返回`true`则返回`true`，否则返回`false`
- `some` 对数组中的每一项运行给定的函数，如果其中一项返回`true`,则返回`true`
- `find` 寻找数组中符合测试方法条件的第一个元素，并返回该元素
- `reduce` 方法接收一个函数作为累加器，数组中的每个值开始缩减，最终计算为一个值
- `indexOf` 该方法返回在数组中可以找到一个给定元素的第一个索引，如果不存在则返回 -1
- `includes` 该方法用来判断一个数组是否包含一个指定的值，如果找到返回`true`,否则返回`false`

## 使用

```javascript
// 连接数组 concat
let arr1 = ['a', 'b', 'c'];
let arr2 = ['d', 'e', 'f'];
arr1.concat(arr2); // ['a', 'b', 'c', 'd', 'e', 'f'];
// 使用展开运算符
[...arr1, ...arr2]

// 循环
const arr = ['a', 'b', 'c'];
arr.forEach((ele, index) => {
	console.log(ele, index);
})

// 循环映射
const numbers = [1, 5, 10, 15];
let doubles = numbers.map(item => item * 2);
// [2, 10, 20, 30]

// includes
const a = [1, 2, 3];
a.includes(2);  // true
a.includes('a');  // false

// find 查找元素
const ret = [12, 5, 8, 130, 44];
ret.find(ele => ele >= 15);
// 130

// filter 过滤数组
const filtered = [12, 5, 8, 130, 44];
filtered.filter(value => vlaue >= 10);
// [12, 130, 44]

// every 循环判断，每个元素都执行回调函数
const passed = [12, 5, 8, 130, 44].every((ele, index, array) => ele >= 10);
// false 不是每个元素都大于等于10

// some 循环判断，遇到有返回true的元素则停止执行
const passed = [12, 5, 8, 130 44].some((ele, index, array) => ele >= 10);
// true

// 数组截取 slice
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];
animals.slice(2);  // ['camel', 'duck', 'elephant']
animals.slice(2, 4);  // ['camel', 'duck']

// 数组增、删 splice
const myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
myFish.splice(2, 0, 'durm'); // ['angel', 'clown', 'drum', 'mandarin', 'sturgeon']
myFish.splice(2, 1);  // ['angel', 'clown', 'mandarin', 'sturgeon']

// lastIndexOf
const arr = [2, 5, 9, 2];
arr.lastIndexOf(2);  // 3
arr.lastIndexOf(8);  // -1

// join
const arr = ['Wind', 'Rain', 'Fire'];
a.join();  // 'Wind,Rain,Fire'
a.join('-');  // 'Wind-Rain-Fire'

// 数组去重
const arr = [1, 1, 1, 2, 3, 4, 4, 5, 3];
const set = new Set(arr);
const newarr = Array.from(set);  // [1, 2, 3, 4, 5]
```

