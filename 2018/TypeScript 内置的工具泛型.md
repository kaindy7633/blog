在 `TypeScript` 中默认内置了很多工具泛型，能够合理灵活的使用这些工具，可以使我们的类型定义更加灵活

这些泛型定义在`node_modules/typescript/lib/lib.es5.d.ts`文件中

## 内置类型定义

### `Record`

`Record` 在 `TS` 中的源码实现：

```typescript
type Record<K extends keyof any, T> = {
    [P in K]: T;
};
```

它用来生成一个属性为 `K`，类型为 `T` 的类型集合。如下所示，我用它生成了一个`Foo`类型，那么就表示所有指定为`Foo`类型的变量都必须包含一个 `key` 为`a`，`value` 为`string`类型的字段。否则，`TS` 类型检查器就会报错。

```typescript
type Foo = Record<'a', string>

const foo: Foo = {a: '1'} // 正确
const foo: Foo = {b: '1'} // 错误，因为 key 不为 a
const foo: Foo = {a: 1} // 错误，因为 value 的值不是 string 类型
```

可以用`Record`来处理另外一种场景。假如我本来已经有了两个类型：

```typescript
interface Foo {
  a: string
}
interface Bar {
  b: string
}
```

我想把`Foo`和`Bar`两个类型的 `key` 合并到一起，并给它们重新指定成 `number` 类型，可以使用`Record`这样实现：

```typescript
type Baz = Record<keyof Foo | keyof Bar, number>
```

此时，`Baz`的类型就相当于下面的类型定义了：

```typescript
interface Baz {
  a: number
  b: number
}
```

### `Partial`

`Partial`在 `TS` 中的源码实现：

```typescript
type Partial<T> = {
  [P in keyof T]?: T[P];
};
```

它用来将 `T` 中的所有的属性都变成可选的。下面的示例中定义了一个类型`IFoo`，它拥有两个必选的属性 `a` 和 `b`。

```typescript
interface IFoo {
  a: number
  b: number
}

const foo: IFoo = { a: 1 } // 错误，因为缺少 b 属性
```

在将变量`foo`指定为`IFoo`类型之后，它就必须同时包含 `a` 和 `b` 两个属性，否则就会报下面的类型检查错误：

```typescript
Property 'b' is missing in type '{ a: number; }' but required in type 'IFoo'.
```

所以，如果我们能把`IFoo`的两个属性都变成可选的不就没问题了：

```typescript
const foo: Partial<IFoo> = { a: 2 } // 正确，因为 IFoo 的属性都已经变成了可选状态
```

### `Required`

`Required`在 `TS` 中的源码实现：

```typescript
type Required<T> = {
  [P in keyof T]-?: T[P];
};
```

它的作用正好和上面的`Partial`相反，是将 `T` 中的所有属性都变成必选的状态。下面示例中定义的类型`IFoo`包含了两个可选的属性 `a` 和 `b`。所以，将变量`foo`指定为`IFoo`类型并且只包含一个 `a` 属性是不会有问题的。

```typescript
interface IFoo {
  a?: number
  b?: number
}

// 正确，因为 IFoo 的两个属性本来就是可选的状态
const foo: IFoo = {
  a: 2
}
```

这时，我们可以用`Required`将`IFoo`的所有属性都变成必选状态，否则，就报类型检查错误：

```typescript
// 错误，因为 IFoo 的属性已经被变成了必选的状态
const foo: Required<IFoo> = {
  a: 2
}
```

```typescript
Property 'b' is missing in type '{ a: number; }' but required in type 'Required<IFoo>'.
```

### `Readonly`

`Readonly`在 `TS` 中的源码实现：

```typescript
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};
```

这个从字面意思就可以理解是将一个类型的所有成员变为只读的状态。看下面的示例，肯定可以随意给`name`赋值成别的字符串值。

```typescript
interface IFoo {
  name: string
  age: number
}

const foo: IFoo = {
  name: 'cxc',
  age: 22,
}

foo.name = 'xiaoming'
```

