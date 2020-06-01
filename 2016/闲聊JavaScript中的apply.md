# 闲聊JavaScript中的apply

`apply` 方法: 它能劫持另外一个对象的方法，继承另外一个对象的属性

`Function.apply(obj,args)` 能接受两个参数：

`obj` : 这个对象将代替 `Function` 类中的` this` 对象

`args`: 这是个数组，它将作为参数传递给 `Function` 类

示例代码：

```javascript
<script>
  /* 定义一个人类 */
  function Person(name, age){
    this.name = name;
    this.age = age;
  }

  /* 定义一个学生类 */
  function Student(name, age, grade){
    Person.apply(this, arguments);
    this.grade = grade;
  }

  /* 创建一个学生对象 */
  var student = new Student('LZ', 40, '一年级');

  //测试
  alert("name:"+student.name+"\n"+"age:"+student.age+"\n"+"grade:"+student.grade);

  //大家可以看到测试结果name:LZ age:40 grade:一年级
  //学生类里面我没有给name和age属性赋值啊,为什么又存在这两个属性的值呢,这个就
  //是apply的神奇之处. 

</script>
```

`Person.apply(this,arguments)`

`this` : 在创建对象时这个代表 `student`

`arguments` : 是一个数组,也就是 `[“LZ”,”40”,”一年级”]`

用 `student` 去执行 `Person` 这个类里面的内容,在 `Person` 这个类里面存在 `this.name` 等之类的语句,这样就将属性创建到了 `student` 对象里面

apply的一些其他巧妙用法:

1. `Math.max` 可以实现得到数组中最大的一项, 因为 `Math.max` 参数里面不支持 `Math.max([param1,param2])` 也就是数组

    但是它支持 `Math.max(param1,param2,param3…)` ,所以可以根据刚才 `apply` 的特点来解决 
    
    `var max=Math.max.apply(null,array)`, 这样轻易的可以得到一个数组中最大的一项

    这块在调用的时候第一个参数给了一个`null`,这个是因为没有对象去调用这个方法,我只需要用这个方法帮我运算,得到返回的结果就行,.所以直接传递了一个`null`过去

2. `Math.min` 可以实现得到数组中最小的一项

    同样和`max`是一个思想 
    
    `var min=Math.min.apply(null,array)`

3. `Array.prototype.push` 可以实现两个数组合并

    同样 `push` 方法没有提供 `push` 一个数组,但是它提供了 
    `push(param1,param,…paramN)` 所以同样也可以通过 `apply` 来装换一下这个数组,即:

    ```javascript
    var arr1 = new Array("1","2","3"); 
    var arr2 = new Array("4","5","6");   

    Array.prototype.push.apply(arr1, arr2);
    ```

    也可以这样理解,arr1调用了`push`方法,参数是通过`apply`将数组装换为参数列表的集合  
