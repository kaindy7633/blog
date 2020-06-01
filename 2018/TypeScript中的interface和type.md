`typescript` 总会使用到 `interface` 和 `type`，官方规范稍微说了下两者的区别

> An interface can be named in an extends or implements clause, but a type alias for an object type literal cannot.
An interface can have multiple merged declarations, but a type alias for an object type literal cannot.

## 相同点

### 都可以描述一个对象或者函数

#### interface

```typescript
interface User {
  name: string
  age: number
}

interface SetUser {
  (name: string, age: number): void;
}
```

#### type

```typescript
type User = {
  name: string
  age: number
};

type SetUser = (name: string, age: number)=> void;
```

### 都允许拓展（`extends`）

`interface` 和 `type` 都可以拓展，并且两者并不是相互独立的，也就是说 `interface` 可以 `extends` `type`, `type` 也可以 `extends` `interface` 。 虽然效果差不多，但是两者语法不同。

#### `interface extends interface`

```typescript
interface Name { 
  name: string; 
}
interface User extends Name { 
  age: number; 
}
```

#### `type extends type`

```typescript
type Name = {
  name: string;
}
type User = Name & { age: number  };
```

#### `interface extends type`

```typescript
type Name = { 
  name: string; 
}
interface User extends Name { 
  age: number; 
}
```

#### `type extends interface`

```typescript
interface Name {
  name: string;
}
type User = Name & {
  age: number;
}
```

### 不同点

#### `type` 可以而 `interface` 不行

- `type` 可以声明基本类型别名，联合类型，元组等类型

	```typescript
	// 基本类型别名
	type Name = string

	// 联合类型
	interface Dog {
		wong();
	}
	interface Cat {
		miao();
	}

	type Pet = Dog | Cat

	// 具体定义数组每个位置的类型
	type PetList = [Dog, Pet]
	```

- `type` 语句中还可以使用 `typeof` 获取实例的 类型进行赋值

	```typescript
	// 当你想获取一个变量的类型时，使用 typeof
	let div = document.createElement('div');
	type B = typeof div
```

- 其他骚操作

	```typescript
	type StringOrNumber = string | number;  
	type Text = string | { text: string };  
	type NameLookup = Dictionary<string, Person>;  
	type Callback<T> = (data: T) => void;  
	type Pair<T> = [T, T];  
	type Coordinates = Pair<number>;  
	type Tree<T> = T | { left: Tree<T>, right: Tree<T> };
	复制代码interface 可以而 type 不行
	interface 能够声明合并
	interface User {
	  name: string
	  age: number
	}

	interface User {
	  sex: string
	}

	/*
	User 接口为 {
	  name: string
	  age: number
	  sex: string 
	}
	*/
	```

一般来说，如果不清楚什么时候用 `interface/type`，能用 `interface` 实现，就用 `interface` , 如果不能就用 `type` 。其他更多详情参看 [官方规范文档](https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md "官方规范文档")