用`Readonly`转换一下：

```typescript
const foo: Readonly<IFoo> = {
  name: 'cxc',
  age: 22,
}

foo.name = 'xiaoming' // 错误，因为 name 仅是只读的
foo.age = 20 // 错误，因为 age 也仅是只读的
```

```typescript
Cannot assign to 'name' because it is a read-only property.
```

### `Pick`

`Pick`在 `TS` 中的源码实现：

```typescript
type Pick<T, K extends keyof T> = {
  [P in K]: T[P];
};
```

它的作用是从 `T` 中将所有的 `K` 取出来，并生成一个新的类型。下面示例中定义的`IFoo`类型包含了两个必选属性 `a` 和 `b`。所以，将`foo`指定为`IFoo`类型之后，就肯定必须包含这两个属性，否则就会报类型检查错误：

```typescript
interface IFoo {
  a: number
  b: number
}

const foo: IFoo = {
  a: 1,
  b: 2,
}
```

但是，如果我想让`foo`只包含`IFoo`类型的 `a` 属性，就可以用`Pick`这样来实现。它就是告诉 `TS` 仅仅将 `a` 属性从`IFoo`中提取出来即可。

```typescript
// 正确，使用 Pick 生成的新类型确实只包含 a 属性
const foo: Pick<IFoo, 'a'> = {
  a: 2,
}

// 错误，使用 Pick 生成的新类型中并不包含 b 属性
const foo: Pick<IFoo, 'a'> = {
  b: 2,
}
```

注意，它和上面的`Partial`不一样的地方在于，`Partial`是将类型中的所有的属性都变成了可选状态，而不能将某一个属性单独提取出来。

### `Exclude`

`Exclude`在 `TS` 源码中的实现：

```typescript
type Exclude<T, U> = T extends U ? never : T;
```

它的作用是从 `T` 中排除掉所有包含的 `U` 属性。如果不明白这句话，就看下面示例。

代码运行之后，`TFoo`只会包含一个 `2`。这是因为`Exclude`会从第一个类型参数中将其所有包含的第二个类型参数中的值给排除掉。我们可以看到在第一个类型参数中只包含第二个类型参数中的 `1`，因此，它就会被排除掉，只剩下 `2` 了。

```typescript
type TFoo = Exclude<1 | 2, 1 | 3>
```

所以，如果一个变量被指定为了`TFoo`类型，它就只能被赋值为 `2` 了，否则就会报类型检查错误：

```typescript
const foo: TFoo = 2 // 正确
const foo: TFoo = 3 // 错误，因为 TFoo 中不包含 3
```

### `Extract`

`Extract`在 `TS` 中的源码实现：

```typescript
type Extract<T, U> = T extends U ? T : never;
```

它的作用正好和上面的`Exclude`相反。而是从 `T` 中提取出所有包含的 `U` 属性值。还是看下面的示例：

```typescript
type TFoo = Extract<1 | 2, 1 | 3>
```

`TFoo`类型最终只会包含 `1`。这是因为 `T` 包含 `U` 中的属性值 `1`，`Extract`会将它提取出来生成一个类型，也就相当于：

```typescript
type TFoo = 1
```

### `NonNullable`

`NonNullable`在 `TS` 中的源码实现：

```typescript
type NonNullable<T> = T extends null | undefined ? never : T;
```

它的作用是去除 `T` 中包含的`null`或者`undefined`。如下示例所示，变量`foo`的类型为`TFoo`，因此下面的赋值都是没问题的。

```typescript
type TFoo = 1 | null | undefined
let foo: TFoo = 1
foo = null
foo = undefined
```

如果我想把`TFoo`中的`null`和`undefined`去除掉，可以这样处理：

```typescript
let foo: NonNullable<TFoo> = 1 // 正确
foo = null // 错误，因为这个值已经被去除
```

### `Parameters`

`Parameters`的 `TS` 源码实现：

