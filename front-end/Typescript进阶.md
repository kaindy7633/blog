# Typescript进阶

## 原始类型和对象类型

### 原始类型的注解

首先，我们来看 `JavaScript` 的内置原始类型。除了最常见的 `number` / `string` / `boolean` / `null` / `undefined`， `ECMAScript 2015`（ES6）、2020 (ES11) 又分别引入了 2 个新的原始类型：`symbol` 与 `bigint` 。在 `TypeScript` 中它们都有对应的类型注解：

```ts
const name: string = 'linbudu';
const age: number = 24;
const male: boolean = false;
const undef: undefined = undefined;
const nul: null = null;
const obj: object = { name, age, male };
const bigintVar1: bigint = 9007199254740991n;
const bigintVar2: bigint = BigInt(9007199254740991);
const symbolVar: symbol = Symbol('unique');
```