```typescript
type Parameters<T extends (...args: any[]) => any> = T extends (...args: infer P) => any ? P : never;
```

它的作用是用来获取一个函数的参数类型，而且返回的是只能包含一组类型的数组。

```typescript
type Func = (user: string) => void

type Param = Parameters<Func>

let p: Param = ['1'] // 正确
p = ['1', '2'] // 错误，只能包含一个字符串类型值
```

通过上面的示例可以看到通过`Parameters`获取到了`Func`的参数类型，并返回的是数组形式：`[string]`。因此，变量`p`的赋值就只能是包含一个字符串类型值的数组。

### `ConstructorParameters`

`ConstructorParameters`的 `TS` 源码实现：

```typescript
type ConstructorParameters<T extends new (...args: any[]) => any> = T extends new (...args: infer P) => any ? P : never;
```

它的作用是用来获取一个类的构造函数参数类型，并以数组的形式返回。如果不明白这句话的意思，看下面的示例。类`Foo`的构造函数有两个参数，第一个为 `string` 类型，第二个为 `number` 类型。

```typescript
class Foo {
  constructor(x: string, y: number){
    console.log(x, y)
  }
}
```

在使用`ConstructorParameters`处理之后，获取到的是一个类型数组。而且第一个值必须为 `string` 类型，第二个值必须为 `number` 类型。

```typescript
const foo: ConstructorParameters<typeof Foo> = ['1', 2]
```

### `ReturnType`

`ReturnType`的 `TS` 源码实现：

```typescript
type ReturnType<T extends (...args: any[]) => any> = T extends (...args: any[]) => infer R ? R : any;
```

它用来得到一个函数的返回值类型。看下面的示例用`ReturnType`获取到`Func`的返回值类型为`string`，所以，`foo`也就只能被赋值为字符串了。

```typescript
type Func = (value: number) => string

const foo: ReturnType<Func> = '1'
```

### `InstanceType`

`InstanceType`的 `TS` 源码实现：

```typescript
type InstanceType<T extends new (...args: any[]) => any> = T extends new (...args: any[]) => infer R ? R : any;
```

它的作用是获取一个类的实例类型，可以用获取到的实例类型来约束一个变量的赋值必须和类的成员类型完全一样才可以。看下面示例定义的类`Foo`中有一个字符串类型的`x`，一个数字类型的`y`，一个参数为字符串类型的方法`say`

```typescript
class Foo {
  public x = '1'
  public y = 2

  public say = (value: string) => {
    console.log(value)
  }
}
```

我们用`InstanceType`获取类`Foo`的实例类型，用来它约束变量`foo`。那么，接下来给`foo`赋值时就必须完全符合`Foo`的成员类型才可以。

```typescript
const foo: InstanceType<typeof Foo> = {
  x: '1',
  y: 2,
  say: (value: string) => {
    console.log(value)
  }
}
```

假设你将变量`foo`中的`x`值赋值为数字 `1`，就肯定会收到类型检查错误了：

```typescript
Type 'number' is not assignable to type 'string'.
```

### `Omit`

`Omit`用来忽略 `T` 中的 `K` 属性

```typescript
type Omit<T, K> = Pick<T, Exclude<keyof T, K>>
```

## 非内置类型定义

下面这些并非是 `TS` 内置的类型定义

### `DeepReadonly`

`DeepReadonly`用来深度遍历 `T`，并将其所有属性变成只读类型

```typescript
type DeepReadonly<T> = { readonly [P in keyof T]: DeepReadonly<T[P]> }
```

### `ConvertNumberToString`

`ConvertNumberToString`用来将`number`转换为`string`类型

```typescript
type ConvertNumberToString<T> = {
  [K in keyof T]: T[K] extends string ? string : T[K]
}
```

### `ValueOf`

`ValueOf`与`keyof`相对应。取出指定类型的所有 `value`

```typescript
type ValueOf<T> = T[keyof T]
```