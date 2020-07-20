<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [精读ECMAScript 6.0](#%E7%B2%BE%E8%AF%BBecmascript-60)
  - [简介](#%E7%AE%80%E4%BB%8B)
  - [let和const](#let%E5%92%8Cconst)
    - [let 命令](#let-%E5%91%BD%E4%BB%A4)
    - [块级作用域](#%E5%9D%97%E7%BA%A7%E4%BD%9C%E7%94%A8%E5%9F%9F)
    - [const 命令](#const-%E5%91%BD%E4%BB%A4)
    - [顶层对象的属性](#%E9%A1%B6%E5%B1%82%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%B1%9E%E6%80%A7)
    - [globalThis 对象](#globalthis-%E5%AF%B9%E8%B1%A1)
  - [解构赋值](#%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [数组的解构赋值](#%E6%95%B0%E7%BB%84%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [对象的解构赋值](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [字符串的解构赋值](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [数值和布尔值的解构赋值](#%E6%95%B0%E5%80%BC%E5%92%8C%E5%B8%83%E5%B0%94%E5%80%BC%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [函数参数的解构赋值](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0%E7%9A%84%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC)
    - [用途](#%E7%94%A8%E9%80%94)
  - [字符串的扩展](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%89%A9%E5%B1%95)
    - [Unicode表示法](#unicode%E8%A1%A8%E7%A4%BA%E6%B3%95)
    - [遍历器接口](#%E9%81%8D%E5%8E%86%E5%99%A8%E6%8E%A5%E5%8F%A3)
    - [JSON.stringify() 的改造](#jsonstringify-%E7%9A%84%E6%94%B9%E9%80%A0)
    - [模板字符串](#%E6%A8%A1%E6%9D%BF%E5%AD%97%E7%AC%A6%E4%B8%B2)
  - [字符串新增方法](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%96%B0%E5%A2%9E%E6%96%B9%E6%B3%95)
    - [String.fromCodePoint()](#stringfromcodepoint)
    - [String.raw()](#stringraw)
    - [实例方法：codePointAt()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95codepointat)
    - [实例方法：normalize()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95normalize)
    - [实例方法：includes(), startsWith(), endsWith()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95includes-startswith-endswith)
    - [实例方法：repeat()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95repeat)
    - [实例方法：padStart()，padEnd()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95padstartpadend)
    - [实例方法：trimStart()，trimEnd()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95trimstarttrimend)
    - [实例方法：matchAll()](#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95matchall)
  - [正则的扩展](#%E6%AD%A3%E5%88%99%E7%9A%84%E6%89%A9%E5%B1%95)
    - [RegExp 构造函数](#regexp-%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0)
    - [字符串的正则方法](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%AD%A3%E5%88%99%E6%96%B9%E6%B3%95)
    - [u 修饰符](#u-%E4%BF%AE%E9%A5%B0%E7%AC%A6)
    - [RegExp.prototype.unicode 属性](#regexpprototypeunicode-%E5%B1%9E%E6%80%A7)
    - [y 修饰符](#y-%E4%BF%AE%E9%A5%B0%E7%AC%A6)
    - [RegExp.prototype.sticky 属性](#regexpprototypesticky-%E5%B1%9E%E6%80%A7)
    - [RegExp.prototype.flags 属性](#regexpprototypeflags-%E5%B1%9E%E6%80%A7)
    - [s 修饰符：dotAll 模式](#s-%E4%BF%AE%E9%A5%B0%E7%AC%A6dotall-%E6%A8%A1%E5%BC%8F)
    - [具名组匹配](#%E5%85%B7%E5%90%8D%E7%BB%84%E5%8C%B9%E9%85%8D)
    - [String.prototype.matchAll()](#stringprototypematchall)
  - [数值的扩展](#%E6%95%B0%E5%80%BC%E7%9A%84%E6%89%A9%E5%B1%95)
    - [二进制和八进制表示法](#%E4%BA%8C%E8%BF%9B%E5%88%B6%E5%92%8C%E5%85%AB%E8%BF%9B%E5%88%B6%E8%A1%A8%E7%A4%BA%E6%B3%95)
    - [Number.isFinite(), Number.isNaN()](#numberisfinite-numberisnan)
    - [Number.parseInt(), Number.parseFloat()](#numberparseint-numberparsefloat)
    - [Number.isInteger()](#numberisinteger)
    - [Number.EPSILON](#numberepsilon)
    - [安全整数和 Number.isSafeInteger()](#%E5%AE%89%E5%85%A8%E6%95%B4%E6%95%B0%E5%92%8C-numberissafeinteger)
    - [Math 对象的扩展](#math-%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%89%A9%E5%B1%95)
    - [对数方法](#%E5%AF%B9%E6%95%B0%E6%96%B9%E6%B3%95)
    - [双曲函数方法](#%E5%8F%8C%E6%9B%B2%E5%87%BD%E6%95%B0%E6%96%B9%E6%B3%95)
    - [指数运算符](#%E6%8C%87%E6%95%B0%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [BigInt 数据类型](#bigint-%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B)
    - [BigInt 对象](#bigint-%E5%AF%B9%E8%B1%A1)
    - [BigInt的转换规则](#bigint%E7%9A%84%E8%BD%AC%E6%8D%A2%E8%A7%84%E5%88%99)
    - [数学运算](#%E6%95%B0%E5%AD%A6%E8%BF%90%E7%AE%97)
  - [函数的扩展](#%E5%87%BD%E6%95%B0%E7%9A%84%E6%89%A9%E5%B1%95)
    - [函数参数的默认值](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0%E7%9A%84%E9%BB%98%E8%AE%A4%E5%80%BC)
    - [rest 参数](#rest-%E5%8F%82%E6%95%B0)
    - [严格模式](#%E4%B8%A5%E6%A0%BC%E6%A8%A1%E5%BC%8F)
    - [name 属性](#name-%E5%B1%9E%E6%80%A7)
    - [箭头函数](#%E7%AE%AD%E5%A4%B4%E5%87%BD%E6%95%B0)
    - [尾调用优化](#%E5%B0%BE%E8%B0%83%E7%94%A8%E4%BC%98%E5%8C%96)
    - [函数参数的尾逗号](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0%E7%9A%84%E5%B0%BE%E9%80%97%E5%8F%B7)
    - [Function.prototype.toString()](#functionprototypetostring)
    - [catch 命令的参数省略](#catch-%E5%91%BD%E4%BB%A4%E7%9A%84%E5%8F%82%E6%95%B0%E7%9C%81%E7%95%A5)
  - [数组的扩展](#%E6%95%B0%E7%BB%84%E7%9A%84%E6%89%A9%E5%B1%95)
    - [扩展运算符](#%E6%89%A9%E5%B1%95%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [Array.from()](#arrayfrom)
    - [Array.of()](#arrayof)
    - [数组实例的 copyWithin()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-copywithin)
    - [数组实例的 find() 和 findIndex()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-find-%E5%92%8C-findindex)
    - [数组实例的 fill()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-fill)
    - [数组实例的 entries()，keys() 和 values()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-entrieskeys-%E5%92%8C-values)
    - [数组实例的 includes()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-includes)
    - [数组实例的 flat()，flatMap()](#%E6%95%B0%E7%BB%84%E5%AE%9E%E4%BE%8B%E7%9A%84-flatflatmap)
    - [数组的空位](#%E6%95%B0%E7%BB%84%E7%9A%84%E7%A9%BA%E4%BD%8D)
    - [Array.prototype.sort() 的排序稳定性](#arrayprototypesort-%E7%9A%84%E6%8E%92%E5%BA%8F%E7%A8%B3%E5%AE%9A%E6%80%A7)
  - [对象的扩展](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%89%A9%E5%B1%95)
    - [属性的简洁表示法](#%E5%B1%9E%E6%80%A7%E7%9A%84%E7%AE%80%E6%B4%81%E8%A1%A8%E7%A4%BA%E6%B3%95)
    - [属性名表达式](#%E5%B1%9E%E6%80%A7%E5%90%8D%E8%A1%A8%E8%BE%BE%E5%BC%8F)
    - [方法的 name 属性](#%E6%96%B9%E6%B3%95%E7%9A%84-name-%E5%B1%9E%E6%80%A7)
    - [属性的可枚举性和遍历](#%E5%B1%9E%E6%80%A7%E7%9A%84%E5%8F%AF%E6%9E%9A%E4%B8%BE%E6%80%A7%E5%92%8C%E9%81%8D%E5%8E%86)
    - [super 关键字](#super-%E5%85%B3%E9%94%AE%E5%AD%97)
    - [对象的扩展运算符](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%89%A9%E5%B1%95%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [链判断运算符](#%E9%93%BE%E5%88%A4%E6%96%AD%E8%BF%90%E7%AE%97%E7%AC%A6)
    - [Null 判断运算符](#null-%E5%88%A4%E6%96%AD%E8%BF%90%E7%AE%97%E7%AC%A6)
  - [对象的新增方法](#%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%96%B0%E5%A2%9E%E6%96%B9%E6%B3%95)
    - [Object.is()](#objectis)
    - [Object.assign()](#objectassign)
    - [Object.getOwnPropertyDescriptors()](#objectgetownpropertydescriptors)
    - [__proto__属性，Object.setPrototypeOf()，Object.getPrototypeOf()](#__proto__%E5%B1%9E%E6%80%A7objectsetprototypeofobjectgetprototypeof)
      - [__proto__属性](#__proto__%E5%B1%9E%E6%80%A7)
      - [Object.setPrototypeOf()](#objectsetprototypeof)
      - [Object.getPrototypeOf()](#objectgetprototypeof)
    - [Object.keys()，Object.values()，Object.entries()](#objectkeysobjectvaluesobjectentries)
      - [Object.keys()](#objectkeys)
      - [Object.values()](#objectvalues)
      - [Object.entries()](#objectentries)
    - [Object.fromEntries()](#objectfromentries)
  - [Symbol](#symbol)
    - [Symbol.prototype.description](#symbolprototypedescription)
    - [作为属性名的 Symbol](#%E4%BD%9C%E4%B8%BA%E5%B1%9E%E6%80%A7%E5%90%8D%E7%9A%84-symbol)
    - [消除魔术字符串](#%E6%B6%88%E9%99%A4%E9%AD%94%E6%9C%AF%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [属性名的遍历](#%E5%B1%9E%E6%80%A7%E5%90%8D%E7%9A%84%E9%81%8D%E5%8E%86)
    - [Symbol.for()，Symbol.keyFor()](#symbolforsymbolkeyfor)
    - [模块的 Singleton 模式](#%E6%A8%A1%E5%9D%97%E7%9A%84-singleton-%E6%A8%A1%E5%BC%8F)
    - [内置的 Symbol 值](#%E5%86%85%E7%BD%AE%E7%9A%84-symbol-%E5%80%BC)
      - [Symbol.hasInstance](#symbolhasinstance)
      - [Symbol.isConcatSpreadable](#symbolisconcatspreadable)
      - [Symbol.species](#symbolspecies)
      - [Symbol.match](#symbolmatch)
      - [Symbol.replace](#symbolreplace)
      - [Symbol.search](#symbolsearch)
      - [Symbol.split](#symbolsplit)
      - [Symbol.iterator](#symboliterator)
      - [Symbol.toPrimitive](#symboltoprimitive)
      - [Symbol.toStringTag](#symboltostringtag)
      - [Symbol.unscopables](#symbolunscopables)
  - [Set和Map数据结构](#set%E5%92%8Cmap%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84)
    - [Set](#set)
      - [基本用法](#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
      - [Set 实例的属性和方法](#set-%E5%AE%9E%E4%BE%8B%E7%9A%84%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95)
      - [遍历操作](#%E9%81%8D%E5%8E%86%E6%93%8D%E4%BD%9C)
    - [WeakSet](#weakset)
      - [含义](#%E5%90%AB%E4%B9%89)
      - [语法](#%E8%AF%AD%E6%B3%95)
    - [Map](#map)
      - [含义和基本用法](#%E5%90%AB%E4%B9%89%E5%92%8C%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
      - [实例的属性和操作方法](#%E5%AE%9E%E4%BE%8B%E7%9A%84%E5%B1%9E%E6%80%A7%E5%92%8C%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95)
      - [遍历方法](#%E9%81%8D%E5%8E%86%E6%96%B9%E6%B3%95)
      - [与其他数据结构的互相转换](#%E4%B8%8E%E5%85%B6%E4%BB%96%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E7%9A%84%E4%BA%92%E7%9B%B8%E8%BD%AC%E6%8D%A2)
    - [WeakMap](#weakmap)
      - [含义](#%E5%90%AB%E4%B9%89-1)
      - [WeakMap 的语法](#weakmap-%E7%9A%84%E8%AF%AD%E6%B3%95)
  - [Proxy](#proxy)
    - [概述](#%E6%A6%82%E8%BF%B0)
    - [Proxy 实例的方法](#proxy-%E5%AE%9E%E4%BE%8B%E7%9A%84%E6%96%B9%E6%B3%95)
      - [get()](#get)
      - [set()](#set)
      - [apply()](#apply)
      - [has()](#has)
      - [construct()](#construct)
      - [deleteProperty()](#deleteproperty)
      - [defineProperty()](#defineproperty)
      - [getOwnPropertyDescriptor()](#getownpropertydescriptor)
      - [getPrototypeOf()](#getprototypeof)
      - [isExtensible()](#isextensible)
      - [ownKeys()](#ownkeys)
      - [preventExtensions()](#preventextensions)
      - [setPrototypeOf()](#setprototypeof)
    - [Proxy.revocable()](#proxyrevocable)
  - [Reflect](#reflect)
    - [概述](#%E6%A6%82%E8%BF%B0-1)
    - [静态方法](#%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95)
      - [Reflect.get(target, name, receiver)](#reflectgettarget-name-receiver)
      - [Reflect.set(target, name, value, receiver)](#reflectsettarget-name-value-receiver)
      - [Reflect.has(obj, name)](#reflecthasobj-name)
      - [Reflect.deleteProperty(obj, name)](#reflectdeletepropertyobj-name)
      - [Reflect.construct(target, args)](#reflectconstructtarget-args)
      - [Reflect.getPrototypeOf(obj)](#reflectgetprototypeofobj)
      - [Reflect.setPrototypeOf(obj, newProto)](#reflectsetprototypeofobj-newproto)
      - [Reflect.apply(func, thisArg, args)](#reflectapplyfunc-thisarg-args)
      - [Reflect.defineProperty(target, propertyKey, attributes)](#reflectdefinepropertytarget-propertykey-attributes)
      - [Reflect.getOwnPropertyDescriptor(target, propertyKey)](#reflectgetownpropertydescriptortarget-propertykey)
      - [Reflect.isExtensible (target)](#reflectisextensible-target)
      - [Reflect.preventExtensions(target)](#reflectpreventextensionstarget)
      - [Reflect.ownKeys (target)](#reflectownkeys-target)
    - [实例：使用 Proxy 实现观察者模式](#%E5%AE%9E%E4%BE%8B%E4%BD%BF%E7%94%A8-proxy-%E5%AE%9E%E7%8E%B0%E8%A7%82%E5%AF%9F%E8%80%85%E6%A8%A1%E5%BC%8F)
  - [Promise 对象](#promise-%E5%AF%B9%E8%B1%A1)
    - [Promise 的含义](#promise-%E7%9A%84%E5%90%AB%E4%B9%89)
    - [基本用法](#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95-1)
    - [Promise.prototype.then()](#promiseprototypethen)
    - [Promise.prototype.catch()](#promiseprototypecatch)
    - [Promise.prototype.finally()](#promiseprototypefinally)
    - [Promise.all()](#promiseall)
    - [Promise.race()](#promiserace)
    - [Promise.allSettled()](#promiseallsettled)
    - [Promise.any()](#promiseany)
    - [Promise.resolve()](#promiseresolve)
      - [Promise.reject()](#promisereject)
    - [应用](#%E5%BA%94%E7%94%A8)
      - [加载图片](#%E5%8A%A0%E8%BD%BD%E5%9B%BE%E7%89%87)
      - [Generator 函数与 Promise 的结合](#generator-%E5%87%BD%E6%95%B0%E4%B8%8E-promise-%E7%9A%84%E7%BB%93%E5%90%88)
  - [Iterator 和 for...of 循环](#iterator-%E5%92%8C-forof-%E5%BE%AA%E7%8E%AF)
    - [Iterator（遍历器）的概念](#iterator%E9%81%8D%E5%8E%86%E5%99%A8%E7%9A%84%E6%A6%82%E5%BF%B5)
    - [默认 Iterator 接口](#%E9%BB%98%E8%AE%A4-iterator-%E6%8E%A5%E5%8F%A3)
    - [调用 Iterator 接口的场合](#%E8%B0%83%E7%94%A8-iterator-%E6%8E%A5%E5%8F%A3%E7%9A%84%E5%9C%BA%E5%90%88)
    - [字符串的 Iterator 接口](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84-iterator-%E6%8E%A5%E5%8F%A3)
    - [Iterator 接口与 Generator 函数](#iterator-%E6%8E%A5%E5%8F%A3%E4%B8%8E-generator-%E5%87%BD%E6%95%B0)
    - [遍历器对象的 return()，throw()](#%E9%81%8D%E5%8E%86%E5%99%A8%E5%AF%B9%E8%B1%A1%E7%9A%84-returnthrow)
    - [for...of 循环](#forof-%E5%BE%AA%E7%8E%AF)
      - [数组](#%E6%95%B0%E7%BB%84)
      - [Set 和 Map 结构](#set-%E5%92%8C-map-%E7%BB%93%E6%9E%84)
      - [计算生成的数据结构](#%E8%AE%A1%E7%AE%97%E7%94%9F%E6%88%90%E7%9A%84%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84)
      - [类似数组的对象](#%E7%B1%BB%E4%BC%BC%E6%95%B0%E7%BB%84%E7%9A%84%E5%AF%B9%E8%B1%A1)
      - [对象](#%E5%AF%B9%E8%B1%A1)
  - [Generator 函数的语法](#generator-%E5%87%BD%E6%95%B0%E7%9A%84%E8%AF%AD%E6%B3%95)
    - [简介](#%E7%AE%80%E4%BB%8B-1)
      - [基本概念](#%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5)
      - [yield 表达式](#yield-%E8%A1%A8%E8%BE%BE%E5%BC%8F)
      - [与 Iterator 接口的关系](#%E4%B8%8E-iterator-%E6%8E%A5%E5%8F%A3%E7%9A%84%E5%85%B3%E7%B3%BB)
    - [next 方法的参数](#next-%E6%96%B9%E6%B3%95%E7%9A%84%E5%8F%82%E6%95%B0)
    - [for...of 循环](#forof-%E5%BE%AA%E7%8E%AF-1)
    - [Generator.prototype.throw()](#generatorprototypethrow)
    - [Generator.prototype.return()](#generatorprototypereturn)
    - [next()、throw()、return() 的共同点](#nextthrowreturn-%E7%9A%84%E5%85%B1%E5%90%8C%E7%82%B9)
    - [yield* 表达式](#yield-%E8%A1%A8%E8%BE%BE%E5%BC%8F)
  - [Generator 函数的异步应用](#generator-%E5%87%BD%E6%95%B0%E7%9A%84%E5%BC%82%E6%AD%A5%E5%BA%94%E7%94%A8)
    - [传统方法](#%E4%BC%A0%E7%BB%9F%E6%96%B9%E6%B3%95)
    - [基本概念](#%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5-1)
      - [异步](#%E5%BC%82%E6%AD%A5)
      - [回调函数](#%E5%9B%9E%E8%B0%83%E5%87%BD%E6%95%B0)
      - [Promise](#promise)
    - [Generator 函数](#generator-%E5%87%BD%E6%95%B0)
      - [协程](#%E5%8D%8F%E7%A8%8B)
      - [协程的 Generator 函数实现](#%E5%8D%8F%E7%A8%8B%E7%9A%84-generator-%E5%87%BD%E6%95%B0%E5%AE%9E%E7%8E%B0)
      - [Generator 函数的数据交换和错误处理](#generator-%E5%87%BD%E6%95%B0%E7%9A%84%E6%95%B0%E6%8D%AE%E4%BA%A4%E6%8D%A2%E5%92%8C%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86)
      - [异步任务的封装](#%E5%BC%82%E6%AD%A5%E4%BB%BB%E5%8A%A1%E7%9A%84%E5%B0%81%E8%A3%85)
    - [Thunk 函数](#thunk-%E5%87%BD%E6%95%B0)
      - [参数的求值策略](#%E5%8F%82%E6%95%B0%E7%9A%84%E6%B1%82%E5%80%BC%E7%AD%96%E7%95%A5)
      - [Thunk 函数的含义](#thunk-%E5%87%BD%E6%95%B0%E7%9A%84%E5%90%AB%E4%B9%89)
      - [JavaScript 语言的 Thunk 函数](#javascript-%E8%AF%AD%E8%A8%80%E7%9A%84-thunk-%E5%87%BD%E6%95%B0)
      - [Generator 函数的流程管理](#generator-%E5%87%BD%E6%95%B0%E7%9A%84%E6%B5%81%E7%A8%8B%E7%AE%A1%E7%90%86)
      - [Thunk 函数的自动流程管理](#thunk-%E5%87%BD%E6%95%B0%E7%9A%84%E8%87%AA%E5%8A%A8%E6%B5%81%E7%A8%8B%E7%AE%A1%E7%90%86)
    - [co 模块](#co-%E6%A8%A1%E5%9D%97)
      - [基本用法](#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95-2)
  - [async 函数](#async-%E5%87%BD%E6%95%B0)
    - [含义](#%E5%90%AB%E4%B9%89-2)
    - [基本用法](#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95-3)
    - [语法](#%E8%AF%AD%E6%B3%95-1)
      - [返回 Promise 对象](#%E8%BF%94%E5%9B%9E-promise-%E5%AF%B9%E8%B1%A1)
      - [Promise 对象的状态变化](#promise-%E5%AF%B9%E8%B1%A1%E7%9A%84%E7%8A%B6%E6%80%81%E5%8F%98%E5%8C%96)
      - [await 命令](#await-%E5%91%BD%E4%BB%A4)
      - [错误处理](#%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86)
  - [Class 的基本语法](#class-%E7%9A%84%E5%9F%BA%E6%9C%AC%E8%AF%AD%E6%B3%95)
    - [简介](#%E7%AE%80%E4%BB%8B-2)
      - [类的由来](#%E7%B1%BB%E7%9A%84%E7%94%B1%E6%9D%A5)
      - [constructor 方法](#constructor-%E6%96%B9%E6%B3%95)
      - [类的实例](#%E7%B1%BB%E7%9A%84%E5%AE%9E%E4%BE%8B)
      - [取值函数（getter）和存值函数（setter）](#%E5%8F%96%E5%80%BC%E5%87%BD%E6%95%B0getter%E5%92%8C%E5%AD%98%E5%80%BC%E5%87%BD%E6%95%B0setter)
      - [属性表达式](#%E5%B1%9E%E6%80%A7%E8%A1%A8%E8%BE%BE%E5%BC%8F)
      - [Class 表达式](#class-%E8%A1%A8%E8%BE%BE%E5%BC%8F)
      - [注意点](#%E6%B3%A8%E6%84%8F%E7%82%B9)
    - [静态方法](#%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95-1)
    - [实例属性的新写法](#%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7%E7%9A%84%E6%96%B0%E5%86%99%E6%B3%95)
    - [静态属性](#%E9%9D%99%E6%80%81%E5%B1%9E%E6%80%A7)
    - [私有方法和私有属性](#%E7%A7%81%E6%9C%89%E6%96%B9%E6%B3%95%E5%92%8C%E7%A7%81%E6%9C%89%E5%B1%9E%E6%80%A7)
      - [现有的解决方案](#%E7%8E%B0%E6%9C%89%E7%9A%84%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88)
      - [私有属性的提案](#%E7%A7%81%E6%9C%89%E5%B1%9E%E6%80%A7%E7%9A%84%E6%8F%90%E6%A1%88)
      - [new.target 属性](#newtarget-%E5%B1%9E%E6%80%A7)
  - [Class 的继承](#class-%E7%9A%84%E7%BB%A7%E6%89%BF)
    - [简介](#%E7%AE%80%E4%BB%8B-3)
    - [Object.getPrototypeOf()](#objectgetprototypeof-1)
    - [super 关键字](#super-%E5%85%B3%E9%94%AE%E5%AD%97-1)
    - [类的 prototype 属性和__proto__属性](#%E7%B1%BB%E7%9A%84-prototype-%E5%B1%9E%E6%80%A7%E5%92%8C__proto__%E5%B1%9E%E6%80%A7)
    - [原生构造函数的继承](#%E5%8E%9F%E7%94%9F%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E7%9A%84%E7%BB%A7%E6%89%BF)
    - [Mixin 模式的实现](#mixin-%E6%A8%A1%E5%BC%8F%E7%9A%84%E5%AE%9E%E7%8E%B0)
  - [Module 的语法](#module-%E7%9A%84%E8%AF%AD%E6%B3%95)
    - [概述](#%E6%A6%82%E8%BF%B0-2)
    - [严格模式](#%E4%B8%A5%E6%A0%BC%E6%A8%A1%E5%BC%8F-1)
    - [export 命令](#export-%E5%91%BD%E4%BB%A4)
    - [import 命令](#import-%E5%91%BD%E4%BB%A4)
    - [模块的整体加载](#%E6%A8%A1%E5%9D%97%E7%9A%84%E6%95%B4%E4%BD%93%E5%8A%A0%E8%BD%BD)
    - [export default 命令](#export-default-%E5%91%BD%E4%BB%A4)
    - [import()](#import)
  - [编程风格](#%E7%BC%96%E7%A8%8B%E9%A3%8E%E6%A0%BC)
    - [块级作用域](#%E5%9D%97%E7%BA%A7%E4%BD%9C%E7%94%A8%E5%9F%9F-1)
      - [let 取代 var](#let-%E5%8F%96%E4%BB%A3-var)
      - [全局常量和线程安全](#%E5%85%A8%E5%B1%80%E5%B8%B8%E9%87%8F%E5%92%8C%E7%BA%BF%E7%A8%8B%E5%AE%89%E5%85%A8)
    - [字符串](#%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [解构赋值](#%E8%A7%A3%E6%9E%84%E8%B5%8B%E5%80%BC-1)
    - [对象](#%E5%AF%B9%E8%B1%A1-1)
    - [数组](#%E6%95%B0%E7%BB%84-1)
    - [函数](#%E5%87%BD%E6%95%B0)
    - [Map 结构](#map-%E7%BB%93%E6%9E%84)
    - [Class](#class)
    - [模块](#%E6%A8%A1%E5%9D%97)
  - [异步遍历器](#%E5%BC%82%E6%AD%A5%E9%81%8D%E5%8E%86%E5%99%A8)
    - [同步遍历器的问题](#%E5%90%8C%E6%AD%A5%E9%81%8D%E5%8E%86%E5%99%A8%E7%9A%84%E9%97%AE%E9%A2%98)
    - [异步遍历的接口](#%E5%BC%82%E6%AD%A5%E9%81%8D%E5%8E%86%E7%9A%84%E6%8E%A5%E5%8F%A3)
    - [for await...of](#for-awaitof)
    - [异步 Generator 函数](#%E5%BC%82%E6%AD%A5-generator-%E5%87%BD%E6%95%B0)
    - [yield* 语句](#yield-%E8%AF%AD%E5%8F%A5)
  - [ArrayBuffer](#arraybuffer)
    - [ArrayBuffer 对象](#arraybuffer-%E5%AF%B9%E8%B1%A1)
      - [概述](#%E6%A6%82%E8%BF%B0-3)
      - [ArrayBuffer.prototype.byteLength](#arraybufferprototypebytelength)
      - [ArrayBuffer.prototype.slice()](#arraybufferprototypeslice)
      - [ArrayBuffer.isView()](#arraybufferisview)
    - [TypedArray 视图](#typedarray-%E8%A7%86%E5%9B%BE)
      - [概述](#%E6%A6%82%E8%BF%B0-4)
      - [构造函数](#%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0)
      - [数组方法](#%E6%95%B0%E7%BB%84%E6%96%B9%E6%B3%95)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 精读ECMAScript 6.0

## 简介

ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准，在2015年6月正式发布。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现

## let和const

### let 命令

ES6 新增了 `let` 命令，用来声明变量，用法类似于 `var`

不存在变量提升:  `var` 命令会发生“变量提升”现象，即变量可以在声明之前使用，值为 `undefined`,  `let`命令改变了语法行为，它所声明的变量一定要在声明后使用，否则报错。


暂时性死区：只要块级作用域内存在` let` 命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响。

在代码块内，使用 `let` 命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）。

ES6 规定暂时性死区和 `let` 、`const` 语句不出现变量提升，主要是为了减少运行时错误，防止在变量声明前就使用这个变量，从而导致意料之外的行为

`let` 不允许在相同作用域内，重复声明同一个变量

### 块级作用域

`ES5` 只有全局作用域和函数作用域，没有块级作用域，这带来很多不合理的场景

- 内层变量可能会覆盖外层变量
- 用来计数的循环变量泄露为全局变量

`let`实际上为 `JavaScript` 新增了块级作用域。

`ES5` 规定，函数只能在顶层作用域和函数作用域之中声明，不能在块级作用域声明，`ES6` 引入了块级作用域，明确允许在块级作用域之中声明函数

### const 命令

`const`声明一个只读的常量。一旦声明，常量的值就不能改变.

`const`的作用域与`let`命令相同：只在声明所在的块级作用域内有效。`const`命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。

`const`实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，`const`只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了

`ES5` 只有两种声明变量的方法：`var`命令和`function`命令。ES6 除了添加`let`和`const`命令，后面还会提到，另外两种声明变量的方法：`import`命令和`class`命令。所以，ES6 一共有 6 种声明变量的方法。

### 顶层对象的属性

顶层对象，在浏览器环境指的是`window`对象，在`Node` 指的是`global`对象

`ES6` 为了保持兼容性，`var`命令和`function`命令声明的全局变量，依旧是顶层对象的属性；另一方面规定，`let`命令、`const`命令、`class`命令声明的全局变量，不属于顶层对象的属性

### globalThis 对象

`JavaScript` 语言存在一个顶层对象，它提供全局环境（即全局作用域）,但这个顶层对象在各种实现里面是不统一的

- 浏览器里面，顶层对象是`window`，但 `Node` 和 `Web Worker` 没有`window`。
- 浏览器和 `Web Worker` 里面，`self`也指向顶层对象，但是 `Node` 没有`self`。
- `Node` 里面，顶层对象是`global`，但其他环境都不支持。

`ES2020` 在语言标准的层面，引入`globalThis`作为顶层对象。也就是说，任何环境下，`globalThis`都是存在的，都可以从它拿到顶层对象，指向全局环境下的`this`

## 解构赋值

### 数组的解构赋值

`ES6` 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）

```javascript
let [a, b, c] = [1, 2, 3];
```

如果解构不成功，变量的值就等于`undefined`

对于 `Set` 结构，也可以使用数组的解构赋值。

```javascript
let [x, y, z] = new Set(['a', 'b', 'c']);
x // "a"
```

事实上，只要某种数据结构具有 `Iterator` 接口，都可以采用数组形式的解构赋值

```javascript
function* fibs() {
  let a = 0;
  let b = 1;
  while (true) {
    yield a;
    [a, b] = [b, a + b];
  }
}

let [first, second, third, fourth, fifth, sixth] = fibs();
sixth // 5
```

解构赋值允许指定默认值

```javascript
let [foo = true] = [];
foo // true

let [x, y = 'b'] = ['a']; // x='a', y='b'
let [x, y = 'b'] = ['a', undefined]; // x='a', y='b'
```

### 对象的解构赋值

解构不仅可以用于数组，还可以用于对象

```javascript
let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
foo // "aaa"
bar // "bbb"
```

对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值

```javascript
let { bar, foo } = { foo: 'aaa', bar: 'bbb' };
foo // "aaa"
bar // "bbb"

let { baz } = { foo: 'aaa', bar: 'bbb' };
baz // undefined
```

对象的解构赋值，可以很方便地将现有对象的方法，赋值到某个变量

```javascript
// 例一
let { log, sin, cos } = Math;

// 例二
const { log } = console;
log('hello') // hello
```

对象的解构也可以指定默认值。

```javascript
var {x = 3} = {};
x // 3

var {x, y = 5} = {x: 1};
x // 1
y // 5

var {x: y = 3} = {};
y // 3

var {x: y = 3} = {x: 5};
y // 5

var { message: msg = 'Something went wrong' } = {};
msg // "Something went wrong"
```

### 字符串的解构赋值

字符串也可以解构赋值。这是因为此时，字符串被转换成了一个类似数组的对象

```javascript
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"
```

### 数值和布尔值的解构赋值

解构赋值时，如果等号右边是数值和布尔值，则会先转为对象

```javascript
let {toString: s} = 123;
s === Number.prototype.toString // true

let {toString: s} = true;
s === Boolean.prototype.toString // true
```

### 函数参数的解构赋值

函数的参数也可以使用解构赋值

```javascript
function add([x, y]){
  return x + y;
}

add([1, 2]); // 3
```

### 用途

- 交换变量的值

  ```javascript
  let x = 1;
  let y = 2;

  [x, y] = [y, x];
  ```

- 从函数返回多个值

  ```javascript
  // 返回一个数组

  function example() {
    return [1, 2, 3];
  }
  let [a, b, c] = example();

  // 返回一个对象

  function example() {
    return {
      foo: 1,
      bar: 2
    };
  }
  let { foo, bar } = example();
  ```

- 函数参数的定义

  ```javascript
  // 参数是一组有次序的值
  function f([x, y, z]) { ... }
  f([1, 2, 3]);

  // 参数是一组无次序的值
  function f({x, y, z}) { ... }
  f({z: 3, y: 2, x: 1});
  ```

- 提取 `JSON` 数据

  ```javascript
  let jsonData = {
    id: 42,
    status: "OK",
    data: [867, 5309]
  };

  let { id, status, data: number } = jsonData;

  console.log(id, status, number);
  // 42, "OK", [867, 5309]
  ```

- 函数参数的默认值

  ```javascript
  jQuery.ajax = function (url, {
    async = true,
    beforeSend = function () {},
    cache = true,
    complete = function () {},
    crossDomain = false,
    global = true,
    // ... more config
  } = {}) {
    // ... do stuff
  };
  ```

- 遍历 `Map` 结构

  任何部署了 Iterator 接口的对象，都可以用for...of循环遍历。Map 结构原生支持 Iterator 接口，配合变量的解构赋值，获取键名和键值就非常方便

  ```javascript
  const map = new Map();
  map.set('first', 'hello');
  map.set('second', 'world');

  for (let [key, value] of map) {
    console.log(key + " is " + value);
  }
  // first is hello
  // second is world
  ```

- 输入模块的指定方法

  ```javascript
  const { SourceMapConsumer, SourceNode } = require("source-map");
  ```

## 字符串的扩展

### Unicode表示法

`ES6` 加强了对 `Unicode` 的支持，允许采用`\uxxxx`形式表示一个字符，其中`xxxx`表示字符的 `Unicode` 码点

```javascript
"\u0061"
// "a"
```

但是，这种表示法只限于码点在`\u0000~\uFFFF`之间的字符,`ES6` 对这一点做出了改进，只要将码点放入大括号，就能正确解读该字符

```javascript
"\u{20BB7}"
// "𠮷"

"\u{41}\u{42}\u{43}"
// "ABC"

let hello = 123;
hell\u{6F} // 123

'\u{1F680}' === '\uD83D\uDE80'
// true
```

### 遍历器接口

`ES6` 为字符串添加了遍历器接口，使得字符串可以被`for...of`循环遍历。

```javascript
for (let codePoint of 'foo') {
  console.log(codePoint)
}
// "f"
// "o"
// "o"
```

### JSON.stringify() 的改造

根据标准，`JSON` 数据必须是 `UTF-8` 编码。但是，现在的`JSON.stringify()`方法有可能返回不符合 `UTF-8` 标准的字符串

为了确保返回的是合法的 `UTF-8` 字符，`ES2019` 改变了`JSON.stringify()`的行为。如果遇到`0xD800`到`0xDFFF`之间的单个码点，或者不存在的配对形式，它会返回转义字符串，留给应用自己决定下一步的处理

### 模板字符串

`ES6` 引入了模板字符

```javascript
$('#result').append(`
  There are <b>${basket.count}</b> items
   in your basket, <em>${basket.onSale}</em>
  are on sale!
`);
```

模板字符串（template string）是增强版的字符串，用反引号（`）标识。它可以当作普通字符串使用，也可以用来定义多行字符串，或者在字符串中嵌入变量

```javascript
// 普通字符串
`In JavaScript '\n' is a line-feed.`

// 多行字符串
`In JavaScript this is
 not legal.`

console.log(`string text line 1
string text line 2`);

// 字符串中嵌入变量
let name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`
```

模板字符串中嵌入变量，需要将变量名写在`${}`之中,大括号内部可以放入任意的 `JavaScript` 表达式，可以进行运算，以及引用对象属性

```javascript
let x = 1;
let y = 2;

`${x} + ${y} = ${x + y}`
// "1 + 2 = 3"

`${x} + ${y * 2} = ${x + y * 2}`
// "1 + 4 = 5"

let obj = {x: 1, y: 2};
`${obj.x + obj.y}`
// "3"
```

## 字符串新增方法

### String.fromCodePoint()

`ES5` 提供 `String.fromCharCode()` 方法，用于从 `Unicode` 码点返回对应字符，但是这个方法不能识别码点大于 `0xFFFF` 的字符

`ES6` 提供了`String.fromCodePoint()`方法，可以识别大于`0xFFFF`的字符，弥补了`String.fromCharCode()`方法的不足

```javascript
String.fromCodePoint(0x20BB7)
// "𠮷"
String.fromCodePoint(0x78, 0x1f680, 0x79) === 'x\uD83D\uDE80y'
// true
```

### String.raw()

`ES6` 还为原生的 `String` 对象，提供了一个`raw()`方法。该方法返回一个斜杠都被转义（即斜杠前面再加一个斜杠）的字符串，往往用于模板字符串的处理方法

```javascript
String.raw`Hi\n${2+3}!`
// 实际返回 "Hi\\n5!"，显示的是转义后的结果 "Hi\n5!"

String.raw`Hi\u000A!`;
// 实际返回 "Hi\\u000A!"，显示的是转义后的结果 "Hi\u000A!"
```

### 实例方法：codePointAt()

`JavaScript` 内部，字符以 `UTF-16` 的格式储存，每个字符固定为2个字节。对于那些需要4个字节储存的字符（`Unicode` 码点大于`0xFFFF`的字符），`JavaScript` 会认为它们是两个字符

`ES6` 提供了`codePointAt()`方法，能够正确处理 4 个字节储存的字符，返回一个字符的码点

```javascript
let s = '𠮷a';

s.codePointAt(0) // 134071
s.codePointAt(1) // 57271

s.codePointAt(2) // 97
```

`codePointAt()`方法可以用来测试一个字符由两个字节还是由四个字节组成的

```javascript
function is32Bit(c) {
  return c.codePointAt(0) > 0xFFFF;
}

is32Bit("𠮷") // true
is32Bit("a") // false
```

### 实例方法：normalize()

`ES6` 提供字符串实例的`normalize()`方法，用来将字符的不同表示方法统一为同样的形式，这称为 `Unicode` 正规化

```javascript
'\u01D1'.normalize() === '\u004F\u030C'.normalize()
// true
```

### 实例方法：includes(), startsWith(), endsWith()

传统上，`JavaScript` 只有`indexOf`方法，可以用来确定一个字符串是否包含在另一个字符串中。`ES6` 又提供了三种新方法:

- `includes()`：返回布尔值，表示是否找到了参数字符串。
- `startsWith()`：返回布尔值，表示参数字符串是否在原字符串的头部。
- `endsWith()`：返回布尔值，表示参数字符串是否在原字符串的尾部。

```javascript
let s = 'Hello world!';

s.startsWith('Hello') // true
s.endsWith('!') // true
s.includes('o') // true
```

这三个方法都支持第二个参数，表示开始搜索的位置

```javascript
let s = 'Hello world!';

s.startsWith('world', 6) // true
s.endsWith('Hello', 5) // true
s.includes('Hello', 6) // false
```

### 实例方法：repeat()

`repeat`方法返回一个新字符串，表示将原字符串重复n次

```javascript
'x'.repeat(3) // "xxx"
'hello'.repeat(2) // "hellohello"
'na'.repeat(0) // ""
```

### 实例方法：padStart()，padEnd()

`ES2017` 引入了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。`padStart()`用于头部补全，`padEnd()`用于尾部补全

```javascript
'x'.padStart(5, 'ab') // 'ababx'
'x'.padStart(4, 'ab') // 'abax'

'x'.padEnd(5, 'ab') // 'xabab'
'x'.padEnd(4, 'ab') // 'xaba'
```

`padStart()`和`padEnd()`一共接受两个参数，第一个参数是字符串补全生效的最大长度，第二个参数是用来补全的字符串

### 实例方法：trimStart()，trimEnd()

`ES2019` 对字符串实例新增了`trimStart()`和`trimEnd()`这两个方法。它们的行为与`trim()`一致，`trimStart()`消除字符串头部的空格，`trimEnd()`消除尾部的空格。它们返回的都是新字符串，不会修改原始字符串

```javascript
const s = '  abc  ';

s.trim() // "abc"
s.trimStart() // "abc  "
s.trimEnd() // "  abc"
```

### 实例方法：matchAll()

`matchAll()`方法返回一个正则表达式在当前字符串的所有匹配

## 正则的扩展

### RegExp 构造函数

在 `ES` 中的 `RegExp` 构造函数的参数有两种情况:

- 参数是字符串，这时第二个参数表示正则表达式的修饰符（`flag`）

  ```javascript
  var regex = new RegExp('xyz', 'i');
  // 等价于
  var regex = /xyz/i;
  ```

- 参数是一个正则表示式，这时会返回一个原有正则表达式的拷贝

  ```javascript
  var regex = new RegExp(/xyz/i);
  // 等价于
  var regex = /xyz/i;
  ```

在 `ES6` 中，如果`RegExp`构造函数第一个参数是一个正则对象，那么可以使用第二个参数指定修饰符。而且，返回的正则表达式会忽略原有的正则表达式的修饰符，只使用新指定的修饰符

```javascript
new RegExp(/abc/ig, 'i').flags
// "i"
```

### 字符串的正则方法

字符串对象共有 4 个方法，可以使用正则表达式：

- `match()` `String.prototype.match` 调用 `RegExp.prototype[Symbol.match]`
- `replace()` `String.prototype.replace` 调用 `RegExp.prototype[Symbol.replace]`
- `search()` `String.prototype.search` 调用 `RegExp.prototype[Symbol.search]`
- `split()` `String.prototype.split` 调用 `RegExp.prototype[Symbol.split]`

### u 修饰符

`ES6` 对正则表达式添加了`u`修饰符，含义为“Unicode 模式”，用来正确处理大于`\uFFFF`的 `Unicode` 字符

```javascript
/^\uD83D/u.test('\uD83D\uDC2A') // false
/^\uD83D/.test('\uD83D\uDC2A') // true
```

### RegExp.prototype.unicode 属性

正则实例对象新增`unicode`属性，表示是否设置了`u`修饰符

```javascript
const r1 = /hello/;
const r2 = /hello/u;

r1.unicode // false
r2.unicode // true
```

### y 修饰符

`ES6` 为正则表达式添加了`y`修饰符，叫做“粘连”（sticky）修饰符

`y`修饰符的作用与`g`修饰符类似，也是全局匹配，后一次匹配都从上一次匹配成功的下一个位置开始。不同之处在于，`g`修饰符只要剩余位置中存在匹配即可，而`y`修饰符确保匹配必须从剩余的第一个位置开始，这也就是“粘连”的涵义

```javascript
var s = 'aaa_aa_a';
var r1 = /a+/g;
var r2 = /a+/y;

r1.exec(s) // ["aaa"]
r2.exec(s) // ["aaa"]

r1.exec(s) // ["aa"]
r2.exec(s) // null
```

### RegExp.prototype.sticky 属性

与`y`修饰符相匹配，`ES6` 的正则实例对象多了`sticky`属性，表示是否设置了`y`修饰符。

```javascript
var r = /hello\d/y;
r.sticky // true
```

### RegExp.prototype.flags 属性

`ES6` 为正则表达式新增了`flags`属性，会返回正则表达式的修饰符

```javascript
// ES5 的 source 属性
// 返回正则表达式的正文
/abc/ig.source
// "abc"

// ES6 的 flags 属性
// 返回正则表达式的修饰符
/abc/ig.flags
// 'gi'
```

### s 修饰符：dotAll 模式

正则表达式中，点（.）是一个特殊字符，代表任意的单个字符，但是有两个例外。一个是四个字节的 `UTF-16` 字符，这个可以用`u`修饰符解决；另一个是行终止符（line terminator character）

`ES2018` 引入`s`修饰符，使得`.`可以匹配任意单个字符。

这被称为`dotAll`模式，即点（`dot`）代表一切字符。所以，正则表达式还引入了一个`dotAll`属性，返回一个布尔值，表示该正则表达式是否处在`dotAll`模式

```javascript
const re = /foo.bar/s;
// 另一种写法
// const re = new RegExp('foo.bar', 's');

re.test('foo\nbar') // true
re.dotAll // true
re.flags // 's'
```

### 具名组匹配

`ES2018` 引入了具名组匹配（Named Capture Groups），允许为每一个组匹配指定一个名字，既便于阅读代码，又便于引用

```javascript
const RE_DATE = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;

const matchObj = RE_DATE.exec('1999-12-31');
const year = matchObj.groups.year; // 1999
const month = matchObj.groups.month; // 12
const day = matchObj.groups.day; // 31
```

如果具名组没有匹配，那么对应的`groups`对象属性会是`undefined`

有了具名组匹配以后，可以使用解构赋值直接从匹配结果上为变量赋值

```javascript
let {groups: {one, two}} = /^(?<one>.*):(?<two>.*)$/u.exec('foo:bar');
one  // foo
two  // bar
```

### String.prototype.matchAll()

`ES2020` 增加了`String.prototype.matchAll()`方法，可以一次性取出所有匹配。不过，它返回的是一个遍历器（Iterator），而不是数组

```javascript
const string = 'test1test2test3';

// g 修饰符加不加都可以
const regex = /t(e)(st(\d?))/g;

for (const match of string.matchAll(regex)) {
  console.log(match);
}
// ["test1", "e", "st1", "1", index: 0, input: "test1test2test3"]
// ["test2", "e", "st2", "2", index: 5, input: "test1test2test3"]
// ["test3", "e", "st3", "3", index: 10, input: "test1test2test3"]
```

遍历器转为数组是非常简单的，使用`...`运算符和`Array.from()`方法就可以了

```javascript
// 转为数组方法一
[...string.matchAll(regex)]

// 转为数组方法二
Array.from(string.matchAll(regex))
```

## 数值的扩展

### 二进制和八进制表示法

`ES6` 提供了二进制和八进制数值的新的写法，分别用前缀`0b`（或`0B`）和`0o`（或`0O`）表示

```javascript
0b111110111 === 503 // true
0o767 === 503 // true
```

从 `ES5` 开始，在严格模式之中，八进制就不再允许使用前缀`0`表示，`ES6` 进一步明确，要使用前缀`0o`表示

```javascript
// 非严格模式
(function(){
  console.log(0o11 === 011);
})() // true

// 严格模式
(function(){
  'use strict';
  console.log(0o11 === 011);
})() // Uncaught SyntaxError: Octal literals are not allowed in strict mode
```

### Number.isFinite(), Number.isNaN()

`ES6` 在`Number`对象上，新提供了`Number.isFinite()`和`Number.isNaN()`两个方法

`Number.isFinite()`用来检查一个数值是否为有限的（`finite`），即不是`Infinity`

```javascript
Number.isFinite(15); // true
Number.isFinite(0.8); // true
Number.isFinite(NaN); // false
Number.isFinite(Infinity); // false
Number.isFinite(-Infinity); // false
Number.isFinite('foo'); // false
Number.isFinite('15'); // false
Number.isFinite(true); // false
```

如果参数类型不是数值，`Number.isFinite`一律返回`false`

`Number.isNaN()`用来检查一个值是否为`NaN`

```javascript
Number.isNaN(NaN) // true
Number.isNaN(15) // false
Number.isNaN('15') // false
Number.isNaN(true) // false
Number.isNaN(9/NaN) // true
Number.isNaN('true' / 0) // true
Number.isNaN('true' / 'true') // true
```

### Number.parseInt(), Number.parseFloat()

`ES6` 将全局方法`parseInt()`和`parseFloat()`，移植到`Number`对象上面，行为完全保持不变。

```javascript
// ES5的写法
parseInt('12.34') // 12
parseFloat('123.45#') // 123.45

// ES6的写法
Number.parseInt('12.34') // 12
Number.parseFloat('123.45#') // 123.45
```

### Number.isInteger()

`Number.isInteger()`用来判断一个数值是否为整数

```javascript
Number.isInteger(25) // true
Number.isInteger(25.1) // false
```

`JavaScript` 内部，整数和浮点数采用的是同样的储存方法，所以 `25` 和 `25.0` 被视为同一个值。

```javascript
Number.isInteger(25) // true
Number.isInteger(25.0) // true
```

如果参数不是数值，`Number.isInteger`返回`false`

如果对数据精度的要求较高，不建议使用`Number.isInteger()`判断一个数值是否为整数

### Number.EPSILON

`ES6` 在`Number`对象上面，新增一个极小的常量`Number.EPSILON`。根据规格，它表示 1 与大于 1 的最小浮点数之间的差

```javascript
Number.EPSILON === Math.pow(2, -52)
// true
Number.EPSILON
// 2.220446049250313e-16
Number.EPSILON.toFixed(20)
// "0.00000000000000022204"
```

·Number.EPSILON`可以用来设置“能够接受的误差范围”。比如，误差范围设为 2 的-50 次方（即Number.EPSILON * Math.pow(2, 2)），即如果两个浮点数的差小于这个值，我们就认为这两个浮点数相等。因此，`Number.EPSILON`的实质是一个可以接受的最小误差范围

```javascript
function withinErrorMargin (left, right) {
  return Math.abs(left - right) < Number.EPSILON * Math.pow(2, 2);
}

0.1 + 0.2 === 0.3 // false
withinErrorMargin(0.1 + 0.2, 0.3) // true

1.1 + 1.3 === 2.4 // false
withinErrorMargin(1.1 + 1.3, 2.4) // true
```

### 安全整数和 Number.isSafeInteger()

`JavaScript` 能够准确表示的整数范围在`-2^53`到`2^53`之间（不含两个端点），超过这个范围，无法精确表示这个值

```javascript
Math.pow(2, 53) // 9007199254740992

9007199254740992  // 9007199254740992
9007199254740993  // 9007199254740992

Math.pow(2, 53) === Math.pow(2, 53) + 1
// true
```

`ES6` 引入了`Number.MAX_SAFE_INTEGER`和`Number.MIN_SAFE_INTEGER`这两个常量，用来表示这个范围的上下限

```javascript
Number.MAX_SAFE_INTEGER === Math.pow(2, 53) - 1
// true
Number.MAX_SAFE_INTEGER === 9007199254740991
// true

Number.MIN_SAFE_INTEGER === -Number.MAX_SAFE_INTEGER
// true
Number.MIN_SAFE_INTEGER === -9007199254740991
// true
```

`Number.isSafeInteger()`则是用来判断一个整数是否落在这个范围之内

```javascript
Number.isSafeInteger('a') // false
Number.isSafeInteger(null) // false
Number.isSafeInteger(NaN) // false
Number.isSafeInteger(Infinity) // false
Number.isSafeInteger(-Infinity) // false

Number.isSafeInteger(3) // true
Number.isSafeInteger(1.2) // false
Number.isSafeInteger(9007199254740990) // true
Number.isSafeInteger(9007199254740992) // false

Number.isSafeInteger(Number.MIN_SAFE_INTEGER - 1) // false
Number.isSafeInteger(Number.MIN_SAFE_INTEGER) // true
Number.isSafeInteger(Number.MAX_SAFE_INTEGER) // true
Number.isSafeInteger(Number.MAX_SAFE_INTEGER + 1) // false
```

### Math 对象的扩展

`ES6` 在 `Math` 对象上新增了 17 个与数学相关的方法。所有这些方法都是静态方法，只能在 `Math` 对象上调用

- `Math.trunc()`方法用于去除一个数的小数部分，返回整数部分

  ```javascript
  Math.trunc(4.1) // 4
  Math.trunc(4.9) // 4
  Math.trunc(-4.1) // -4
  Math.trunc(-4.9) // -4
  Math.trunc(-0.1234) // -0
  ```

- Math.sign()方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值

  它会返回五种值:

  - 参数为正数，返回+1；
  - 参数为负数，返回-1；
  - 参数为 0，返回0；
  - 参数为-0，返回-0;
  - 其他值，返回NaN

  ```javascript
  Math.sign(-5) // -1
  Math.sign(5) // +1
  Math.sign(0) // +0
  Math.sign(-0) // -0
  Math.sign(NaN) // NaN
  ```

- Math.cbrt()方法用于计算一个数的立方根

  ```javascript
  Math.cbrt(-1) // -1
  Math.cbrt(0)  // 0
  Math.cbrt(1)  // 1
  Math.cbrt(2)  // 1.2599210498948732
  ```

- Math.clz32()方法将参数转为 32 位无符号整数的形式，然后返回这个 32 位值里面有多少个前导 0

  ```javascript
  Math.clz32(0) // 32
  Math.clz32(1) // 31
  Math.clz32(1000) // 22
  Math.clz32(0b01000000000000000000000000000000) // 1
  Math.clz32(0b00100000000000000000000000000000) // 2
  ```

- Math.imul()方法返回两个数以 32 位带符号整数形式相乘的结果，返回的也是一个 32 位的带符号整数

  ```javascript
  Math.imul(2, 4)   // 8
  Math.imul(-1, 8)  // -8
  Math.imul(-2, -2) // 4
  ```

- Math.fround()方法返回一个数的32位单精度浮点数形式

  ```javascript
  Math.fround(0)   // 0
  Math.fround(1)   // 1
  Math.fround(2 ** 24 - 1)   // 16777215
  ```

- Math.hypot()方法返回所有参数的平方和的平方根

  ```javascript
  Math.hypot(3, 4);        // 5
  Math.hypot(3, 4, 5);     // 7.0710678118654755
  Math.hypot();            // 0
  Math.hypot(NaN);         // NaN
  Math.hypot(3, 4, 'foo'); // NaN
  Math.hypot(3, 4, '5');   // 7.0710678118654755
  Math.hypot(-3);          // 3
  ```

### 对数方法

`ES6` 新增了 4 个对数相关方法

- `Math.expm1(x)`返回 `ex - 1`，即`Math.exp(x) - 1`

  ```javascript
  Math.expm1(-1) // -0.6321205588285577
  Math.expm1(0)  // 0
  Math.expm1(1)  // 1.718281828459045
  ```

- `Math.log1p(x)`方法返回`1 + x`的自然对数，即`Math.log(1 + x)`。如果`x`小于`-1`，返回`NaN`

  ```javascript
  Math.log1p(1)  // 0.6931471805599453
  Math.log1p(0)  // 0
  Math.log1p(-1) // -Infinity
  Math.log1p(-2) // NaN
  ```

- Math.log10()返回以 10 为底的`x`的对数。如果`x`小于 0，则返回 `NaN`

  ```javascript
  Math.log10(2)      // 0.3010299956639812
  Math.log10(1)      // 0
  Math.log10(0)      // -Infinity
  Math.log10(-2)     // NaN
  Math.log10(100000) // 5
  ```

- Math.log2()返回以 2 为底的`x`的对数。如果`x`小于 0，则返回 `NaN`

  ```javascript
  Math.log2(3)       // 1.584962500721156
  Math.log2(2)       // 1
  Math.log2(1)       // 0
  Math.log2(0)       // -Infinity
  Math.log2(-2)      // NaN
  Math.log2(1024)    // 10
  Math.log2(1 << 29) // 29
  ```

### 双曲函数方法

`ES6` 新增了 6 个双曲函数方法。

- `Math.sinh(x)` 返回x的双曲正弦（hyperbolic sine）
- `Math.cosh(x)` 返回x的双曲余弦（hyperbolic cosine）
- `Math.tanh(x)` 返回x的双曲正切（hyperbolic tangent）
- `Math.asinh(x)` 返回x的反双曲正弦（inverse hyperbolic sine）
- `Math.acosh(x)` 返回x的反双曲余弦（inverse hyperbolic cosine）
- `Math.atanh(x)` 返回x的反双曲正切（inverse hyperbolic tangent）

### 指数运算符

`ES2016` 新增了一个指数运算符（`**`）

```javascript
2 ** 2 // 4
2 ** 3 // 8
```

### BigInt 数据类型

`JavaScript` 所有数字都保存成 `64` 位浮点数，这给数值的表示带来了两大限制。

一是数值的精度只能到 `53` 个二进制位（相当于 `16` 个十进制位），大于这个范围的整数，`JavaScript` 是无法精确表示的，这使得 `JavaScript` 不适合进行科学和金融方面的精确计算。二是大于或等于2的1024次方的数值，`JavaScript` 无法表示，会返回`Infinity`。

`ES2020` 引入了一种新的数据类型 `BigInt`（大整数），来解决这个问题。`BigInt` 只用来表示整数，没有位数的限制，任何位数的整数都可以精确表示。

```javascript
const a = 2172141653n;
const b = 15346349309n;

// BigInt 可以保持精度
a * b // 33334444555566667777n

// 普通整数无法保持精度
Number(a) * Number(b) // 33334444555566670000
```

为了与 `Number` 类型区别，`BigInt` 类型的数据必须添加后缀`n`

`BigInt` 与普通整数是两种值，它们之间并不相等。

```javascript
42n === 42 // false
```

`typeof`运算符对于 `BigInt` 类型的数据返回`bigint`。

```javascript
typeof 123n // 'bigint'
```

`BigInt` 可以使用负号（-），但是不能使用正号（+），因为会与 `asm.js` 冲突。

```javascript
-42n // 正确
+42n // 报错
```

### BigInt 对象

`JavaScript` 原生提供`BigInt`对象，可以用作构造函数生成 `BigInt` 类型的数值

```javascript
BigInt(123) // 123n
BigInt('123') // 123n
BigInt(false) // 0n
BigInt(true) // 1n
```

`BigInt` 对象继承了 `Object` 对象的两个实例方法:

- `BigInt.prototype.toString()`
- `BigInt.prototype.valueOf()`

继承了 `Number` 对象的一个实例方法:

- `BigInt.prototype.toLocaleString()`

此外，还提供了三个静态方法。

- `BigInt.asUintN(width, BigInt)`： 给定的 BigInt 转为 0 到 2width - 1 之间对应的值。
- `BigInt.asIntN(width, BigInt)`：给定的 BigInt 转为 -2width - 1 到 2width - 1 - 1 之间对应的值。
- `BigInt.parseInt(string[, radix])`：近似于Number.parseInt()，将一个字符串转换成指定进制的 BigInt。

```javascript
const max = 2n ** (64n - 1n) - 1n;

BigInt.asIntN(64, max)
// 9223372036854775807n
BigInt.asIntN(64, max + 1n)
// -9223372036854775808n
BigInt.asUintN(64, max + 1n)
// 9223372036854775808n
```

### BigInt的转换规则

可以使用`Boolean()`、`Number()`和`String()`这三个方法，将 `BigInt` 可以转为布尔值、数值和字符串类型

```javascript
Boolean(0n) // false
Boolean(1n) // true
Number(1n)  // 1
String(1n)  // "1"
```

### 数学运算

`BigInt` 类型的`+`、`-`、`*`和`**`这四个二元运算符，与 `Number` 类型的行为一致。除法运算`/`会舍去小数部分，返回一个整数

```javascript
9n / 5n
// 1n
```

## 函数的扩展

### 函数参数的默认值

`ES6` 允许为函数的参数设置默认值，即直接写在参数定义的后面

```javascript
function log(x, y = 'World') {
  console.log(x, y);
}

log('Hello') // Hello World
log('Hello', 'China') // Hello China
log('Hello', '') // Hello
```

参数变量是默认声明的，所以不能用`let`或`const`再次声明

```javascript
function foo(x = 5) {
  let x = 1; // error
  const x = 2; // error
}
```

使用参数默认值时，函数不能有同名参数

参数默认值可以与解构赋值的默认值，结合起来使用

```javascript
function foo({x, y = 5}) {
  console.log(x, y);
}

foo({}) // undefined 5
foo({x: 1}) // 1 5
foo({x: 1, y: 2}) // 1 2
foo() // TypeError: Cannot read property 'x' of undefined
```

通常情况下，定义了默认值的参数，应该是函数的尾参数

```javascript
// 例一
function f(x = 1, y) {
  return [x, y];
}

f() // [1, undefined]
f(2) // [2, undefined]
f(, 1) // 报错
f(undefined, 1) // [1, 1]

// 例二
function f(x, y = 5, z) {
  return [x, y, z];
}

f() // [undefined, 5, undefined]
f(1) // [1, 5, undefined]
f(1, ,2) // 报错
f(1, undefined, 2) // [1, 5, 2]
```

指定了默认值以后，函数的`length`属性，将返回没有指定默认值的参数个数。也就是说，指定了默认值后，`length`属性将失真

```javascript
(function (a) {}).length // 1
(function (a = 5) {}).length // 0
(function (a, b, c = 5) {}).length // 2
```

### rest 参数

`ES6` 引入 `rest` 参数（形式为`...变量名`），用于获取函数的多余参数，这样就不需要使用`arguments`对象了。`rest` 参数搭配的变量是一个数组，该变量将多余的参数放入数组中

```javascript
function add(...values) {
  let sum = 0;

  for (var val of values) {
    sum += val;
  }

  return sum;
}

add(2, 5, 3) // 10
```

注意，`rest` 参数之后不能再有其他参数（即只能是最后一个参数），否则会报错

```javascript
// 报错
function f(a, ...b, c) {
  // ...
}
```

### 严格模式

从 `ES5` 开始，函数内部可以设定为严格模式, `ES2016` 做了一点修改，规定只要函数参数使用了默认值、解构赋值、或者扩展运算符，那么函数内部就不能显式设定为严格模式，否则会报错

```javascript
// 报错
function doSomething(a, b = a) {
  'use strict';
  // code
}

// 报错
const doSomething = function ({a, b}) {
  'use strict';
  // code
};

// 报错
const doSomething = (...a) => {
  'use strict';
  // code
};

const obj = {
  // 报错
  doSomething({a, b}) {
    'use strict';
    // code
  }
};
```

### name 属性

`ES6` 对函数的 `name` 的行为做出了一些修改。如果将一个匿名函数赋值给一个变量，`ES5` 的`name`属性，会返回空字符串，而 `ES6` 的`name`属性会返回实际的函数名

```javascript
var f = function () {};

// ES5
f.name // ""

// ES6
f.name // "f"
```

### 箭头函数

`ES6` 允许使用“箭头”（`=>`）定义函数

```javascript
var f = v => v;

// 等同于
var f = function (v) {
  return v;
};
```

如果箭头函数不需要参数或需要多个参数，就使用一个圆括号代表参数部分

```javascript
var f = () => 5;
// 等同于
var f = function () { return 5 };

var sum = (num1, num2) => num1 + num2;
// 等同于
var sum = function(num1, num2) {
  return num1 + num2;
};
```

箭头函数可以与变量解构结合使用

```javascript
const full = ({ first, last }) => first + ' ' + last;

// 等同于
function full(person) {
  return person.first + ' ' + person.last;
}
```

箭头函数的一个用处是简化回调函数

```javascript
// 正常函数写法
[1,2,3].map(function (x) {
  return x * x;
});

// 箭头函数写法
[1,2,3].map(x => x * x);
```

```javascript
// 正常函数写法
var result = values.sort(function (a, b) {
  return a - b;
});

// 箭头函数写法
var result = values.sort((a, b) => a - b);
```

箭头函数有几个使用注意点。

- 函数体内的`this`对象，就是定义时所在的对象，而不是使用时所在的对象。

- 不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误。

- 不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 `rest` 参数代替。

- 不可以使用`yield`命令，因此箭头函数不能用作 `Generator` 函数

### 尾调用优化

尾调用（Tail Call）是函数式编程的一个重要概念，就是指某个函数的最后一步是调用另一个函数

```javascript
function f(x){
  return g(x);
}
```

尾调用之所以与其他调用不同，就在于它的特殊的调用位置。

我们知道，函数调用会在内存形成一个“调用记录”，又称“调用帧”（call frame），保存调用位置和内部变量等信息。如果在函数`A`的内部调用函数`B`，那么在`A`的调用帧上方，还会形成一个`B`的调用帧。等到`B`运行结束，将结果返回到`A`，`B`的调用帧才会消失。如果函数`B`内部还调用函数`C`，那就还有一个`C`的调用帧，以此类推。所有的调用帧，就形成一个“调用栈”（call stack）

尾调用由于是函数的最后一步操作，所以不需要保留外层函数的调用帧，因为调用位置、内部变量等信息都不会再用到了，只要直接用内层函数的调用帧，取代外层函数的调用帧就可以了

```javascript
function f() {
  let m = 1;
  let n = 2;
  return g(m + n);
}
f();

// 等同于
function f() {
  return g(3);
}
f();

// 等同于
g(3);
```

这就叫做“尾调用优化”（Tail call optimization），即只保留内层函数的调用帧。如果所有函数都是尾调用，那么完全可以做到每次执行时，调用帧只有一项，这将大大节省内存。这就是“尾调用优化”的意义

函数调用自身，称为递归。如果尾调用自身，就称为尾递归

```javascript
function factorial(n) {
  if (n === 1) return 1;
  return n * factorial(n - 1);
}

factorial(5) // 120
```

我们将上面的阶乘函数优化成尾递归

```javascript
function factorial(n, total) {
  if (n === 1) return total;
  return factorial(n - 1, n * total);
}

factorial(5, 1) // 120
```

来看看斐波拉契数列的例子：

```javascript
function Fibonacci (n) {
  if ( n <= 1 ) {return 1};

  return Fibonacci(n - 1) + Fibonacci(n - 2);
}

Fibonacci(10) // 89
Fibonacci(100) // 超时
Fibonacci(500) // 超时
```

尾递归优化过的 `Fibonacci` 数列实现如下

```javascript
function Fibonacci2 (n , ac1 = 1 , ac2 = 1) {
  if( n <= 1 ) {return ac2};

  return Fibonacci2 (n - 1, ac2, ac1 + ac2);
}

Fibonacci2(100) // 573147844013817200000
Fibonacci2(1000) // 7.0330367711422765e+208
Fibonacci2(10000) // Infinity
```

`ES6` 明确规定，所有 `ECMAScript` 的实现，都必须部署“尾调用优化”。这就是说，`ES6` 中只要使用尾递归，就不会发生栈溢出

尾递归的实现，往往需要改写递归函数，确保最后一步只调用自身, 这很不直观，解决这个问题有两个方法：

- 在尾递归函数之外，再提供一个正常形式的函数

  ```javascript
  function tailFactorial(n, total) {
    if (n === 1) return total;
    return tailFactorial(n - 1, n * total);
  }

  function factorial(n) {
    return tailFactorial(n, 1);
  }

  factorial(5) // 120
  ```

  或者通过柯里化的方式，柯里化（currying），是将多参数的函数转换成单参数的形式

  ```javascript
  function currying(fn, n) {
    return function (m) {
      return fn.call(this, m, n);
    };
  }

  function tailFactorial(n, total) {
    if (n === 1) return total;
    return tailFactorial(n - 1, n * total);
  }

  const factorial = currying(tailFactorial, 1);

  factorial(5) // 120
  ```

- 采用 `ES6` 的函数默认值

  ```javascript
  function factorial(n, total = 1) {
    if (n === 1) return total;
    return factorial(n - 1, n * total);
  }

  factorial(5) // 120
  ```

`ES6` 的尾调用优化只在严格模式下开启，正常模式是无效的

尾递归优化只在严格模式下生效，那么正常模式下,就自己实现尾递归优化。它的原理非常简单，尾递归之所以需要优化，原因是调用栈太多，造成溢出，那么只要减少调用栈，就不会溢出。怎么做可以减少调用栈呢？就是采用“循环”换掉“递归”。

```javascript
// 递归函数
function sum(x, y) {
  if (y > 0) {
    return sum(x + 1, y - 1);
  } else {
    return x;
  }
}

sum(1, 100000)
// Uncaught RangeError: Maximum call stack size exceeded(…)

// 使用蹦床函数（trampoline）可以将递归执行转为循环执行
function trampoline(f) {
  while (f && f instanceof Function) {
    f = f();
  }
  return f;
}

// 改写上面的 sum 递归
function sum(x, y) {
  if (y > 0) {
    return sum.bind(null, x + 1, y - 1);
  } else {
    return x;
  }
}

// 现在使用蹦床函数执行
trampoline(sum(1, 100000))
// 100001
```

然后，蹦床函数并不是真正的尾递归优化，下面的代码实现才是

```javascript
function tco(f) {
  var value;
  var active = false;
  var accumulated = [];

  return function accumulator() {
    accumulated.push(arguments);
    if (!active) {
      active = true;
      while (accumulated.length) {
        value = f.apply(this, accumulated.shift());
      }
      active = false;
      return value;
    }
  };
}

var sum = tco(function(x, y) {
  if (y > 0) {
    return sum(x + 1, y - 1)
  }
  else {
    return x
  }
});

sum(1, 100000)
// 100001
```

### 函数参数的尾逗号

`ES2017` 允许函数的最后一个参数有尾逗号（trailing comma）

```javascript
function clownsEverywhere(
  param1,
  param2,
) { /* ... */ }

clownsEverywhere(
  'foo',
  'bar',
);
```

### Function.prototype.toString()

`ES2019` 对函数实例的`toString()`方法做出了修改。`toString()`方法返回函数代码本身，以前会省略注释和空格, 修改后的`toString()`方法，明确要求返回一模一样的原始代码

```javascript
function /* foo comment */ foo () {}

foo.toString()
// "function /* foo comment */ foo () {}"
```

### catch 命令的参数省略

`JavaScript` 语言的`try...catch`结构，以前明确要求`catch`命令后面必须跟参数，接受`try`代码块抛出的错误对象, `ES2019` 做出了改变，允许`catch`语句省略参数

```javascript
try {
  // ...
} catch {
  // ...
}
```

## 数组的扩展

### 扩展运算符

扩展运算符（spread）是三个点（`...`）。它好比 `rest` 参数的逆运算，将一个数组转为用逗号分隔的参数序列

```javascript
console.log(...[1, 2, 3])
// 1 2 3

console.log(1, ...[2, 3, 4], 5)
// 1 2 3 4 5

[...document.querySelectorAll('div')]
// [<div>, <div>, <div>]
```

该运算符主要用于函数调用

```javascript
function push(array, ...items) {
  array.push(...items);
}

function add(x, y) {
  return x + y;
}

const numbers = [4, 38];
add(...numbers) // 42
```

扩展运算符后面还可以放置表达式

```javascript
const arr = [
  ...(x > 0 ? ['a'] : []),
  'b',
];
```

由于扩展运算符可以展开数组，所以不再需要`apply`方法，将数组转为函数的参数了。

```javascript
// ES5 的写法
function f(x, y, z) {
  // ...
}
var args = [0, 1, 2];
f.apply(null, args);

// ES6的写法
function f(x, y, z) {
  // ...
}
let args = [0, 1, 2];
f(...args);
```

求数组中的最大值

```javascript
Math.max(...[14, 3, 77])
```

通过`push`函数，将一个数组添加到另一个数组的尾部

```javascript
let arr1 = [0, 1, 2];
let arr2 = [3, 4, 5];
arr1.push(...arr2);
```

扩展运算符有以下应用：

- 复制数组，用扩展运算符复制数组，得到的是副本，而非地址值的拷贝

  ```javascript
  const a1 = [1, 2];
  // 写法一
  const a2 = [...a1];
  // 写法二
  const [...a2] = a1;
  ```

- 合并数组

  ```javascript
  [...arr1, ...arr2, ...arr3]
  ```

- 与解构赋值结合, 扩展运算符可以与解构赋值结合起来，用于生成数组

  ```javascript
  // ES5
  a = list[0], rest = list.slice(1)
  // ES6
  [a, ...rest] = list
  ```

  ```javascript
  const [first, ...rest] = [1, 2, 3, 4, 5];
  first // 1
  rest  // [2, 3, 4, 5]

  const [first, ...rest] = [];
  first // undefined
  rest  // []

  const [first, ...rest] = ["foo"];
  first  // "foo"
  rest   // []
  ```

- 扩展运算符还可以将字符串转为真正的数组

  ```javascript
  [...'hello']
  // [ "h", "e", "l", "l", "o" ]
  ```

- 实现了 `Iterator` 接口的对象

  任何定义了遍历器（`Iterator`）接口的对象，都可以用扩展运算符转为真正的数组

  ```javascript
  let nodeList = document.querySelectorAll('div');
  let array = [...nodeList];
  ```

- `Map` 和 `Set` 结构，`Generator` 函数

  ```javascript
  let map = new Map([
    [1, 'one'],
    [2, 'two'],
    [3, 'three'],
  ]);

  let arr = [...map.keys()]; // [1, 2, 3]
  ```

  `Generator` 函数运行后，返回一个遍历器对象，因此也可以使用扩展运算符

  ```javascript
  const go = function*(){
    yield 1;
    yield 2;
    yield 3;
  };

  [...go()] // [1, 2, 3]
  ```

### Array.from()

`Array.from`方法用于将两类对象转为真正的数组：类似数组的对象（`array-like object`）和可遍历（`iterable`）的对象（包括 `ES6` 新增的数据结构 `Set` 和 `Map`）

```javascript
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
};

// ES5的写法
var arr1 = [].slice.call(arrayLike); // ['a', 'b', 'c']

// ES6的写法
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```

实际应用中，常见的类似数组的对象是 `DOM` 操作返回的 `NodeList` 集合，以及函数内部的`arguments`对象。`Array.from`都可以将它们转为真正的数组

```javascript
// NodeList对象
let ps = document.querySelectorAll('p');
Array.from(ps).filter(p => {
  return p.textContent.length > 100;
});

// arguments对象
function foo() {
  var args = Array.from(arguments);
  // ...
}
```

`Array.from`还可以接受第二个参数，作用类似于数组的`map`方法，用来对每个元素进行处理，将处理后的值放入返回的数组

```javascript
Array.from(arrayLike, x => x * x);
// 等同于
Array.from(arrayLike).map(x => x * x);

Array.from([1, 2, 3], (x) => x * x)
// [1, 4, 9]
```

### Array.of()

`Array.of`方法用于将一组值，转换为数组

```javascript
Array.of(3, 11, 8) // [3,11,8]
Array.of(3) // [3]
Array.of(3).length // 1
```

`Array.of`基本上可以用来替代`Array()`或`new Array()`，并且不存在由于参数不同而导致的重载。它的行为非常统一

`Array.of`总是返回参数值组成的数组。如果没有参数，就返回一个空数组

### 数组实例的 copyWithin()

数组实例的`copyWithin()`方法，在当前数组内部，将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组

```javascript
Array.prototype.copyWithin(target, start = 0, end = this.length)
```

它接受三个参数:

- `target`（必需）：从该位置开始替换数据。如果为负值，表示倒数。
- `start`（可选）：从该位置开始读取数据，默认为 0。如果为负值，表示从末尾开始计算。
- `end`（可选）：到该位置前停止读取数据，默认等于数组长度。如果为负值，表示从末尾开始计算。

这三个参数都应该是数值，如果不是，会自动转为数值, 下面是一些例子：

```javascript
// 将3号位复制到0号位
[1, 2, 3, 4, 5].copyWithin(0, 3, 4)
// [4, 2, 3, 4, 5]

// -2相当于3号位，-1相当于4号位
[1, 2, 3, 4, 5].copyWithin(0, -2, -1)
// [4, 2, 3, 4, 5]

// 将3号位复制到0号位
[].copyWithin.call({length: 5, 3: 1}, 0, 3)
// {0: 1, 3: 1, length: 5}

// 将2号位到数组结束，复制到0号位
let i32a = new Int32Array([1, 2, 3, 4, 5]);
i32a.copyWithin(0, 2);
// Int32Array [3, 4, 5, 4, 5]

// 对于没有部署 TypedArray 的 copyWithin 方法的平台
// 需要采用下面的写法
[].copyWithin.call(new Int32Array([1, 2, 3, 4, 5]), 0, 3, 4);
// Int32Array [4, 2, 3, 4, 5]
```

### 数组实例的 find() 和 findIndex()

数组实例的`find`方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为`true`的成员，然后返回该成员。如果没有符合条件的成员，则返回`undefined`

```javascript
[1, 4, -5, 10].find((n) => n < 0)
// -5
```

`find`方法的回调函数可以接受三个参数，依次为当前的值、当前的位置和原数组

```javascript
[1, 5, 10, 15].find(function(value, index, arr) {
  return value > 9;
}) // 10
```

数组实例的`findIndex`方法的用法与`find`方法非常类似，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回`-1`

```javascript
[1, 5, 10, 15].findIndex(function(value, index, arr) {
  return value > 9;
}) // 2
```

这两个方法都可以接受第二个参数，用来绑定回调函数的`this`对象

```javascript
function f(v){
  return v > this.age;
}
let person = {name: 'John', age: 20};
[10, 12, 26, 15].find(f, person);    // 26
```

### 数组实例的 fill()

`fill`方法使用给定值，填充一个数组

```javascript
['a', 'b', 'c'].fill(7)
// [7, 7, 7]

new Array(3).fill(7)
// [7, 7, 7]
```

`fill`方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置

```javascript
['a', 'b', 'c'].fill(7, 1, 2)
// ['a', 7, 'c']
```

### 数组实例的 entries()，keys() 和 values()

`ES6` 提供三个新的方法——`entries()`，`keys()`和`values()`——用于遍历数组。它们都返回一个遍历器对象，可以用`for...of`循环进行遍历，唯一的区别是`keys()`是对键名的遍历、`values()`是对键值的遍历，`entries()`是对键值对的遍历

```javascript
for (let index of ['a', 'b'].keys()) {
  console.log(index);
}
// 0
// 1

for (let elem of ['a', 'b'].values()) {
  console.log(elem);
}
// 'a'
// 'b'

for (let [index, elem] of ['a', 'b'].entries()) {
  console.log(index, elem);
}
// 0 "a"
// 1 "b"
```

也可以手动调用遍历器对象的next方法，进行遍历

```javascript
let letter = ['a', 'b', 'c'];
let entries = letter.entries();
console.log(entries.next().value); // [0, 'a']
console.log(entries.next().value); // [1, 'b']
console.log(entries.next().value); // [2, 'c']
```

### 数组实例的 includes()

`Array.prototype.includes`方法返回一个布尔值，表示某个数组是否包含给定的值，与字符串的`includes`方法类似。`ES2016` 引入了该方法

```javascript
[1, 2, 3].includes(2)     // true
[1, 2, 3].includes(4)     // false
[1, 2, NaN].includes(NaN) // true
```

该方法的第二个参数表示搜索的起始位置，默认为`0`。如果第二个参数为负数，则表示倒数的位置，如果这时它大于数组长度（比如第二个参数为-4，但数组长度为3），则会重置为从`0`开始

### 数组实例的 flat()，flatMap()

数组的成员有时还是数组，`Array.prototype.flat()`用于将嵌套的数组“拉平”，变成一维的数组。该方法返回一个新数组，对原数据没有影响。

```javascript
[1, 2, [3, 4]].flat()
// [1, 2, 3, 4]
```

`flat()`默认只会“拉平”一层，如果想要“拉平”多层的嵌套数组，可以将`flat()`方法的参数写成一个整数，表示想要拉平的层数，默认为1

```javascript
[1, 2, [3, [4, 5]]].flat()
// [1, 2, 3, [4, 5]]

[1, 2, [3, [4, 5]]].flat(2)
// [1, 2, 3, 4, 5]
```

### 数组的空位

数组的空位指，数组的某一个位置没有任何值。比如，`Array`构造函数返回的数组都是空位。

```javascript
Array(3) // [, , ,]
```

### Array.prototype.sort() 的排序稳定性

排序稳定性（stable sorting）是排序算法的重要属性，指的是排序关键字相同的项目，排序前后的顺序不变

```javascript
const arr = [
  'peach',
  'straw',
  'apple',
  'spork'
];

const stableSorting = (s1, s2) => {
  if (s1[0] < s2[0]) return -1;
  return 1;
};

arr.sort(stableSorting)
// ["apple", "peach", "straw", "spork"]
```

常见的排序算法之中，插入排序、合并排序、冒泡排序等都是稳定的，堆排序、快速排序等是不稳定的。不稳定排序的主要缺点是，多重排序时可能会产生问题, `ES2019` 明确规定，`Array.prototype.sort()`的默认排序算法必须稳定

## 对象的扩展

### 属性的简洁表示法

`ES6` 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法

```javascript
const foo = 'bar';
const baz = {foo};
baz // {foo: "bar"}

// 等同于
const baz = {foo: foo};
```

除了属性简写，方法也可以简写

```javascript
const o = {
  method() {
    return "Hello!";
  }
};

// 等同于

const o = {
  method: function() {
    return "Hello!";
  }
};
```

### 属性名表达式

`JavaScript` 定义对象的属性，有两种方法

```javascript
// 方法一
obj.foo = true;

// 方法二
obj['a' + 'bc'] = 123;
```

`ES6` 允许字面量定义对象时，用方法二（表达式）作为对象的属性名，即把表达式放在方括号内。

```javascript
let propKey = 'foo';

let obj = {
  [propKey]: true,
  ['a' + 'bc']: 123
};
```

### 方法的 name 属性

函数的`name`属性，返回函数名。对象方法也是函数，因此也有`name`属性

```javascript
const person = {
  sayName() {
    console.log('hello!');
  },
};

person.sayName.name   // "sayName"
```

### 属性的可枚举性和遍历

对象的每个属性都有一个描述对象（`Descriptor`），用来控制该属性的行为。`Object.getOwnPropertyDescriptor`方法可以获取该属性的描述对象

```javascript
let obj = { foo: 123 };
Object.getOwnPropertyDescriptor(obj, 'foo')
//  {
//    value: 123,
//    writable: true,
//    enumerable: true,
//    configurable: true
//  }
```

描述对象的`enumerable`属性，称为“可枚举性”，如果该属性为`false`，就表示某些操作会忽略当前属性。

目前，有四个操作会忽略`enumerable`为`false`的属性。

- `for...in`循环：只遍历对象自身的和继承的可枚举的属性。
- `Object.keys()`：返回对象自身的所有可枚举的属性的键名。
- `JSON.stringify()`：只串行化对象自身的可枚举的属性。
- `Object.assign()`： 忽略`enumerable`为`false`的属性，只拷贝对象自身的可枚举的属性。

总的来说，操作中引入继承的属性会让问题复杂化，大多数时候，我们只关心对象自身的属性。所以，尽量不要用`for...in`循环，而用`Object.keys()`代替

`ES6` 一共有 5 种方法可以遍历对象的属性:

- `for...in`循环遍历对象自身的和继承的可枚举属性（不含 `Symbol` 属性）
- `Object.keys`返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 `Symbol` 属性）的键名。
- `Object.getOwnPropertyNames`返回一个数组，包含对象自身的所有属性（不含 `Symbol` 属性，但是包括不可枚举属性）的键名
- `Object.getOwnPropertySymbols`返回一个数组，包含对象自身的所有 `Symbol` 属性的键名。
- `Reflect.ownKeys`返回一个数组，包含对象自身的（不含继承的）所有键名，不管键名是 `Symbol` 或字符串，也不管是否可枚举

### super 关键字

`ES6` 新增了关键字`super`，它指向当前对象的原型对象

```javascript
const proto = {
  foo: 'hello'
};

const obj = {
  foo: 'world',
  find() {
    return super.foo;
  }
};

Object.setPrototypeOf(obj, proto);
obj.find() // "hello"
```

### 对象的扩展运算符

`ES2018` 将这个扩展运算符引入了对象

对象的解构赋值用于从一个对象取值，相当于将目标对象自身的所有可遍历的（`enumerable`）、但尚未被读取的属性，分配到指定的对象上面。所有的键和它们的值，都会拷贝到新对象上面

```javascript
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
x // 1
y // 2
z // { a: 3, b: 4 }
```

**注意: 解构赋值的拷贝是浅拷贝，即如果一个键的值是复合类型的值（数组、对象、函数）、那么解构赋值拷贝的是这个值的引用，而��是这个值的副本**

对象的扩展运算符（`...`）用于取出参数对象的所有可遍历属性，拷贝到当前对象之中。

```javascript
let z = { a: 3, b: 4 };
let n = { ...z };
n // { a: 3, b: 4 }
```

数组是特殊的对象，所以对象的扩展运算符也可以用于数组。

```javascript
let foo = { ...['a', 'b', 'c'] };
foo
// {0: "a", 1: "b", 2: "c"}
```

如果扩展运算符后面是一个空对象，则没有任何效果。

```javascript
{...{}, a: 1}
// { a: 1 }
```

如果扩展运算符后面不是对象，则会自动将其转为对象。

```javascript
// 等同于 {...Object(1)}
{...1} // {}
```


对象的扩展运算符等同于使用`Object.assign()`方法

```javascript
let aClone = { ...a };
// 等同于
let aClone = Object.assign({}, a);
```

扩展运算符可以用于合并两个对象。

```javascript
let ab = { ...a, ...b };
// 等同于
let ab = Object.assign({}, a, b);
```

与数组的扩展运算符一样，对象的扩展运算符后面可以跟表达式。

```javascript
const obj = {
  ...(x > 1 ? {a: 1} : {}),
  b: 2,
};
```

### 链判断运算符

`ES2020` 引入了“链判断运算符”（optional chaining operator）`?.`

```javascript
const firstName = message?.body?.user?.firstName || 'default';
const fooValue = myForm.querySelector('input[name=foo]')?.value
```

链判断运算符有三种用法:

- `obj?.prop` // 对象属性
- `obj?.[expr]` // 同上
- `func?.(...args)` // 函数或对象方法的调用

```javascript
// 判断对象方法是否存在，如果存在则立即执行
iterator.return?.()
```

下面是这个运算符常见的使用形式：

```javascript
a?.b
// 等同于
a == null ? undefined : a.b

a?.[x]
// 等同于
a == null ? undefined : a[x]

a?.b()
// 等同于
a == null ? undefined : a.b()

a?.()
// 等同于
a == null ? undefined : a()
```

### Null 判断运算符

`ES2020` 引入了一个新的 `Null` 判断运算符`??`。它的行为类似`||`，但是只有运算符左侧的值为`null`或`undefined`时，才会返回右侧的值

```javascript
const headerText = response.settings.headerText ?? 'Hello, world!';
const animationDuration = response.settings.animationDuration ?? 300;
const showSplashScreen = response.settings.showSplashScreen ?? true;
```

这个运算符跟链判断运算符 `?.` 配合使用，为`null`或`undefined`的值设置默认值。

```javascript
const animationDuration = response.settings?.animationDuration ?? 300;
```

## 对象的新增方法

### Object.is()

`ES6` 提出“Same-value equality”（同值相等）算法, `Object.is`就是部署这个算法的新方法。它用来比较两个值是否严格相等，与严格比较运算符（`===`）的行为基本一致

```javascript
Object.is('foo', 'foo')
// true
Object.is({}, {})
// false
```

同时它也解决了 `ES5` 中的两个问题：+0不等于-0，NaN等于自身

```javascript
// ES5
+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true
```

### Object.assign()

`Object.assign`方法用于对象的合并，将源对象（`source`）的所有可枚举属性，复制到目标对象（`target`）

```javascript
const target = { a: 1 };

const source1 = { b: 2 };
const source2 = { c: 3 };

Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}
```

`Object.assign`方法的第一个参数是目标对象，后面的参数都是源对象

如果只有一个参数，`Object.assign`会直接返回该参数。

```javascript
const obj = {a: 1};
Object.assign(obj) === obj // true
```

如果该参数不是对象，则会先转成对象，然后返回。

```javascript
typeof Object.assign(2) // "object"
```

由于`undefined`和`null`无法转成对象，所以如果它们作为参数，就会报错。

```javascript
Object.assign(undefined) // 报错
Object.assign(null) // 报错
```

`Object.assign`拷贝的属性是有限制的，只拷贝源对象的自身属性（不拷贝继承属性），也不拷贝不可枚举的属性（`enumerable: false`）

```javascript
Object.assign({b: 'c'},
  Object.defineProperty({}, 'invisible', {
    enumerable: false,
    value: 'hello'
  })
)
// { b: 'c' }
```

注意点：

- `Object.assign`方法实行的是浅拷贝，而不是深拷贝。也就是说，如果源对象某个属性的值是对象，那么目标对象拷贝得到的是这个对象的引用

  ```javascript
  const obj1 = {a: {b: 1}};
  const obj2 = Object.assign({}, obj1);

  obj1.a.b = 2;
  obj2.a.b // 2
  ```

- 对于这种嵌套的对象，一旦遇到同名属性，`Object.assign`的处理方法是替换，而不是添加

  ```javascript
  const target = { a: { b: 'c', d: 'e' } }
  const source = { a: { b: 'hello' } }
  Object.assign(target, source)
  // { a: { b: 'hello' } }
  ```

- `Object.assign`可以用来处理数组，但是会把数组视为对象

  ```javascript
  Object.assign([1, 2, 3], [4, 5])
  // [4, 5, 3]
  ```

- `Object.assign`只能进行值的复制，如果要复制的值是一个取值函数，那么将求值后再复制

  ```javascript
  const source = {
    get foo() { return 1 }
  };
  const target = {};

  Object.assign(target, source)
  // { foo: 1 }
  ```
  
常见用途:

- 为对象添加属性

  ```javascript
  class Point {
    constructor(x, y) {
      Object.assign(this, {x, y});
    }
  }
  ```

- 为对象添加方法

  ```javascript
  Object.assign(SomeClass.prototype, {
    someMethod(arg1, arg2) {
      ···
    },
    anotherMethod() {
      ···
    }
  });

  // 等同于下面的写法
  SomeClass.prototype.someMethod = function (arg1, arg2) {
    ···
  };
  SomeClass.prototype.anotherMethod = function () {
    ···
  };
  ```

- 克隆对象

  ```javascript
  function clone(origin) {
    return Object.assign({}, origin);
  }
  ```

- 合并多个对象

  ```javascript
  const merge =
    (target, ...sources) => Object.assign(target, ...sources);
  ```

- 为属性指定默认值

  ```javascript
  const DEFAULTS = {
    logLevel: 0,
    outputFormat: 'html'
  };

  function processContent(options) {
    options = Object.assign({}, DEFAULTS, options);
    console.log(options);
    // ...
  }
  ```

### Object.getOwnPropertyDescriptors()

`ES5` 的`Object.getOwnPropertyDescriptor()`方法会返回某个对象属性的描述对象（`descriptor`）。`ES2017` 引入了`Object.getOwnPropertyDescriptors()`方法，返回指定对象所有自身属性（非继承属性）的描述对象

```javascript
const obj = {
  foo: 123,
  get bar() { return 'abc' }
};

Object.getOwnPropertyDescriptors(obj)
// { foo:
//    { value: 123,
//      writable: true,
//      enumerable: true,
//      configurable: true },
//   bar:
//    { get: [Function: get bar],
//      set: undefined,
//      enumerable: true,
//      configurable: true } }
```

该方法的引入目的，主要是为了解决`Object.assign()`无法正确拷贝`get`属性和`set`属性的问题

### __proto__属性，Object.setPrototypeOf()，Object.getPrototypeOf()

`JavaScript` 语言的对象继承是通过原型链实现的。`ES6` 提供了更多原型对象的操作方法

#### __proto__属性

`__proto__`属性（前后各两个下划线），用来读取或设置当前对象的原型对象（`prototype`）。目前，所有浏览器（包括 IE11）都部署了这个属性

```javascript
// es5 的写法
const obj = {
  method: function() { ... }
};
obj.__proto__ = someOtherObj;

// es6 的写法
var obj = Object.create(someOtherObj);
obj.method = function() { ... };
```

虽然 `__proto__` 属性已成为 `ES6` 的标准，但无论从语义的角度，还是从兼容性的角度，都不要使用这个属性，而是使用以下API：

- `Object.setPrototypeOf()`（写操作）
- `Object.getPrototypeOf()`（读操作）
- `Object.create()`（生成操作）

#### Object.setPrototypeOf()

`Object.setPrototypeOf()`方法的作用与`__proto__`相同，用来设置一个对象的原型对象（`prototype`），返回参数对象本身。它是 `ES6` 正式推荐的设置原型对象的方法。

```javascript
// 格式
Object.setPrototypeOf(object, prototype)

// 用法
const o = Object.setPrototypeOf({}, null);
```

例子：

```javascript
let proto = {};
let obj = { x: 10 };
Object.setPrototypeOf(obj, proto);

proto.y = 20;
proto.z = 40;

obj.x // 10
obj.y // 20
obj.z // 40
```

#### Object.getPrototypeOf()

该方法与`Object.setPrototypeOf`方法配套，用于读取一个对象的原型对象

```javascript
function Rectangle() {
  // ...
}

const rec = new Rectangle();

Object.getPrototypeOf(rec) === Rectangle.prototype
// true

Object.setPrototypeOf(rec, Object.prototype);
Object.getPrototypeOf(rec) === Rectangle.prototype
// false
```

### Object.keys()，Object.values()，Object.entries()

#### Object.keys()

`ES5` 引入了`Object.keys`方法，返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（`enumerable`）属性的键名

```javascript
var obj = { foo: 'bar', baz: 42 };
Object.keys(obj)
// ["foo", "baz"]
```

`ES2017` 引入了跟`Object.keys`配套的`Object.values`和`Object.entries`，作为遍历一个对象的补充手段，供`for...of`循环使用

```javascript
let {keys, values, entries} = Object;
let obj = { a: 1, b: 2, c: 3 };

for (let key of keys(obj)) {
  console.log(key); // 'a', 'b', 'c'
}

for (let value of values(obj)) {
  console.log(value); // 1, 2, 3
}

for (let [key, value] of entries(obj)) {
  console.log([key, value]); // ['a', 1], ['b', 2], ['c', 3]
}
```

#### Object.values()

`Object.values`方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（`enumerable`）属性的键值

```javascript
const obj = { foo: 'bar', baz: 42 };
Object.values(obj)
// ["bar", 42]
```

`Object.values`只返回对象自身的可遍历属性。

```javascript
const obj = Object.create({}, {p: {value: 42}});
Object.values(obj) // []
```

#### Object.entries()

`Object.entries()`方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（`enumerable`）属性的键值对数组。

```javascript
const obj = { foo: 'bar', baz: 42 };
Object.entries(obj)
// [ ["foo", "bar"], ["baz", 42] ]
```

`Object.entries`的基本用途是遍历对象的属性

```javascript
let obj = { one: 1, two: 2 };
for (let [k, v] of Object.entries(obj)) {
  console.log(
    `${JSON.stringify(k)}: ${JSON.stringify(v)}`
  );
}
// "one": 1
// "two": 2
```

`Object.entries`方法的另一个用处是，将对象转为真正的`Map`结构。

```javascript
const obj = { foo: 'bar', baz: 42 };
const map = new Map(Object.entries(obj));
map // Map { foo: "bar", baz: 42 }
```

### Object.fromEntries()

`Object.fromEntries()`方法是`Object.entries()`的逆操作，用于将一个键值对数组转为对象。

```javascript
Object.fromEntries([
  ['foo', 'bar'],
  ['baz', 42]
])
// { foo: "bar", baz: 42 }
```

## Symbol

`ES6` 引入`Symbol`, 是为了解决对象属性可能会重复的问题

`ES6` 引入了一种新的原始数据类型`Symbol`，表示独一无二的值。它是 `JavaScript` 语言的第七种数据类型，前六种是：`undefined`、`null`、布尔值（`Boolean`）、字符串（`String`）、数值（`Number`）、对象（`Object`）。

`Symbol` 值通过`Symbol`函数生成。这就是说，对象的属性名现在可以有两种类型，一种是原来就有的字符串，另一种就是新增的 `Symbol` 类型

```javascript
let s = Symbol();

typeof s
// "symbol"
```

`Symbol`函数前不能使用`new`命令，否则会报错

`Symbol`函数可以接受一个字符串作为参数，表示对 `Symbol` 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分

```javascript
let s1 = Symbol('foo');
let s2 = Symbol('bar');

s1 // Symbol(foo)
s2 // Symbol(bar)

s1.toString() // "Symbol(foo)"
s2.toString() // "Symbol(bar)"
```

### Symbol.prototype.description

创建 `Symbol` 的时候，可以添加一个描述。

```js
const sym = Symbol('foo');
```

`ES2019` 提供了一个实例属性`description`，直接返回 `Symbol` 的描述。

```js
const sym = Symbol('foo');

sym.description // "foo"
```

### 作为属性名的 Symbol

由于每一个 `Symbol` 值都是不相等的，这意味着 `Symbol` 值可以作为标识符，用于对象的属性名，就能保证不会出现同名的属性

```js
let mySymbol = Symbol();

// 第一种写法
let a = {};
a[mySymbol] = 'Hello!';

// 第二种写法
let a = {
  [mySymbol]: 'Hello!'
};

// 第三种写法
let a = {};
Object.defineProperty(a, mySymbol, { value: 'Hello!' });

// 以上写法都得到同样结果
a[mySymbol] // "Hello!"
```

`Symbol` 类型还可以用于定义一组常量，保证这组常量的值都是不相等的

```js
const log = {};

log.levels = {
  DEBUG: Symbol('debug'),
  INFO: Symbol('info'),
  WARN: Symbol('warn')
};
console.log(log.levels.DEBUG, 'debug message');
console.log(log.levels.INFO, 'info message');
```

### 消除魔术字符串

魔术字符串指的是，在代码之中多次出现、与代码形成强耦合的某一个具体的字符串或者数值。风格良好的代码，应该尽量消除魔术字符串，改由含义清晰的变量代替, 常用的消除魔术字符串的方法，就是把它写成一个变量

```js
const shapeType = {
  triangle: 'Triangle'
};

function getArea(shape, options) {
  let area = 0;
  switch (shape) {
    case shapeType.triangle:
      area = .5 * options.width * options.height;
      break;
  }
  return area;
}

getArea(shapeType.triangle, { width: 100, height: 100 });
```

### 属性名的遍历

`Symbol` 作为属性名，遍历对象的时候，该属性不会出现在`for...in`、`for...of`循环中，也不会被`Object.keys()`、`Object.getOwnPropertyNames()`、`JSON.stringify()`返回

`Object.getOwnPropertySymbols()`方法，可以获取指定对象的所有 `Symbol` 属性名。该方法返回一个数组，成员是当前对象的所有用作属性名的 `Symbol` 值

```js
const obj = {};
let a = Symbol('a');
let b = Symbol('b');

obj[a] = 'Hello';
obj[b] = 'World';

const objectSymbols = Object.getOwnPropertySymbols(obj);

objectSymbols
// [Symbol(a), Symbol(b)]
```

使用`for...in`循环和`Object.getOwnPropertyNames()`方法都得不到 `Symbol` 键名，需要使用`Object.getOwnPropertySymbols()`方法

另一个新的 API，`Reflect.ownKeys()`方法可以返回所有类型的键名，包括常规键名和 `Symbol` 键名

```js
let obj = {
  [Symbol('my_key')]: 1,
  enum: 2,
  nonEnum: 3
};

Reflect.ownKeys(obj)
//  ["enum", "nonEnum", Symbol(my_key)]
```

### Symbol.for()，Symbol.keyFor()

`Symbol.for()`方法接受一个字符串作为参数，然后搜索有没有以该参数作为名称的 `Symbol` 值。如果有，就返回这个 `Symbol` 值，否则就新建一个以该字符串为名称的 `Symbol` 值，并将其注册到全局。

```js
let s1 = Symbol.for('foo');
let s2 = Symbol.for('foo');

s1 === s2 // true
```

`Symbol.for()`与`Symbol()`这两种写法，都会生成新的 `Symbol`。它们的区别是，前者会被登记在全局环境中供搜索，后者不会

`Symbol.keyFor()`方法返回一个已登记的 `Symbol` 类型值的`key`

```js
let s1 = Symbol.for("foo");
Symbol.keyFor(s1) // "foo"

let s2 = Symbol("foo");
Symbol.keyFor(s2) // undefined
```

### 模块的 Singleton 模式

`Singleton` 模式指的是调用一个类，任何时候返回的都是同一个实例

在 `Nodejs` 中实现 `Singleton` 模式，只需要把实例放到顶层对象 `Global` 里就可以了，但问题是这个放在顶层对象中的实例可以被修改，此时可以通过 `Symbol` 来实现

### 内置的 Symbol 值

`ES6` 还提供了 11 个内置的 `Symbol` 值，指向语言内部使用的方法

#### Symbol.hasInstance

对象的`Symbol.hasInstance`属性，指向一个内部方法。当其他对象使用`instanceof`运算符，判断是否为该对象的实例时，会调用这个方法

```js
class MyClass {
  [Symbol.hasInstance](foo) {
    return foo instanceof Array;
  }
}

[1, 2, 3] instanceof new MyClass() // true
```

#### Symbol.isConcatSpreadable

对象的`Symbol.isConcatSpreadable`属性等于一个布尔值，表示该对象用于`Array.prototype.concat()`时，是否可以展开

```js
let arr1 = ['c', 'd'];
['a', 'b'].concat(arr1, 'e') // ['a', 'b', 'c', 'd', 'e']
arr1[Symbol.isConcatSpreadable] // undefined

let arr2 = ['c', 'd'];
arr2[Symbol.isConcatSpreadable] = false;
['a', 'b'].concat(arr2, 'e') // ['a', 'b', ['c','d'], 'e']
```

#### Symbol.species

对象的`Symbol.species`属性，指向一个构造函数。创建衍生对象时，会使用该属性

```js
class MyArray extends Array {
}

const a = new MyArray(1, 2, 3);
const b = a.map(x => x);
const c = a.filter(x => x > 1);

b instanceof MyArray // true
c instanceof MyArray // true
```

```js
class MyArray extends Array {
  static get [Symbol.species]() { return Array; }
}
```

上面代码中，由于定义了`Symbol.species`属性，创建衍生对象时就会使用这个属性返回的函数，作为构造函数

#### Symbol.match

对象的`Symbol.match`属性，指向一个函数。当执行`str.match(myObject)`时，如果该属性存在，会调用它，返回该方法的返回值

```js
String.prototype.match(regexp)
// 等同于
regexp[Symbol.match](this)

class MyMatcher {
  [Symbol.match](string) {
    return 'hello world'.indexOf(string);
  }
}

'e'.match(new MyMatcher()) // 1
```

#### Symbol.replace

对象的`Symbol.replace`属性，指向一个方法，当该对象被`String.prototype.replace`方法调用时，会返回该方法的返回值。

```js
String.prototype.replace(searchValue, replaceValue)
// 等同于
searchValue[Symbol.replace](this, replaceValue)
```

#### Symbol.search

对象的`Symbol.search`属性，指向一个方法，当该对象被`String.prototype.search`方法调用时，会返回该方法的返回值。

```js
String.prototype.search(regexp)
// 等同于
regexp[Symbol.search](this)

class MySearch {
  constructor(value) {
    this.value = value;
  }
  [Symbol.search](string) {
    return string.indexOf(this.value);
  }
}
'foobar'.search(new MySearch('foo')) // 0
```

#### Symbol.split

对象的`Symbol.split`属性，指向一个方法，当该对象被`String.prototype.split`方法调用时，会返回该方法的返回值。

```js
String.prototype.split(separator, limit)
// 等同于
separator[Symbol.split](this, limit)
```

#### Symbol.iterator

对象的`Symbol.iterator`属性，指向该对象的默认遍历器方法

```js
const myIterable = {};
myIterable[Symbol.iterator] = function* () {
  yield 1;
  yield 2;
  yield 3;
};

[...myIterable] // [1, 2, 3]
```

#### Symbol.toPrimitive

对象的`Symbol.toPrimitive`属性，指向一个方法。该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值

`Symbol.toPrimitive`被调用时，会接受一个字符串参数，表示当前运算的模式，一共有三种模式。

- `Number`：该场合需要转成数值
- `String`：该场合需要转成字符串
- `Default`：该场合可以转成数值，也可以转成字符串

```js
let obj = {
  [Symbol.toPrimitive](hint) {
    switch (hint) {
      case 'number':
        return 123;
      case 'string':
        return 'str';
      case 'default':
        return 'default';
      default:
        throw new Error();
     }
   }
};

2 * obj // 246
3 + obj // '3default'
obj == 'default' // true
String(obj) // 'str'
```

#### Symbol.toStringTag

对象的`Symbol.toStringTag`属性，指向一个方法。在该对象上面调用`Object.prototype.toString`方法时，如果这个属性存在，它的返回值会出现在`toString`方法返回的字符串之中，表示对象的类型

#### Symbol.unscopables

对象的`Symbol.unscopables`属性，指向一个对象。该对象指定了使用`with`关键字时，哪些属性会被`with`环境排除

## Set和Map数据结构

### Set

#### 基本用法

`ES6` 提供了新的数据结构 `Set`。它类似于数组，但是成员的值都是唯一的，没有重复的值。

`Set`本身是一个构造函数，用来生成 `Set` 数据结构

```js
const s = new Set();

[2, 3, 5, 4, 5, 2, 2].forEach(x => s.add(x));

for (let i of s) {
  console.log(i);
}
// 2 3 5 4
```

`Set`函数可以接受一个数组（或者具有 `iterable` 接口的其他数据结构）作为参数，用来初始化。

```js
// 例一
const set = new Set([1, 2, 3, 4, 4]);
[...set]
// [1, 2, 3, 4]

// 例二
const items = new Set([1, 2, 3, 4, 5, 5, 5, 5]);
items.size // 5

// 例三
const set = new Set(document.querySelectorAll('div'));
set.size // 56

// 类似于
const set = new Set();
document
 .querySelectorAll('div')
 .forEach(div => set.add(div));
set.size // 56
```

`Set`也成为一种去除数组重复成员的方法

```js
// 去除数组的重复成员
[...new Set(array)]
```

也可以用于去除字符串里面的重复字符

```js
[...new Set('ababbc')].join('')
// "abc"
```

#### Set 实例的属性和方法

`Set` 结构的实例有以下属性:

- `Set.prototype.constructor`：构造函数，默认就是`Set`函数。
- `Set.prototype.size`：返回`Set`实例的成员总数。

`Set` 实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。下面先介绍四个操作方法。

- `Set.prototype.add(value)`：添加某个值，返回 `Set` 结构本身。
- `Set.prototype.delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
- `Set.prototype.has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。
- `Set.prototype.clear()`：清除所有成员，没有返回值

```js
s.add(1).add(2).add(2);
// 注意2被加入了两次

s.size // 2

s.has(1) // true
s.has(2) // true
s.has(3) // false

s.delete(2);
s.has(2) // false
```

`Array.from`方法可以将 `Set` 结构转为数组

```js
const items = new Set([1, 2, 3, 4, 5]);
const array = Array.from(items);
```

#### 遍历操作

`Set` 结构的实例有四个遍历方法，可以用于遍历成员。

- `Set.prototype.keys()`：返回键名的遍历器
- `Set.prototype.values()`：返回键值的遍历器
- `Set.prototype.entries()`：返回键值对的遍历器
- `Set.prototype.forEach()`：使用回调函数遍历每个成员

`keys`方法、`values`方法、`entries`方法返回的都是遍历器对象

```js
let set = new Set(['red', 'green', 'blue']);

for (let item of set.keys()) {
  console.log(item);
}
// red
// green
// blue

for (let item of set.values()) {
  console.log(item);
}
// red
// green
// blue

for (let item of set.entries()) {
  console.log(item);
}
// ["red", "red"]
// ["green", "green"]
// ["blue", "blue"]
```

`Set` 结构可以直接用`for...of`循环遍历

```js
let set = new Set(['red', 'green', 'blue']);

for (let x of set) {
  console.log(x);
}
// red
// green
// blue
```

`Set` 结构的实例与数组一样，也拥有`forEach`方法，用于对每个成员执行某种操作，没有返回值

```js
let set = new Set([1, 4, 9]);
set.forEach((value, key) => console.log(key + ' : ' + value))
// 1 : 1
// 4 : 4
// 9 : 9
```

扩展运算符（`...`）内部使用`for...of`循环，所以也可以用于 `Set` 结构

```js
let set = new Set(['red', 'green', 'blue']);
let arr = [...set];
// ['red', 'green', 'blue']
```

扩展运算符和 `Set` 结构相结合，就可以去除数组的重复成员。

```js
let arr = [3, 5, 2, 2, 5, 5];
let unique = [...new Set(arr)];
// [3, 5, 2]
```

数组的`map`和`filter`方法也可以间接用于 `Set `

```js
let set = new Set([1, 2, 3]);
set = new Set([...set].map(x => x * 2));
// 返回Set结构：{2, 4, 6}

let set = new Set([1, 2, 3, 4, 5]);
set = new Set([...set].filter(x => (x % 2) == 0));
// 返回Set结构：{2, 4}
```

使用 `Set` 可以很容易地实现并集（`Union`）、交集（`Intersect`）和差集（`Difference`）

```js
let a = new Set([1, 2, 3]);
let b = new Set([4, 3, 2]);

// 并集
let union = new Set([...a, ...b]);
// Set {1, 2, 3, 4}

// 交集
let intersect = new Set([...a].filter(x => b.has(x)));
// set {2, 3}

// （a 相对于 b 的）差集
let difference = new Set([...a].filter(x => !b.has(x)));
// Set {1}
```

### WeakSet

#### 含义

`WeakSet` 的成员只能是对象，而不能是其他类型的值

```js
const ws = new WeakSet();
ws.add(1)
// TypeError: Invalid value used in weak set
ws.add(Symbol())
// TypeError: invalid value used in weak set
```

`WeakSet` 中的对象都是弱引用，即垃圾回收机制不考虑 `WeakSet` 对该对象的引用，也就是说，如果其他对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于 `WeakSet` 之中

`ES6` 规定 `WeakSet` 不可遍历

#### 语法

`WeakSet` 是一个构造函数，可以使用`new`命令，创建 `WeakSet` 数据结构

```js
const ws = new WeakSet();
```

作为构造函数，`WeakSet` 可以接受一个数组或类似数组的对象作为参数, 该数组的所有成员，都会自动成为 `WeakSet` 实例对象的成员。

```js
const a = [[1, 2], [3, 4]];
const ws = new WeakSet(a);
// WeakSet {[1, 2], [3, 4]}
```

`WeakSet` 结构有以下三个方法:

- `WeakSet.prototype.add(value)`：向 `WeakSet` 实例添加一个新成员。
- `WeakSet.prototype.delete(value)`：清除 `WeakSet` 实例的指定成员。
- `WeakSet.prototype.has(value)`：返回一个布尔值，表示某个值是否在 `WeakSet` 实例之中。

```js
const ws = new WeakSet();
const obj = {};
const foo = {};

ws.add(window);
ws.add(obj);

ws.has(window); // true
ws.has(foo);    // false

ws.delete(window);
ws.has(window);    // false
```

`WeakSet` 没有`size`属性，没有办法遍历它的成员

`WeakSet` 的一个用处，是储存 `DOM` 节点，而不用担心这些节点从文档移除时，会引发内存泄漏

### Map

#### 含义和基本用法

`JavaScript` 的对象（`Object`），本质上是键值对的集合（`Hash` 结构），但是传统上只能用字符串当作键

`ES6` 提供了 `Map` 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键

```js
const m = new Map();
const o = {p: 'Hello World'};

m.set(o, 'content')
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false
```

作为构造函数，`Map` 也可以接受一个数组作为参数。该数组的成员是一个个表示键值对的数组

```js
const map = new Map([
  ['name', '张三'],
  ['title', 'Author']
]);

map.size // 2
map.has('name') // true
map.get('name') // "张三"
map.has('title') // true
map.get('title') // "Author"
```

不仅仅是数组，任何具有 `Iterator` 接口、且每个成员都是一个双元素的数组的数据结构都可以当作`Map`构造函数的参数

```js
const set = new Set([
  ['foo', 1],
  ['bar', 2]
]);
const m1 = new Map(set);
m1.get('foo') // 1

const m2 = new Map([['baz', 3]]);
const m3 = new Map(m2);
m3.get('baz') // 3
```

#### 实例的属性和操作方法

- `size`属性返回 `Map` 结构的成员总数

  ```js
  const map = new Map();
  map.set('foo', true);
  map.set('bar', false);

  map.size // 2
  ```

- `Map.prototype.set(key, value)`, `set`方法设置键名`key`对应的键值为`value`，然后返回整个 `Map` 结构。如果`key`已经有值，则键值会被更新，否则就新生成该键

  ```js
  const m = new Map();

  m.set('edition', 6)        // 键是字符串
  m.set(262, 'standard')     // 键是数值
  m.set(undefined, 'nah')    // 键是 undefined
  ```

- `Map.prototype.get(key)`, `get`方法读取`key`对应的键值，如果找不到`key`，返回`undefined`

  ```js
  const m = new Map();

  const hello = function() {console.log('hello');};
  m.set(hello, 'Hello ES6!') // 键是函数

  m.get(hello)  // Hello ES6!
  ```

- `Map.prototype.has(key)`, `has`方法返回一个布尔值，表示某个键是否在当前 `Map` 对象之中。

  ```js
  const m = new Map();

  m.set('edition', 6);
  m.set(262, 'standard');
  m.set(undefined, 'nah');

  m.has('edition')     // true
  m.has('years')       // false
  m.has(262)           // true
  m.has(undefined)     // true
  ```

- `Map.prototype.delete(key)`, `delete`方法删除某个键，返回`true`。如果删除失败，返回`false`。

  ```js
  const m = new Map();
  m.set(undefined, 'nah');
  m.has(undefined)     // true

  m.delete(undefined)
  m.has(undefined)       // false
  ```

- `Map.prototype.clear()`, `clear`方法清除所有成员，没有返回值。

  ```js
  let map = new Map();
  map.set('foo', true);
  map.set('bar', false);

  map.size // 2
  map.clear()
  map.size // 0
  ```

#### 遍历方法

`Map` 结构原生提供三个遍历器生成函数和一个遍历方法。

- `Map.prototype.keys()`：返回键名的遍历器。
- `Map.prototype.values()`：返回键值的遍历器。
- `Map.prototype.entries()`：返回所有成员的遍历器。
- `Map.prototype.forEach()`：遍历 `Map` 的所有成员。

```js
const map = new Map([
  ['F', 'no'],
  ['T',  'yes'],
]);

for (let key of map.keys()) {
  console.log(key);
}
// "F"
// "T"

for (let value of map.values()) {
  console.log(value);
}
// "no"
// "yes"

for (let item of map.entries()) {
  console.log(item[0], item[1]);
}
// "F" "no"
// "T" "yes"

// 或者
for (let [key, value] of map.entries()) {
  console.log(key, value);
}
// "F" "no"
// "T" "yes"

// 等同于使用map.entries()
for (let [key, value] of map) {
  console.log(key, value);
}
// "F" "no"
// "T" "yes"
```

`Map` 结构转为数组结构，比较快速的方法是使用扩展运算符（`...`）。

```js
const map = new Map([
  [1, 'one'],
  [2, 'two'],
  [3, 'three'],
]);

[...map.keys()]
// [1, 2, 3]

[...map.values()]
// ['one', 'two', 'three']

[...map.entries()]
// [[1,'one'], [2, 'two'], [3, 'three']]

[...map]
// [[1,'one'], [2, 'two'], [3, 'three']]
```

结合数组的`map`方法、`filter`方法，可以实现 `Map` 的遍历和过滤

```js
const map0 = new Map()
  .set(1, 'a')
  .set(2, 'b')
  .set(3, 'c');

const map1 = new Map(
  [...map0].filter(([k, v]) => k < 3)
);
// 产生 Map 结构 {1 => 'a', 2 => 'b'}

const map2 = new Map(
  [...map0].map(([k, v]) => [k * 2, '_' + v])
    );
// 产生 Map 结构 {2 => '_a', 4 => '_b', 6 => '_c'}
```

#### 与其他数据结构的互相转换

- `Map` 转为数组, `Map` 转为数组最方便的方法，就是使用扩展运算符（`...`）。

  ```js
  const myMap = new Map()
    .set(true, 7)
    .set({foo: 3}, ['abc']);
  [...myMap]
  // [ [ true, 7 ], [ { foo: 3 }, [ 'abc' ] ] ]
  ```

- 数组 转为 `Map`, 将数组传入 `Map` 构造函数，就可以转为 `Map`。

  ```js
  new Map([
    [true, 7],
    [{foo: 3}, ['abc']]
  ])
  // Map {
  //   true => 7,
  //   Object {foo: 3} => ['abc']
  // }
  ```

- `Map` 转为对象, 如果所有 `Map` 的键都是字符串，它可以无损地转为对象。

  ```js
  function strMapToObj(strMap) {
    let obj = Object.create(null);
    for (let [k,v] of strMap) {
      obj[k] = v;
    }
    return obj;
  }

  const myMap = new Map()
    .set('yes', true)
    .set('no', false);
  strMapToObj(myMap)
  // { yes: true, no: false }
  ```

- 对象转为 `Map`, 对象转为 `Map` 可以通过`Object.entries()`。

  ```js
  let obj = {"a":1, "b":2};
  let map = new Map(Object.entries(obj));
  ```

- `Map` 转为 `JSON`
  
  `Map` 转为 `JSON` 要区分两种情况。一种情况是，`Map` 的键名都是字符串，这时可以选择转为对象 `JSON`。

  ```js
  function strMapToJson(strMap) {
    return JSON.stringify(strMapToObj(strMap));
  }

  let myMap = new Map().set('yes', true).set('no', false);
  strMapToJson(myMap)
  // '{"yes":true,"no":false}'
  ```

  另一种情况是，`Map` 的键名有非字符串，这时可以选择转为数组 `JSON`。

  ```js
  function mapToArrayJson(map) {
    return JSON.stringify([...map]);
  }

  let myMap = new Map().set(true, 7).set({foo: 3}, ['abc']);
  mapToArrayJson(myMap)
  // '[[true,7],[{"foo":3},["abc"]]]'
  ```

- `JSON` 转为 `Map`

  `JSON` 转为 `Map`，正常情况下，所有键名都是字符串。

  ```js
  function jsonToStrMap(jsonStr) {
    return objToStrMap(JSON.parse(jsonStr));
  }

  jsonToStrMap('{"yes": true, "no": false}')
  // Map {'yes' => true, 'no' => false}
  ```

### WeakMap

#### 含义

`WeakMap`结构与`Map`结构类似，也是用于生成键值对的集合。

```js
// WeakMap 可以使用 set 方法添加成员
const wm1 = new WeakMap();
const key = {foo: 1};
wm1.set(key, 2);
wm1.get(key) // 2

// WeakMap 也可以接受一个数组，
// 作为构造函数的参数
const k1 = [1, 2, 3];
const k2 = [4, 5, 6];
const wm2 = new WeakMap([[k1, 'foo'], [k2, 'bar']]);
wm2.get(k2) // "bar"
```

`WeakMap`与`Map`的区别有两点:

- `WeakMap`只接受对象作为键名（`null`除外），不接受其他类型的值作为键名。

  ```js
  const map = new WeakMap();
  map.set(1, 2)
  // TypeError: 1 is not an object!
  map.set(Symbol(), 2)
  // TypeError: Invalid value used as weak map key
  map.set(null, 2)
  // TypeError: Invalid value used as weak map key
  ```

- `WeakMap`的键名所指向的对象，不计入垃圾回收机制

`WeakMap` 键名所引用的对象都是弱引用，即垃圾回收机制不将该引用考虑在内。因此，只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存

基本上，如果你要往对象上添加数据，又不想干扰垃圾回收机制，就可以使用 `WeakMap`。一个典型应用场景是，在网页的 `DOM` 元素上添加数据，就可以使用`WeakMap`结构。当该 `DOM` 元素被清除，其所对应的`WeakMap`记录就会自动被移除。

```js
const wm = new WeakMap();

const element = document.getElementById('example');

wm.set(element, 'some information');
wm.get(element) // "some information"
```

注意，`WeakMap` 弱引用的只是键名，而不是键值。键值依然是正常引用。

```js
const wm = new WeakMap();
let key = {};
let obj = {foo: 1};

wm.set(key, obj);
obj = null;
wm.get(key)
// Object {foo: 1}
```

#### WeakMap 的语法

`WeakMap` 与 `Map` 在 `API` 上的区别主要是两个，一是没有遍历操作（即没有`keys()`、`values()`和`entries()`方法），也没有`size`属性, 无法清空，即不支持`clear`方法

`WeakMap`只有四个方法可用：`get()`、`set()`、`has()`、`delete()`

```js
const wm = new WeakMap();

// size、forEach、clear 方法都不存在
wm.size // undefined
wm.forEach // undefined
wm.clear // undefined
```

## Proxy

### 概述

`Proxy` 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming），即对编程语言进行编程。

`Proxy` 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写.

```js
var obj = new Proxy({}, {
  get: function (target, propKey, receiver) {
    console.log(`getting ${propKey}!`);
    return Reflect.get(target, propKey, receiver);
  },
  set: function (target, propKey, value, receiver) {
    console.log(`setting ${propKey}!`);
    return Reflect.set(target, propKey, value, receiver);
  }
});
```

`ES6` 原生提供 `Proxy` 构造函数，用来生成 `Proxy` 实例。

```js
var proxy = new Proxy(target, handler);
```

`Proxy` 支持的拦截操作一览，一共 13 种。

- `get(target, propKey, receiver)`：拦截对象属性的读取，比如`proxy.foo`和`proxy['foo']`。
- `set(target, propKey, value, receiver)`：拦截对象属性的设置，比如`proxy.foo = v`或`proxy['foo'] = v`，返回一个布尔值。
- `has(target, propKey)`：拦截`propKey in proxy`的操作，返回一个布尔值。
- `deleteProperty(target, propKey)`：拦截d`elete proxy[propKey]`的操作，返回一个布尔值。
- `ownKeys(target)`：拦截`Object.getOwnPropertyNames(proxy)`、`Object.getOwnPropertySymbols(proxy)`、Object.keys(proxy)、for...in循环，返回一个数组。该方法返回目标对象所有自身的属性的属性名，而`Object.keys()`的返回结果仅包括目标对象自身的可遍历属性。
- `getOwnPropertyDescriptor(target, propKey)`：拦截`Object.getOwnPropertyDescriptor(proxy, propKey)`，返回属性的描述对象。
- `defineProperty(target, propKey, propDesc)`：拦截`Object.defineProperty(proxy, propKey, propDesc）`、`Object.defineProperties(proxy, propDescs)`，返回一个布尔值。
- `preventExtensions(target)`：拦截`Object.preventExtensions(proxy)`，返回一个布尔值。
- `getPrototypeOf(target)`：拦截`Object.getPrototypeOf(proxy)`，返回一个对象。
- `isExtensible(target)`：拦截`Object.isExtensible(proxy)`，返回一个布尔值。
- `setPrototypeOf(target, proto)`：拦截`Object.setPrototypeOf(proxy, proto)`，返回一个布尔值。如果目标对象是函数，那么还有两种额外操作可以拦截。
- `apply(target, object, args)`：拦截 `Proxy` 实例作为函数调用的操作，比如`proxy(...args)`、`proxy.call(object, ...args)`、`proxy.apply(...)`。
- `construct(target, args)`：拦截 `Proxy` 实例作为构造函数调用的操作，比如`new proxy(...args)`

### Proxy 实例的方法

#### get()

`get`方法用于拦截某个属性的读取操作，可以接受三个参数，依次为目标对象、属性名和 `proxy` 实例本身（严格地说，是操作行为所针对的对象），其中最后一个参数可选。

```js
var person = {
  name: "张三"
};

var proxy = new Proxy(person, {
  get: function(target, propKey) {
    if (propKey in target) {
      return target[propKey];
    } else {
      throw new ReferenceError("Prop name \"" + propKey + "\" does not exist.");
    }
  }
});

proxy.name // "张三"
proxy.age // 抛出一个错误
```

#### set()

`set`方法用来拦截某个属性的赋值操作，可以接受四个参数，依次为目标对象、属性名、属性值和 `Proxy` 实例本身，其中最后一个参数可选

```js
let validator = {
  set: function(obj, prop, value) {
    if (prop === 'age') {
      if (!Number.isInteger(value)) {
        throw new TypeError('The age is not an integer');
      }
      if (value > 200) {
        throw new RangeError('The age seems invalid');
      }
    }

    // 对于满足条件的 age 属性以及其他属性，直接保存
    obj[prop] = value;
  }
};

let person = new Proxy({}, validator);

person.age = 100;

person.age // 100
person.age = 'young' // 报错
person.age = 300 // 报错
```

#### apply()

`apply`方法拦截函数的调用、`call`和`apply`操作。

`apply`方法可以接受三个参数，分别是目标对象、目标对象的上下文对象（`this`）和目标对象的参数数组。

```js
var handler = {
  apply (target, ctx, args) {
    return Reflect.apply(...arguments);
  }
};
```

```js
var target = function () { return 'I am the target'; };
var handler = {
  apply: function () {
    return 'I am the proxy';
  }
};

var p = new Proxy(target, handler);

p()
// "I am the proxy"
```

```js
var twice = {
  apply (target, ctx, args) {
    return Reflect.apply(...arguments) * 2;
  }
};
function sum (left, right) {
  return left + right;
};
var proxy = new Proxy(sum, twice);
proxy(1, 2) // 6
proxy.call(null, 5, 6) // 22
proxy.apply(null, [7, 8]) // 30
```

#### has()

`has`方法用来拦截`HasProperty`操作，即判断对象是否具有某个属性时，这个方法会生效。典型的操作就是`in`运算符。

`has`方法可以接受两个参数，分别是目标对象、需查询的属性名。

下面的例子使用`has`方法隐藏某些属性，不被in运算符发现

```js
var handler = {
  has (target, key) {
    if (key[0] === '_') {
      return false;
    }
    return key in target;
  }
};
var target = { _prop: 'foo', prop: 'foo' };
var proxy = new Proxy(target, handler);
'_prop' in proxy // false
```

`has`方法拦截的是`HasProperty`操作，而不是`HasOwnProperty`操作，即`has`方法不判断一个属性是对象自身的属性，还是继承的属性

#### construct()

`construct`方法用于拦截`new`命令，下面是拦截对象的写法。

```js
var handler = {
  construct (target, args, newTarget) {
    return new target(...args);
  }
};
```


`construct`方法可以接受三个参数。

- `target`：目标对象
- `args`：构造函数的参数对象
- `newTarget`：创造实例对象时，`new`命令作用的构造函数

```js
var p = new Proxy(function () {}, {
  construct: function(target, args) {
    console.log('called: ' + args.join(', '));
    return { value: args[0] * 10 };
  }
});

(new p(1)).value
// "called: 1"
// 10
```

`construct`方法返回的必须是一个对象，否则会报错

#### deleteProperty()

`deleteProperty`方法用于拦截`delete`操作，如果这个方法抛出错误或者返回`false`，当前属性就无法被`delete`命令删除。

```js
var handler = {
  deleteProperty (target, key) {
    invariant(key, 'delete');
    delete target[key];
    return true;
  }
};
function invariant (key, action) {
  if (key[0] === '_') {
    throw new Error(`Invalid attempt to ${action} private "${key}" property`);
  }
}

var target = { _prop: 'foo' };
var proxy = new Proxy(target, handler);
delete proxy._prop
// Error: Invalid attempt to delete private "_prop" property
```

#### defineProperty()

`defineProperty()`方法拦截了`Object.defineProperty()`操作。

```js
var handler = {
  defineProperty (target, key, descriptor) {
    return false;
  }
};
var target = {};
var proxy = new Proxy(target, handler);
proxy.foo = 'bar' // 不会生效
```

#### getOwnPropertyDescriptor()

`getOwnPropertyDescriptor()`方法拦截`Object.getOwnPropertyDescriptor()`，返回一个属性描述对象或者`undefined`。

```js
var handler = {
  getOwnPropertyDescriptor (target, key) {
    if (key[0] === '_') {
      return;
    }
    return Object.getOwnPropertyDescriptor(target, key);
  }
};
var target = { _foo: 'bar', baz: 'tar' };
var proxy = new Proxy(target, handler);
Object.getOwnPropertyDescriptor(proxy, 'wat')
// undefined
Object.getOwnPropertyDescriptor(proxy, '_foo')
// undefined
Object.getOwnPropertyDescriptor(proxy, 'baz')
// { value: 'tar', writable: true, enumerable: true, configurable: true }
```

#### getPrototypeOf()

`getPrototypeOf()`方法主要用来拦截获取对象原型。具体来说，拦截下面这些操作。

- `Object.prototype.__proto__`
- `Object.prototype.isPrototypeOf()`
- `Object.getPrototypeOf()`
- `Reflect.getPrototypeOf()`
- `instanceof`

下面是一个例子。

```js
var proto = {};
var p = new Proxy({}, {
  getPrototypeOf(target) {
    return proto;
  }
});
Object.getPrototypeOf(p) === proto // true
```

#### isExtensible()

`isExtensible()`方法拦截`Object.isExtensible()`操作。

```js
var p = new Proxy({}, {
  isExtensible: function(target) {
    console.log("called");
    return true;
  }
});

Object.isExtensible(p)
// "called"
// true
```

#### ownKeys()

`ownKeys()`方法用来拦截对象自身属性的读取操作。具体来说，拦截以下操作。

- `Object.getOwnPropertyNames()`
- `Object.getOwnPropertySymbols()`
- `Object.keys()`
- `for...in`循环

下面是拦截`Object.keys()`的例子。

```js
let target = {
  a: 1,
  b: 2,
  c: 3
};

let handler = {
  ownKeys(target) {
    return ['a'];
  }
};

let proxy = new Proxy(target, handler);

Object.keys(proxy)
// [ 'a' ]
```

#### preventExtensions()

`preventExtensions()`方法拦截`Object.preventExtensions()`。该方法必须返回一个布尔值，否则会被自动转为布尔值。

这个方法有一个限制，只有目标对象不可扩展时（即`Object.isExtensible(proxy)`为`false`），`proxy.preventExtensions`才能返回`true`，否则会报错。

```js
var proxy = new Proxy({}, {
  preventExtensions: function(target) {
    return true;
  }
});

Object.preventExtensions(proxy)
// Uncaught TypeError: 'preventExtensions' on proxy: trap returned truish but the proxy target is extensible
```

#### setPrototypeOf()

`setPrototypeOf()`方法主要用来拦截`Object.setPrototypeOf()`方法。

下面是一个例子。

```js
var handler = {
  setPrototypeOf (target, proto) {
    throw new Error('Changing the prototype is forbidden');
  }
};
var proto = {};
var target = function () {};
var proxy = new Proxy(target, handler);
Object.setPrototypeOf(proxy, proto);
// Error: Changing the prototype is forbidden
```

### Proxy.revocable()

`Proxy.revocable()`方法返回一个可取消的 `Proxy` 实例。

```js
let target = {};
let handler = {};

let {proxy, revoke} = Proxy.revocable(target, handler);

proxy.foo = 123;
proxy.foo // 123

revoke();
proxy.foo // TypeError: Revoked
```

`Proxy.revocable()`的一个使用场景是，目标对象不允许直接访问，必须通过代理访问，一旦访问结束，就收回代理权，不允许再次访问

## Reflect

### 概述

`Reflect`对象与`Proxy`对象一样，也是 `ES6` 为了操作对象而提供的新 `API`

- 将`Object`对象的一些明显属于语言内部的方法（比如`Object.defineProperty`），放到`Reflect`对象上
- 修改某些`Object`方法的返回结果，让其变得更合理。比如，`Object.defineProperty(obj, name, desc)`在无法定义属性时，会抛出一个错误，而`Reflect.defineProperty(obj, name, desc)`则会返回`false`
- 让`Object`操作都变成函数行为。某些`Object`操作是命令式，比如`name in obj`和`delete obj[name]`，而`Reflect.has(obj, name)`和`Reflect.deleteProperty(obj, name)`让它们变成了函数行为

  ```js
  // 老写法
  'assign' in Object // true

  // 新写法
  Reflect.has(Object, 'assign') // true
  ```
- `Reflect`对象的方法与`Proxy`对象的方法一一对应，只要是`Proxy`对象的方法，就能在`Reflect`对象上找到对应的方法。这就让`Proxy`对象可以方便地调用对应的`Reflect`方法，完成默认行为，作为修改行为的基础。也就是说，不管`Proxy`怎么修改默认行为，你总可以在`Reflect`上获取默认行为

### 静态方法

`Reflect`对象一共有 `13` 个静态方法。

- `Reflect.apply(target, thisArg, args)`
- `Reflect.construct(target, args)`
- `Reflect.get(target, name, receiver)`
- `Reflect.set(target, name, value, receiver)`
- `Reflect.defineProperty(target, name, desc)`
- `Reflect.deleteProperty(target, name)`
- `Reflect.has(target, name)`
- `Reflect.ownKeys(target)`
- `Reflect.isExtensible(target)`
- `Reflect.preventExtensions(target)`
- `Reflect.getOwnPropertyDescriptor(target, name)`
- `Reflect.getPrototypeOf(target)`
- `Reflect.setPrototypeOf(target, prototype)`

#### Reflect.get(target, name, receiver)

`Reflect.get`方法查找并返回`target`对象的`name`属性，如果没有该属性，则返回`undefined`。

```js
var myObject = {
  foo: 1,
  bar: 2,
  get baz() {
    return this.foo + this.bar;
  },
}

Reflect.get(myObject, 'foo') // 1
Reflect.get(myObject, 'bar') // 2
Reflect.get(myObject, 'baz') // 3
```

#### Reflect.set(target, name, value, receiver)

`Reflect.set`方法设置`target`对象的`name`属性等于`value`。

```js
var myObject = {
  foo: 1,
  set bar(value) {
    return this.foo = value;
  },
}

myObject.foo // 1

Reflect.set(myObject, 'foo', 2);
myObject.foo // 2

Reflect.set(myObject, 'bar', 3)
myObject.foo // 3
```

#### Reflect.has(obj, name)

`Reflect.has`方法对应`name in obj`里面的`in`运算符。

```js
var myObject = {
  foo: 1,
};

// 旧写法
'foo' in myObject // true

// 新写法
Reflect.has(myObject, 'foo') // true
```

#### Reflect.deleteProperty(obj, name)

`Reflect.deleteProperty`方法等同于`delete obj[name]`，用于删除对象的属性。

```js
const myObj = { foo: 'bar' };

// 旧写法
delete myObj.foo;

// 新写法
Reflect.deleteProperty(myObj, 'foo');
```

该方法返回一个布尔值。如果删除成功，或者被删除的属性不存在，返回`true`；删除失败，被删除的属性依然存在，返回`false`

#### Reflect.construct(target, args)

`Reflect.construct`方法等同于`new target(...args)`，这提供了一种不使用`new`，来调用构造函数的方法。

```js
function Greeting(name) {
  this.name = name;
}

// new 的写法
const instance = new Greeting('张三');

// Reflect.construct 的写法
const instance = Reflect.construct(Greeting, ['张三']);
```

#### Reflect.getPrototypeOf(obj)

`Reflect.getPrototypeOf`方法用于读取对象的`__proto__`属性，对应`Object.getPrototypeOf(obj)`。

```js
const myObj = new FancyThing();

// 旧写法
Object.getPrototypeOf(myObj) === FancyThing.prototype;

// 新写法
Reflect.getPrototypeOf(myObj) === FancyThing.prototype;
```

#### Reflect.setPrototypeOf(obj, newProto)

`Reflect.setPrototypeOf`方法用于设置目标对象的原型（`prototype`），对应`Object.setPrototypeOf(obj, newProto)`方法。它返回一个布尔值，表示是否设置成功。

```js
const myObj = {};

// 旧写法
Object.setPrototypeOf(myObj, Array.prototype);

// 新写法
Reflect.setPrototypeOf(myObj, Array.prototype);

myObj.length // 0
```

#### Reflect.apply(func, thisArg, args)

`Reflect.apply`方法等同于`Function.prototype.apply.call(func, thisArg, args)`，用于绑定`this`对象后执行给定函数。

一般来说，如果要绑定一个函数的`this`对象，可以这样写`fn.apply(obj, args)`，但是如果函数定义了自己的`apply`方法，就只能写成`Function.prototype.apply.call(fn, obj, args)`，采用`Reflect`对象可以简化这种操作。

```js
const ages = [11, 33, 12, 54, 18, 96];

// 旧写法
const youngest = Math.min.apply(Math, ages);
const oldest = Math.max.apply(Math, ages);
const type = Object.prototype.toString.call(youngest);

// 新写法
const youngest = Reflect.apply(Math.min, Math, ages);
const oldest = Reflect.apply(Math.max, Math, ages);
const type = Reflect.apply(Object.prototype.toString, youngest, []);
```

#### Reflect.defineProperty(target, propertyKey, attributes)

`Reflect.defineProperty`方法基本等同于`Object.defineProperty`，用来为对象定义属性。未来，后者会被逐渐废除，请从现在开始就使用`Reflect.defineProperty`代替它。

```js
function MyDate() {
  /*…*/
}

// 旧写法
Object.defineProperty(MyDate, 'now', {
  value: () => Date.now()
});

// 新写法
Reflect.defineProperty(MyDate, 'now', {
  value: () => Date.now()
});
```

#### Reflect.getOwnPropertyDescriptor(target, propertyKey)

`Reflect.getOwnPropertyDescriptor`基本等同于`Object.getOwnPropertyDescriptor`，用于得到指定属性的描述对象，将来会替代掉后者。

```js
var myObject = {};
Object.defineProperty(myObject, 'hidden', {
  value: true,
  enumerable: false,
});

// 旧写法
var theDescriptor = Object.getOwnPropertyDescriptor(myObject, 'hidden');

// 新写法
var theDescriptor = Reflect.getOwnPropertyDescriptor(myObject, 'hidden');
```

#### Reflect.isExtensible (target)

`Reflect.isExtensible`方法对应`Object.isExtensible`，返回一个布尔值，表示当前对象是否可扩展。

```js
const myObject = {};

// 旧写法
Object.isExtensible(myObject) // true

// 新写法
Reflect.isExtensible(myObject) // true
```

#### Reflect.preventExtensions(target)

`Reflect.preventExtensions`对应`Object.preventExtensions`方法，用于让一个对象变为不可扩展。它返回一个布尔值，表示是否操作成功。

```js
var myObject = {};

// 旧写法
Object.preventExtensions(myObject) // Object {}

// 新写法
Reflect.preventExtensions(myObject) // true
```

#### Reflect.ownKeys (target)

`Reflect.ownKeys`方法用于返回对象的所有属性，基本等同于`Object.getOwnPropertyNames`与`Object.getOwnPropertySymbols`之和。

```js
var myObject = {
  foo: 1,
  bar: 2,
  [Symbol.for('baz')]: 3,
  [Symbol.for('bing')]: 4,
};

// 旧写法
Object.getOwnPropertyNames(myObject)
// ['foo', 'bar']

Object.getOwnPropertySymbols(myObject)
//[Symbol(baz), Symbol(bing)]

// 新写法
Reflect.ownKeys(myObject)
// ['foo', 'bar', Symbol(baz), Symbol(bing)]
```

### 实例：使用 Proxy 实现观察者模式

观察者模式（`Observer mode`）指的是函数自动观察数据对象，一旦对象有变化，函数就会自动执行。

```js
const person = observable({
  name: '张三',
  age: 20
});

function print() {
  console.log(`${person.name}, ${person.age}`)
}

observe(print);
person.name = '李四';
// 输出
// 李四, 20
```

上面代码中，数据对象`person`是观察目标，函数`print`是观察者。一旦数据对象发生变化，`print`就会自动执行。

下面，使用 `Proxy` 写一个观察者模式的最简单实现，即实现`observable`和`observe`这两个函数。思路是`observable`函数返回一个原始对象的 `Proxy` 代理，拦截赋值操作，触发充当观察者的各个函数。

```js
const queuedObservers = new Set();

const observe = fn => queuedObservers.add(fn);
const observable = obj => new Proxy(obj, {set});

function set(target, key, value, receiver) {
  const result = Reflect.set(target, key, value, receiver);
  queuedObservers.forEach(observer => observer());
  return result;
}
```

上面代码中，先定义了一个`Set`集合，所有观察者函数都放进这个集合。然后，`observable`函数返回原始对象的代理，拦截赋值操作。拦截函数`set`之中，会自动执行所有观察者。

## Promise 对象

### Promise 的含义

Promise 是异步编程的一种解决方案，`ES6` 将其写进了语言标准，统一了用法，原生提供了`Promise`对象。

所谓`Promise`，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果。从语法上说，`Promise` 是一个对象，从它可以获取异步操作的消息。`Promise` 提供统一的 `API`，各种异步操作都可以用同样的方法进行处理

`Promise`对象有以下两个特点。

- 对象的状态不受外界影响。`Promise`对象代表一个异步操作，有三种状态：`pending`（进行中）、`fulfilled`（已成功）和`rejected`（已失败）。只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态。

- 一旦状态改变，就不会再变，任何时候都可以得到这个结果, `Promise`对象的状态改变，只有两种可能：从`pending`变为`fulfilled`和从`pending`变为`rejected`

### 基本用法

`ES6` 规定，`Promise`对象是一个构造函数，用来生成`Promise`实例。

下面代码创造了一个`Promise`实例。

```js
const promise = new Promise(function(resolve, reject) {
  // ... some code

  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});
```

`Promise`构造函数接受一个函数作为参数，该函数的两个参数分别是`resolve`和`reject`。

`resolve`函数的作用是，将`Promise`对象的状态从“未完成”变为“成功”（即从 `pending` 变为 `resolved`），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；`reject`函数的作用是，将`Promise`对象的状态从“未完成”变为“失败”（即从 `pending` 变为 `rejected`），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去

`Promise`实例生成以后，可以用`then`方法分别指定`resolved`状态和`rejected`状态的回调函数。

```js
promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
```

下面是一个`Promise`对象的简单例子。

```js
function timeout(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, ms, 'done');
  });
}

timeout(100).then((value) => {
  console.log(value);
});
```

`Promise` 新建后就会立即执行。

```js
let promise = new Promise(function(resolve, reject) {
  console.log('Promise');
  resolve();
});

promise.then(function() {
  console.log('resolved.');
});

console.log('Hi!');

// Promise
// Hi!
// resolved
```

### Promise.prototype.then()

`Promise` 实例具有`then`方法，也就是说，`then`方法是定义在原型对象`Promise.prototype`上的。它的作用是为 `Promise` 实例添加状态改变时的回调函数。前面说过，`then`方法的第一个参数是`resolved`状态的回调函数，第二个参数（可选）是`rejected`状态的回调函数。

`then`方法返回的是一个新的`Promise`实例（注意，不是原来那个`Promise`实例）。因此可以采用链式写法，即`then`方法后面再调用另一个`then`方法。

```js
getJSON("/posts.json").then(function(json) {
  return json.post;
}).then(function(post) {
  // ...
});
```

### Promise.prototype.catch()

`Promise.prototype.catch()`方法是`.then(null, rejection)`或`.then(undefined, rejection)`的别名，用于指定发生错误时的回调函数。

```js
getJSON('/posts.json').then(function(posts) {
  // ...
}).catch(function(error) {
  // 处理 getJSON 和 前一个回调函数运行时发生的错误
  console.log('发生错误！', error);
});
```

`promise`抛出一个错误，就被`catch()`方法指定的回调函数捕获

`Promise` 对象的错误具有“冒泡”性质，会一直向后传递，直到被捕获为止。也就是说，错误总是会被下一个`catch`语句捕获

建议总是使用`catch()`方法，而不使用`then()`方法的第二个参数 `reject`

建议 `Promise` 对象后面要跟`catch()`方法，这样可以处理 `Promise` 内部发生的错误。`catch()`方法返回的还是一个 `Promise` 对象，因此后面还可以接着调用`then()`方法

```js
const someAsyncThing = function() {
  return new Promise(function(resolve, reject) {
    // 下面一行会报错，因为x没有声明
    resolve(x + 2);
  });
};

someAsyncThing()
.catch(function(error) {
  console.log('oh no', error);
})
.then(function() {
  console.log('carry on');
});
// oh no [ReferenceError: x is not defined]
// carry on
```

### Promise.prototype.finally()

`finally()`方法用于指定不管 `Promise` 对象最后状态如何，都会执行的操作。该方法是 `ES2018` 引入标准的。

```js
promise
.then(result => {···})
.catch(error => {···})
.finally(() => {···});
```

`finally`方法的回调函数不接受任何参数，这意味着没有办法知道，前面的 `Promise` 状态到底是`fulfilled`还是`rejected`。这表明，`finally`方法里面的操作，应该是与状态无关的，不依赖于 `Promise` 的执行结果

### Promise.all()

`Promise.all()`方法用于将多个 `Promise` 实例，包装成一个新的 `Promise` 实例。

```js
const p = Promise.all([p1, p2, p3]);
```

`Promise.all()`方法接受一个数组作为参数, 另外，`Promise.all()`方法的参数可以不是数组，但必须具有 `Iterator` 接口，且返回的每个成员都是 `Promise` 实例

```js
// 生成一个Promise对象的数组
const promises = [2, 3, 5, 7, 11, 13].map(function (id) {
  return getJSON('/post/' + id + ".json");
});

Promise.all(promises).then(function (posts) {
  // ...
}).catch(function(reason){
  // ...
});
```

### Promise.race()

`Promise.race()`方法同样是将多个 `Promise` 实例，包装成一个新的 `Promise` 实例。

```js
const p = Promise.race([p1, p2, p3]);
```

上面代码中，只要p1、p2、p3之中有一个实例率先改变状态，p的状态就跟着改变。那个率先改变的 `Promise` 实例的返回值，就传递给`p`的回调函数。

`Promise.race()`方法的参数与`Promise.all()`方法一样，如果不是 `Promise` 实例，就会先调用下面讲到的`Promise.resolve()`方法，将参数转为 `Promise` 实例，再进一步处理。

### Promise.allSettled()

`Promise.allSettled()`方法接受一组 `Promise` 实例作为参数，包装成一个新的 `Promise` 实例。只有等到所有这些参数实例都返回结果，不管是`fulfilled`还是`rejected`，包装实例才会结束。该方法由 `ES2020` 引入。

```js
const promises = [
  fetch('/api-1'),
  fetch('/api-2'),
  fetch('/api-3'),
];

await Promise.allSettled(promises);
removeLoadingIndicator();
```

该方法返回的新的 `Promise` 实例，一旦结束，状态总是`fulfilled`，不会变成`rejected`。状态变成`fulfilled`后，`Promise` 的监听函数接收到的参数是一个数组，每个成员对应一个传入`Promise.allSettled()`的 `Promise` 实例

```js
const resolved = Promise.resolve(42);
const rejected = Promise.reject(-1);

const allSettledPromise = Promise.allSettled([resolved, rejected]);

allSettledPromise.then(function (results) {
  console.log(results);
});
// [
//    { status: 'fulfilled', value: 42 },
//    { status: 'rejected', reason: -1 }
// ]
```

```js
const promises = [ fetch('index.html'), fetch('https://does-not-exist/') ];
const results = await Promise.allSettled(promises);

// 过滤出成功的请求
const successfulPromises = results.filter(p => p.status === 'fulfilled');

// 过滤出失败的请求，并输出原因
const errors = results
  .filter(p => p.status === 'rejected')
  .map(p => p.reason);
```

### Promise.any()

`Promise.any()`方法接受一组 `Promise` 实例作为参数，包装成一个新的 Promise 实例。只要参数实例有一个变成`fulfilled`状态，包装实例就会变成`fulfilled`状态；如果所有参数实例都变成`rejected`状态，包装实例就会变成`rejected`状态。该方法目前是一个第三阶段的提案 。

`Promise.any()`跟`Promise.race()`方法很像，只有一点不同，就是不会因为某个 `Promise` 变成`rejected`状态而结束。

```js
const promises = [
  fetch('/endpoint-a').then(() => 'a'),
  fetch('/endpoint-b').then(() => 'b'),
  fetch('/endpoint-c').then(() => 'c'),
];
try {
  const first = await Promise.any(promises);
  console.log(first);
} catch (error) {
  console.log(error);
}
```

### Promise.resolve()

有时需要将现有对象转为 `Promise` 对象，`Promise.resolve()`方法就起到这个作用。

```js
const jsPromise = Promise.resolve($.ajax('/whatever.json'));
```

`Promise.resolve`方法的参数分成四种情况。

（1）参数是一个 `Promise` 实例

如果参数是 `Promise` 实例，那么`Promise.resolve`将不做任何修改、原封不动地返回这个实例。

（2）参数是一个`thenable`对象

`thenable`对象指的是具有then方法的对象，比如下面这个对象。

```js
let thenable = {
  then: function(resolve, reject) {
    resolve(42);
  }
};
```

`Promise.resolve`方法会将这个对象转为 `Promise` 对象，然后就立即执行`thenable`对象的`then`方法。

```js
let thenable = {
  then: function(resolve, reject) {
    resolve(42);
  }
};

let p1 = Promise.resolve(thenable);
p1.then(function(value) {
  console.log(value);  // 42
});
```

（3）参数不是具有`then`方法的对象，或根本就不是对象

如果参数是一个原始值，或者是一个不具有`then`方法的对象，则`Promise.resolve`方法返回一个新的 `Promise` 对象，状态为`resolved`。

```js
const p = Promise.resolve('Hello');

p.then(function (s){
  console.log(s)
});
// Hello
```

（4）不带有任何参数

`Promise.resolve()`方法允许调用时不带参数，直接返回一个`resolved`状态的 `Promise` 对象。

所以，如果希望得到一个 `Promise` 对象，比较方便的方法就是直接调用`Promise.resolve()`方法。

```js
const p = Promise.resolve();

p.then(function () {
  // ...
});
```

#### Promise.reject()

`Promise.reject(reason)`方法也会返回一个新的 `Promise` 实例，该实例的状态为`rejected`。

```js
const p = Promise.reject('出错了');
// 等同于
const p = new Promise((resolve, reject) => reject('出错了'))

p.then(null, function (s) {
  console.log(s)
});
// 出错了
```

### 应用

#### 加载图片

我们可以将图片的加载写成一个`Promise`，一旦加载完成，`Promise`的状态就发生变化。

```js
const preloadImage = function (path) {
  return new Promise(function (resolve, reject) {
    const image = new Image();
    image.onload  = resolve;
    image.onerror = reject;
    image.src = path;
  });
};
```

#### Generator 函数与 Promise 的结合

使用 `Generator` 函数管理流程，遇到异步操作的时候，通常返回一个`Promise`对象。

```js
function getFoo () {
  return new Promise(function (resolve, reject){
    resolve('foo');
  });
}

const g = function* () {
  try {
    const foo = yield getFoo();
    console.log(foo);
  } catch (e) {
    console.log(e);
  }
};

function run (generator) {
  const it = generator();

  function go(result) {
    if (result.done) return result.value;

    return result.value.then(function (value) {
      return go(it.next(value));
    }, function (error) {
      return go(it.throw(error));
    });
  }

  go(it.next());
}

run(g);
```

上面代码的 `Generator` 函数`g`之中，有一个异步操作`getFoo`，它返回的就是一个`Promise`对象。函数`run`用来处理这个`Promise`对象，并调用下一个`next`方法

## Iterator 和 for...of 循环

### Iterator（遍历器）的概念

`JavaScript` 原有的表示“集合”的数据结构，主要是数组（`Array`）和对象（`Object`），`ES6` 又添加了`Map`和`Set`。这样就有了四种数据集合，用户还可以组合使用它们，定义自己的数据结构。这样就需要一种统一的接口机制，来处理所有不同的数据结构。

遍历器（`Iterator`）就是这样一种机制。它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 `Iterator` 接口，就可以完成遍历操作（即依次处理该数据结构的所有成员）

`Iterator` 的作用有三个：

- 为各种数据结构，提供一个统一的、简便的访问接口
- 使得数据结构的成员能够按某种次序排列
- `ES6` 创造了一种新的遍历命令`for...of`循环，`Iterator` 接口主要供`for...of`消费

### 默认 Iterator 接口

`Iterator` 接口的目的，就是为所有数据结构，提供了一种统一的访问机制，即`for...of`循环。当使用`for...of`循环遍历某种数据结构时，该循环会自动去寻找 `Iterator` 接口。

一种数据结构只要部署了 `Iterator` 接口，我们就称这种数据结构是“可遍历的”（`iterable`）

`ES6` 规定，默认的 `Iterator` 接口部署在数据结构的`Symbol.iterator`属性，或者说，一个数据结构只要具有`Symbol.iterator`属性，就可以认为是“可遍历的”（`iterable`）

`Symbol.iterator`属性本身是一个函数，就是当前数据结构默认的遍历器生成函数。执行这个函数，就会返回一个遍历器。至于属性名`Symbol.iterator`，它是一个表达式，返回`Symbol`对象的`iterator`属性，这是一个预定义好的、类型为 `Symbol` 的特殊值，所以要放在方括号内

```js
const obj = {
  [Symbol.iterator] : function () {
    return {
      next: function () {
        return {
          value: 1,
          done: true
        };
      }
    };
  }
};
```

`ES6` 的有些数据结构原生具备 `Iterator` 接口（比如数组），即不用任何处理，就可以被`for...of`循环遍历, 另外一些数据结构没有（比如对象）

原生具备 `Iterator` 接口的数据结构如下。

- `Array`
- `Map`
- `Set`
- `String`
- `TypedArray`
- 函数的 `arguments` 对象
- `NodeList` 对象

下面的例子是数组的`Symbol.iterator`属性。

```js
let arr = ['a', 'b', 'c'];
let iter = arr[Symbol.iterator]();

iter.next() // { value: 'a', done: false }
iter.next() // { value: 'b', done: false }
iter.next() // { value: 'c', done: false }
iter.next() // { value: undefined, done: true }
```

一个对象如果要具备可被`for...of`循环调用的 `Iterator` 接口，就必须在`Symbol.iterator`的属性上部署遍历器生成方法

```js
class RangeIterator {
  constructor(start, stop) {
    this.value = start;
    this.stop = stop;
  }

  [Symbol.iterator]() { return this; }

  next() {
    var value = this.value;
    if (value < this.stop) {
      this.value++;
      return {done: false, value: value};
    }
    return {done: true, value: undefined};
  }
}

function range(start, stop) {
  return new RangeIterator(start, stop);
}

for (var value of range(0, 3)) {
  console.log(value); // 0, 1, 2
}
```

### 调用 Iterator 接口的场合

有一些场合会默认调用 `Iterator` 接口（即`Symbol.iterator`方法），除了下文会介绍的for...of循环，还有几个别的场合。

- 解构赋值: 对数组和 `Set` 结构进行解构赋值时，会默认调用`Symbol.iterator`方法。

  ```js
  let set = new Set().add('a').add('b').add('c');

  let [x,y] = set;
  // x='a'; y='b'

  let [first, ...rest] = set;
  // first='a'; rest=['b','c'];
  ```

- 扩展运算符: 扩展运算符（`...`）也会调用默认的 `Iterator` 接口。

  ```js
  // 例一
  var str = 'hello';
  [...str] //  ['h','e','l','l','o']

  // 例二
  let arr = ['b', 'c'];
  ['a', ...arr, 'd']
  // ['a', 'b', 'c', 'd']
  ```

- `yield*`: `yield*`后面跟的是一个可遍历的结构，它会调用该结构的遍历器接口。

  ```js
  let generator = function* () {
    yield 1;
    yield* [2,3,4];
    yield 5;
  };

  var iterator = generator();

  iterator.next() // { value: 1, done: false }
  iterator.next() // { value: 2, done: false }
  iterator.next() // { value: 3, done: false }
  iterator.next() // { value: 4, done: false }
  iterator.next() // { value: 5, done: false }
  iterator.next() // { value: undefined, done: true }
  ```

- 其他场合, 由于数组的遍历会调用遍历器接口，所以任何接受数组作为参数的场合，其实都调用了遍历器接口。下面是一些例子。

  - `for...of`
  - `Array.from()`
  - `Map()`, `Set()`, `WeakMap()`, `WeakSet()`（比如new Map([['a',1],['b',2]])）
  - `Promise.all()`
  - `Promise.race()`

### 字符串的 Iterator 接口

字符串是一个类似数组的对象，也原生具有 `Iterator` 接口。

```js
var someString = "hi";
typeof someString[Symbol.iterator]
// "function"

var iterator = someString[Symbol.iterator]();

iterator.next()  // { value: "h", done: false }
iterator.next()  // { value: "i", done: false }
iterator.next()  // { value: undefined, done: true }
```

可以覆盖原生的`Symbol.iterator`方法，达到修改遍历器行为的目的。

```js
var str = new String("hi");

[...str] // ["h", "i"]

str[Symbol.iterator] = function() {
  return {
    next: function() {
      if (this._first) {
        this._first = false;
        return { value: "bye", done: false };
      } else {
        return { done: true };
      }
    },
    _first: true
  };
};

[...str] // ["bye"]
str // "hi"
```

### Iterator 接口与 Generator 函数

`Symbol.iterator`方法的最简单实现，就是 `Generator` 函数。

```js
let myIterable = {
  [Symbol.iterator]: function* () {
    yield 1;
    yield 2;
    yield 3;
  }
}
[...myIterable] // [1, 2, 3]

// 或者采用下面的简洁写法

let obj = {
  * [Symbol.iterator]() {
    yield 'hello';
    yield 'world';
  }
};

for (let x of obj) {
  console.log(x);
}
// "hello"
// "world"
```

### 遍历器对象的 return()，throw()

遍历器对象除了具有`next`方法，还可以具有`return`方法和`throw`方法。如果你自己写遍历器对象生成函数，那么`next`方法是必须部署的，`return`方法和`throw`方法是否部署是可选的。

如果一个对象在完成遍历前，需要清理或释放资源，就可以部署`return`方法

```js
function readLinesSync(file) {
  return {
    [Symbol.iterator]() {
      return {
        next() {
          return { done: false };
        },
        return() {
          file.close();
          return { done: true };
        }
      };
    },
  };
}
```

### for...of 循环

`ES6` 借鉴 `C++`、`Java`、`C#` 和 `Python` 语言，引入了`for...of`循环，作为遍历所有数据结构的统一的方法。

一个数据结构只要部署了`Symbol.iterator`属性，就被视为具有 `iterator` 接口，就可以用`for...of`循环遍历它的成员。也就是说，`for...of`循环内部调用的是数据结构的`Symbol.iterator`方法。

`for...of`循环可以使用的范围包括数组、`Set` 和 `Map` 结构、某些类似数组的对象（比如`arguments`对象、`DOM` `NodeList` 对象）、后文的 `Generator` 对象，以及字符串。

#### 数组

数组原生具备`iterator`接口（即默认部署了`Symbol.iterator`属性），`for...of`循环本质上就是调用这个接口产生的遍历器，可以用下面的代码证明。

```js
const arr = ['red', 'green', 'blue'];

for(let v of arr) {
  console.log(v); // red green blue
}

const obj = {};
obj[Symbol.iterator] = arr[Symbol.iterator].bind(arr);

for(let v of obj) {
  console.log(v); // red green blue
}
```

`for...of`循环可以代替数组实例的`forEach`方法。

```js
const arr = ['red', 'green', 'blue'];

arr.forEach(function (element, index) {
  console.log(element); // red green blue
  console.log(index);   // 0 1 2
});
```

`JavaScript` 原有的`for...in`循环，只能获得对象的键名，不能直接获取键值。`ES6` 提供`for...of`循环，允许遍历获得键值。

```js
var arr = ['a', 'b', 'c', 'd'];

for (let a in arr) {
  console.log(a); // 0 1 2 3
}

for (let a of arr) {
  console.log(a); // a b c d
}
```

#### Set 和 Map 结构

`Set` 和 `Map` 结构也原生具有 `Iterator` 接口，可以直接使用`for...of`循环。

```js
var engines = new Set(["Gecko", "Trident", "Webkit", "Webkit"]);
for (var e of engines) {
  console.log(e);
}
// Gecko
// Trident
// Webkit

var es6 = new Map();
es6.set("edition", 6);
es6.set("committee", "TC39");
es6.set("standard", "ECMA-262");
for (var [name, value] of es6) {
  console.log(name + ": " + value);
}
// edition: 6
// committee: TC39
// standard: ECMA-262
```

#### 计算生成的数据结构

有些数据结构是在现有数据结构的基础上，计算生成的。比如，`ES6` 的数组、`Set`、`Map` 都部署了以下三个方法，调用后都返回遍历器对象。

- `entries()` 返回一个遍历器对象，用来遍历[键名, 键值]组成的数组。对于数组，键名就是索引值；对于 `Set`，键名与键值相同。`Map` 结构的 `Iterator` 接口，默认就是调用`entries`方法。
- `keys()` 返回一个遍历器对象，用来遍历所有的键名。
- `values()` 返回一个遍历器对象，用来遍历所有的键值。

这三个方法调用后生成的遍历器对象，所遍历的都是计算生成的数据结构。

```js
let arr = ['a', 'b', 'c'];
for (let pair of arr.entries()) {
  console.log(pair);
}
// [0, 'a']
// [1, 'b']
// [2, 'c']
```

#### 类似数组的对象

类似数组的对象包括好几类。下面是`for...of`循环用于字符串、`DOM NodeList` 对象、`arguments`对象的例子。

```js
// 字符串
let str = "hello";

for (let s of str) {
  console.log(s); // h e l l o
}

// DOM NodeList对象
let paras = document.querySelectorAll("p");

for (let p of paras) {
  p.classList.add("test");
}

// arguments对象
function printArgs() {
  for (let x of arguments) {
    console.log(x);
  }
}
printArgs('a', 'b');
// 'a'
// 'b'
```

#### 对象

对于普通的对象，`for...of`结构不能直接使用，会报错，必须部署了 `Iterator` 接口后才能使用。但是，这样情况下，`for...in`循环依然可以用来遍历键名。

```js
let es6 = {
  edition: 6,
  committee: "TC39",
  standard: "ECMA-262"
};

for (let e in es6) {
  console.log(e);
}
// edition
// committee
// standard

for (let e of es6) {
  console.log(e);
}
// TypeError: es6[Symbol.iterator] is not a function
```

要获取对象的属性值，有下面两个方法：

- 使用`Object.keys`方法将对象的键名生成一个数组，然后遍历这个数组。

  ```js
  for (var key of Object.keys(someObject)) {
    console.log(key + ': ' + someObject[key]);
  }
  ```

- 使用 `Generator` 函数将对象重新包装一下。

  ```js
  function* entries(obj) {
    for (let key of Object.keys(obj)) {
      yield [key, obj[key]];
    }
  }

  for (let [key, value] of entries(obj)) {
    console.log(key, '->', value);
  }
  // a -> 1
  // b -> 2
  // c -> 3
  ```

## Generator 函数的语法

### 简介

#### 基本概念

`Generator` 函数是 `ES6` 提供的一种异步编程解决方案，语法行为与传统函数完全不同

语法上，首先可以把它理解成一个状态机，封装了多个内部状态。执行 `Generator` 函数会返回一个遍历器对象，也就是说，`Generator` 函数除了是状态机，还是一个遍历器对象生成函数。返回的遍历器对象，可以依次遍历 `Generator` 函数内部的每一个状态。

形式上，`Generator` 函数是一个普通函数，但是有两个特征。一是，`function`关键字与函数名之间有一个星号；二是，函数体内部使用`yield`表达式，定义不同的内部状态。

```js
function* helloWorldGenerator() {
  yield 'hello';
  yield 'world';
  return 'ending';
}

var hw = helloWorldGenerator();
```

`Generator` 函数是分段执行的，`yield`表达式是暂停执行的标记，而`next`方法可以恢复执行

```js
hw.next()
// { value: 'hello', done: false }

hw.next()
// { value: 'world', done: false }

hw.next()
// { value: 'ending', done: true }

hw.next()
// { value: undefined, done: true }
```

调用 `Generator` 函数，返回一个遍历器对象，代表 `Generator` 函数的内部指针。以后，每次调用遍历器对象的`next`方法，就会返回一个有着`value`和`done`两个属性的对象。`value`属性表示当前的内部状态的值，是`yield`表达式后面那个表达式的值；`done`属性是一个布尔值，表示是否遍历结束

#### yield 表达式

由于 `Generator` 函数返回的遍历器对象，只有调用`next`方法才会遍历下一个内部状态，所以其实提供了一种可以暂停执行的函数。`yield`表达式就是暂停标志

`yield`表达式后面的表达式，只有当调用`next`方法、内部指针指向该语句时才会执行，因此等于为 `JavaScript` 提供了手动的“惰性求值”（`Lazy Evaluation`）的语法功能。

#### 与 Iterator 接口的关系

任意一个对象的`Symbol.iterator`方法，等于该对象的遍历器生成函数，调用该函数会返回该对象的一个遍历器对象。

由于 `Generator` 函数就是遍历器生成函数，因此可以把 `Generator` 赋值给对象的`Symbol.iterator`属性，从而使得该对象具有 `Iterator` 接口。

```js
var myIterable = {};
myIterable[Symbol.iterator] = function* () {
  yield 1;
  yield 2;
  yield 3;
};

[...myIterable] // [1, 2, 3]
```

`Generator` 函数执行后，返回一个遍历器对象。该对象本身也具有`Symbol.iterator`属性，执行后返回自身。

```js
function* gen(){
  // some code
}

var g = gen();

g[Symbol.iterator]() === g
// true
```

### next 方法的参数

`yield`表达式本身没有返回值，或者说总是返回`undefined`。`next`方法可以带一个参数，该参数就会被当作上一个`yield`表达式的返回值。

```js
function* f() {
  for(var i = 0; true; i++) {
    var reset = yield i;
    if(reset) { i = -1; }
  }
}

var g = f();

g.next() // { value: 0, done: false }
g.next() // { value: 1, done: false }
g.next(true) // { value: 0, done: false }
```

通过`next`方法的参数，就可以在 `Generator` 函数开始运行之后，向函数体内部注入值。也就是说，可以在 `Generator` 函数运行的不同阶段，从外部向内部注入不同的值，从而调整函数行为

### for...of 循环

`for...of`循环可以自动遍历 `Generator` 函数运行时生成的`Iterator`对象，且此时不再需要调用`next`方法。

```js
function* foo() {
  yield 1;
  yield 2;
  yield 3;
  yield 4;
  yield 5;
  return 6;
}

for (let v of foo()) {
  console.log(v);
}
// 1 2 3 4 5
```

下面是一个利用 `Generator` 函数和`for...of`循环，实现斐波那契数列的例子。

```js
function* fibonacci() {
  let [prev, curr] = [0, 1];
  for (;;) {
    yield curr;
    [prev, curr] = [curr, prev + curr];
  }
}

for (let n of fibonacci()) {
  if (n > 1000) break;
  console.log(n);
}
```

原生的 `JavaScript` 对象没有遍历接口，无法使用`for...of`循环，通过 `Generator` 函数为它加上这个接口，就可以用了。

```js
function* objectEntries(obj) {
  let propKeys = Reflect.ownKeys(obj);

  for (let propKey of propKeys) {
    yield [propKey, obj[propKey]];
  }
}

let jane = { first: 'Jane', last: 'Doe' };

for (let [key, value] of objectEntries(jane)) {
  console.log(`${key}: ${value}`);
}
// first: Jane
// last: Doe
```

除了`for...of`循环以外，扩展运算符（`...`）、解构赋值和`Array.from`方法内部调用的，都是遍历器接口。这意味着，它们都可以将 `Generator` 函数返回的 `Iterator` 对象，作为参数。

```js
function* numbers () {
  yield 1
  yield 2
  return 3
  yield 4
}

// 扩展运算符
[...numbers()] // [1, 2]

// Array.from 方法
Array.from(numbers()) // [1, 2]

// 解构赋值
let [x, y] = numbers();
x // 1
y // 2

// for...of 循环
for (let n of numbers()) {
  console.log(n)
}
// 1
// 2
```

### Generator.prototype.throw()

`Generator` 函数返回的遍历器对象，都有一个`throw`方法，可以在函数体外抛出错误，然后在 `Generator` 函数体内捕获。

```js
var g = function* () {
  try {
    yield;
  } catch (e) {
    console.log('内部捕获', e);
  }
};

var i = g();
i.next();

try {
  i.throw('a');
  i.throw('b');
} catch (e) {
  console.log('外部捕获', e);
}
// 内部捕获 a
// 外部捕获 b
```

`throw`方法可以接受一个参数，该参数会被`catch`语句接收，建议抛出`Error`对象的实例。

```js
var g = function* () {
  try {
    yield;
  } catch (e) {
    console.log(e);
  }
};

var i = g();
i.next();
i.throw(new Error('出错了！'));
// Error: 出错了！(…)
```

### Generator.prototype.return()

`Generator` 函数返回的遍历器对象，还有一个`return`方法，可以返回给定的值，并且终结遍历 `Generator` 函数。

```js
function* gen() {
  yield 1;
  yield 2;
  yield 3;
}

var g = gen();

g.next()        // { value: 1, done: false }
g.return('foo') // { value: "foo", done: true }
g.next()        // { value: undefined, done: true }
```

### next()、throw()、return() 的共同点

`next()`、`throw()`、`return()`这三个方法本质上是同一件事，可以放在一起理解。它们的作用都是让 `Generator` 函数恢复执行，并且使用不同的语句替换`yield`表达式。

`next()`是将`yield`表达式替换成一个值。

```js
const g = function* (x, y) {
  let result = yield x + y;
  return result;
};

const gen = g(1, 2);
gen.next(); // Object {value: 3, done: false}

gen.next(1); // Object {value: 1, done: true}
// 相当于将 let result = yield x + y
// 替换成 let result = 1;
```

### yield* 表达式

如果在 `Generator` 函数内部，调用另一个 `Generator` 函数。需要在前者的函数体内部，自己手动完成遍历。

```js
function* foo() {
  yield 'a';
  yield 'b';
}

function* bar() {
  yield 'x';
  // 手动遍历 foo()
  for (let i of foo()) {
    console.log(i);
  }
  yield 'y';
}

for (let v of bar()){
  console.log(v);
}
// x
// a
// b
// y
```

如果有多个 `Generator` 函数嵌套，写起来就非常麻烦。`ES6` 提供了`yield*`表达式，作为解决办法，用来在一个 `Generator` 函数里面执行另一个 `Generator` 函数

```js
function* bar() {
  yield 'x';
  yield* foo();
  yield 'y';
}

// 等同于
function* bar() {
  yield 'x';
  yield 'a';
  yield 'b';
  yield 'y';
}

// 等同于
function* bar() {
  yield 'x';
  for (let v of foo()) {
    yield v;
  }
  yield 'y';
}

for (let v of bar()){
  console.log(v);
}
// "x"
// "a"
// "b"
// "y"
```

从语法角度看，如果`yield`表达式后面跟的是一个遍历器对象，需要在`yield`表达式后面加上星号，表明它返回的是一个遍历器对象。这被称为`yield*`表达式

## Generator 函数的异步应用

### 传统方法

`ES6` 诞生以前，异步编程的方法，大概有下面四种。

- 回调函数
- 事件监听
- 发布/订阅
- `Promise` 对象

`Generator` 函数将 `JavaScript` 异步编程带入了一个全新的阶段

### 基本概念

#### 异步

所谓"异步"，简单说就是一个任务不是连续完成的，可以理解成该任务被人为分成两段，先执行第一段，然后转而执行其他任务，等做好了准备，再回过头执行第二段。

比如，有一个任务是读取文件进行处理，任务的第一段是向操作系统发出请求，要求读取文件。然后，程序执行其他任务，等到操作系统返回文件，再接着执行任务的第二段（处理文件）。这种不连续的执行，就叫做异步。

相应地，连续的执行就叫做同步。由于是连续执行，不能插入其他任务，所以操作系统从硬盘读取文件的这段时间，程序只能干等着。

#### 回调函数

`JavaScript` 语言对异步编程的实现，就是回调函数。所谓回调函数，就是把任务的第二段单独写在一个函数里面，等到重新执行这个任务的时候，就直接调用这个函数。回调函数的英语名字`callback`，直译过来就是"重新调用"。

读取文件进行处理，是这样写的。

```js
fs.readFile('/etc/passwd', 'utf-8', function (err, data) {
  if (err) throw err;
  console.log(data);
});
```

#### Promise

回调函数的方式会造成回调函数地狱问题，`Promise` 对象就是为了解决这个问题而提出的。它不是新的语法功能，而是一种新的写法，允许将回调函数的嵌套，改成链式调用。采用 `Promise`，连续读取多个文件，写法如下。

```js
var readFile = require('fs-readfile-promise');

readFile(fileA)
.then(function (data) {
  console.log(data.toString());
})
.then(function () {
  return readFile(fileB);
})
.then(function (data) {
  console.log(data.toString());
})
.catch(function (err) {
  console.log(err);
});
```

`Promise` 提供`then`方法加载回调函数，`catch`方法捕捉执行过程中抛出的错误

### Generator 函数

#### 协程

传统的编程语言，早有异步编程的解决方案（其实是多任务的解决方案）。其中有一种叫做"协程"（`coroutine`），意思是多个线程互相协作，完成异步任务

```js
function* asyncJob() {
  // ...其他代码
  var f = yield readFile(fileA);
  // ...其他代码
}
```

`asyncJob`是一个协程，它的奥妙就在其中的`yield`命令。它表示执行到此处，执行权将交给其他协程。也就是说，`yield`命令是异步两个阶段的分界线。

#### 协程的 Generator 函数实现

`Generator` 函数是协程在 `ES6` 的实现，最大特点就是可以交出函数的执行权（即暂停执行）。

整个 `Generator` 函数就是一个封装的异步任务，或者说是异步任务的容器。异步操作需要暂停的地方，都用`yield`语句注明。`Generator` 函数的执行方法如下

```js
function* gen(x) {
  var y = yield x + 2;
  return y;
}

var g = gen(1);
g.next() // { value: 3, done: false }
g.next() // { value: undefined, done: true }
```

#### Generator 函数的数据交换和错误处理

`Generator` 函数可以暂停执行和恢复执行，这是它能封装异步任务的根本原因。除此之外，它还有两个特性，使它可以作为异步编程的完整解决方案：函数体内外的数据交换和错误处理机制。

`next`返回值的 `value` 属性，是 `Generator` 函数向外输出数据；`next`方法还可以接受参数，向 `Generator` 函数体内输入数据。

```js
function* gen(x){
  var y = yield x + 2;
  return y;
}

var g = gen(1);
g.next() // { value: 3, done: false }
g.next(2) // { value: 2, done: true }
```

`Generator` 函数内部还可以部署错误处理代码，捕获函数体外抛出的错误。

```js
function* gen(x){
  try {
    var y = yield x + 2;
  } catch (e){
    console.log(e);
  }
  return y;
}

var g = gen(1);
g.next();
g.throw('出错了');
// 出错了
```

#### 异步任务的封装

下面看看如何使用 `Generator` 函数，执行一个真实的异步任务。

```js
var fetch = require('node-fetch');

function* gen(){
  var url = 'https://api.github.com/users/github';
  var result = yield fetch(url);
  console.log(result.bio);
}
```

执行这段代码的方法如下。

```js
var g = gen();
var result = g.next();

result.value.then(function(data){
  return data.json();
}).then(function(data){
  g.next(data);
});
```

### Thunk 函数

`Thunk` 函数是自动执行 `Generator` 函数的一种方法。

#### 参数的求值策略

参数的求值策略有两种，传值调用和传名调用，传值调用比较简单，但是对参数求值的时候，实际上还没用到这个参数，有可能造成性能损失

#### Thunk 函数的含义

编译器的“传名调用”实现，往往是将参数放到一个临时函数之中，再将这个临时函数传入函数体。这个临时函数就叫做 `Thunk` 函数。

```js
function f(m) {
  return m * 2;
}

f(x + 5);

// 等同于

var thunk = function () {
  return x + 5;
};

function f(thunk) {
  return thunk() * 2;
}
```

`Thunk` 函数的定义，就是“传名调用”的一种实现策略，用来替换某个表达式。

#### JavaScript 语言的 Thunk 函数

`JavaScript` 语言是传值调用，它的 `Thunk` 函数含义有所不同。在 `JavaScript` 语言中，`Thunk` 函数替换的不是表达式，而是多参数函数，将其替换成一个只接受回调函数作为参数的单参数函数。

```js
// 正常版本的readFile（多参数版本）
fs.readFile(fileName, callback);

// Thunk版本的readFile（单参数版本）
var Thunk = function (fileName) {
  return function (callback) {
    return fs.readFile(fileName, callback);
  };
};

var readFileThunk = Thunk(fileName);
readFileThunk(callback);
```

#### Generator 函数的流程管理

`ES6` 有了 `Generator` 函数，`Thunk` 函数现在可以用于 `Generator` 函数的自动流程管理。

`Generator` 函数可以自动执行。

```js
function* gen() {
  // ...
}

var g = gen();
var res = g.next();

while(!res.done){
  console.log(res.value);
  res = g.next();
}
```

#### Thunk 函数的自动流程管理

`Thunk` 函数真正的威力，在于可以自动执行 `Generator` 函数。下面就是一个基于 `Thunk` 函数的 `Generator` 执行器。

```js
function run(fn) {
  var gen = fn();

  function next(err, data) {
    var result = gen.next(data);
    if (result.done) return;
    result.value(next);
  }

  next();
}

function* g() {
  // ...
}

run(g);
```

### co 模块

#### 基本用法

`co` 模块是著名程序员 `TJ Holowaychuk` 于 2013 年 6 月发布的一个小工具，用于 `Generator` 函数的自动执行。

下面是一个 `Generator` 函数，用于依次读取两个文件。

```js
var gen = function* () {
  var f1 = yield readFile('/etc/fstab');
  var f2 = yield readFile('/etc/shells');
  console.log(f1.toString());
  console.log(f2.toString());
};
```

co 模块可以让你不用编写 `Generator` 函数的执行器。

```js
var co = require('co');
co(gen);
```

`co`函数返回一个`Promise`对象，因此可以用`then`方法添加回调函数。

```js
co(gen).then(function (){
  console.log('Generator 函数执行完成');
});
```

## async 函数

### 含义

`ES2017` 标准引入了 `async` 函数，使得异步操作变得更加方便, 它就是 `Generator` 函数的语法糖。

前文有一个 Generator 函数，依次读取两个文件。

```js
const asyncReadFile = async function () {
  const f1 = await readFile('/etc/fstab');
  const f2 = await readFile('/etc/shells');
  console.log(f1.toString());
  console.log(f2.toString());
};
```

`async`函数对 `Generator` 函数的改进，体现在以下四点。

（1）内置执行器。`Generator` 函数的执行必须靠执行器，所以才有了co模块，而async函数自带执行器

（2）更好的语义。`async`和`await`，比起星号和`yield`，语义更清楚了。`async`表示函数里有异步操作，`await`表示紧跟在后面的表达式需要等待结果

（3）更广的适用性。`co`模块约定，`yield`命令后面只能是 `Thunk` 函数或 `Promise` 对象，而`async`函数的`await`命令后面，可以是 `Promise` 对象和原始类型的值（数值、字符串和布尔值，但这时会自动转成立即 `resolved` 的 `Promise` 对象）

（4）返回值是 `Promise`。`async`函数的返回值是 `Promise` 对象，这比 `Generator` 函数的返回值是 `Iterator` 对象方便多了。你可以用`then`方法指定下一步的操

### 基本用法

`async`函数返回一个 `Promise` 对象，可以使用`then`方法添加回调函数。当函数执行的时候，一旦遇到`await`就会先返回，等到异步操作完成，再接着执行函数体内后面的语句

```js
async function getStockPriceByName(name) {
  const symbol = await getStockSymbol(name);
  const stockPrice = await getStockPrice(symbol);
  return stockPrice;
}

getStockPriceByName('goog').then(function (result) {
  console.log(result);
});
```

`async` 函数有多种使用形式。

```js
// 函数声明
async function foo() {}

// 函数表达式
const foo = async function () {};

// 对象的方法
let obj = { async foo() {} };
obj.foo().then(...)

// Class 的方法
class Storage {
  constructor() {
    this.cachePromise = caches.open('avatars');
  }

  async getAvatar(name) {
    const cache = await this.cachePromise;
    return cache.match(`/avatars/${name}.jpg`);
  }
}

const storage = new Storage();
storage.getAvatar('jake').then(…);

// 箭头函数
const foo = async () => {};
```

### 语法

`async`函数的语法规则总体上比较简单，难点是错误处理机制。

#### 返回 Promise 对象

`async`函数返回一个 `Promise` 对象。

`async`函数内部`return`语句返回的值，会成为`then`方法回调函数的参数。

```js
async function f() {
  return 'hello world';
}

f().then(v => console.log(v))
// "hello world"
```

`async`函数内部抛出错误，会导致返回的 `Promise` 对象变为`reject`状态。抛出的错误对象会被`catch`方法回调函数接收到。

```js
async function f() {
  throw new Error('出错了');
}

f().then(
  v => console.log(v),
  e => console.log(e)
)
// Error: 出错了
```

#### Promise 对象的状态变化

`async`函数返回的 `Promise` 对象，必须等到内部所有`await`命令后面的 `Promise` 对象执行完，才会发生状态改变，除非遇到`return`语句或者抛出错误。也就是说，只有`async`函数内部的异步操作执行完，才会执行`then`方法指定的回调函数

```js
async function getTitle(url) {
  let response = await fetch(url);
  let html = await response.text();
  return html.match(/<title>([\s\S]+)<\/title>/i)[1];
}
getTitle('https://tc39.github.io/ecma262/').then(console.log)
// "ECMAScript 2017 Language Specification"
```

#### await 命令

正常情况下，`await`命令后面是一个 `Promise` 对象，返回该对象的结果。如果不是 `Promise` 对象，就直接返回对应的值。

```js
async function f() {
  // 等同于
  // return 123;
  return await 123;
}

f().then(v => console.log(v))
// 123
```

另一种情况是，`await`命令后面是一个`thenable`对象（即定义了`then`方法的对象），那么`await`会将其等同于 `Promise` 对象。

```js
class Sleep {
  constructor(timeout) {
    this.timeout = timeout;
  }
  then(resolve, reject) {
    const startTime = Date.now();
    setTimeout(
      () => resolve(Date.now() - startTime),
      this.timeout
    );
  }
}

(async () => {
  const sleepTime = await new Sleep(1000);
  console.log(sleepTime);
})();
// 1000
```

#### 错误处理

如果`await`后面的异步操作出错，那么等同于`async`函数返回的 `Promis`e 对象被`reject`。

```js
async function f() {
  await new Promise(function (resolve, reject) {
    throw new Error('出错了');
  });
}

f()
.then(v => console.log(v))
.catch(e => console.log(e))
// Error：出错了
```

止出错的方法，也是将其放在`try...catch`代码块之中。

```js
async function f() {
  try {
    await new Promise(function (resolve, reject) {
      throw new Error('出错了');
    });
  } catch(e) {
  }
  return await('hello world');
}
```

## Class 的基本语法

### 简介

#### 类的由来

`JavaScript` 语言中，生成实例对象的传统方法是通过构造函数。下面是一个例子。

```js
function Point(x, y) {
  this.x = x;
  this.y = y;
}

Point.prototype.toString = function () {
  return '(' + this.x + ', ' + this.y + ')';
};

var p = new Point(1, 2);
```

`ES6` 引入了 `Class`（类）这个概念，作为对象的模板。通过`class`关键字，可以定义类。

基本上，`ES6` 的`class`可以看作只是一个语法糖，它的绝大部分功能，`ES5` 都可以做到，新的`class`写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。上面的代码用 `ES6` 的`class`改写，就是下面这样。

```js
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}
```

`ES6` 的类，完全可以看作构造函数的另一种写法。

```js
class Point {
  // ...
}

typeof Point // "function"
Point === Point.prototype.constructor // true
```

类的数据类型就是函数，类本身就指向构造函数。

使用的时候，也是直接对类使用`new`命令，跟构造函数的用法完全一致。

```js
class Bar {
  doStuff() {
    console.log('stuff');
  }
}

var b = new Bar();
b.doStuff() // "stuff"
```

#### constructor 方法

`constructor`方法是类的默认方法，通过`new`命令生成对象实例时，自动调用该方法。一个类必须有`constructor`方法，如果没有显式定义，一个空的`constructor`方法会被默认添加。

```js
class Point {
}

// 等同于
class Point {
  constructor() {}
}
```

`constructor`方法默认返回实例对象（即`this`），完全可以指定返回另外一个对象。

```js
class Foo {
  constructor() {
    return Object.create(null);
  }
}

new Foo() instanceof Foo
// false
```

#### 类的实例

生成类的实例的写法，与 `ES5` 完全一样，也是使用`new`命令

```js
class Point {
  // ...
}

// 报错
var point = Point(2, 3);

// 正确
var point = new Point(2, 3);
```

实例的属性除非显式定义在其本身（即定义在`this`对象上），否则都是定义在原型上（即定义在`class`上）

```js
//定义类
class Point {

  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }

}

var point = new Point(2, 3);

point.toString() // (2, 3)

point.hasOwnProperty('x') // true
point.hasOwnProperty('y') // true
point.hasOwnProperty('toString') // false
point.__proto__.hasOwnProperty('toString') // true
```

#### 取值函数（getter）和存值函数（setter）

与 `ES5` 一样，在“类”的内部可以使用`get`和`set`关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为。

```js
class MyClass {
  constructor() {
    // ...
  }
  get prop() {
    return 'getter';
  }
  set prop(value) {
    console.log('setter: '+value);
  }
}

let inst = new MyClass();

inst.prop = 123;
// setter: 123

inst.prop
// 'getter'
```

#### 属性表达式

类的属性名，可以采用表达式。

```js
let methodName = 'getArea';

class Square {
  constructor(length) {
    // ...
  }

  [methodName]() {
    // ...
  }
}
```

#### Class 表达式

与函数一样，类也可以使用表达式的形式定义。

```js
const MyClass = class Me {
  getClassName() {
    return Me.name;
  }
};
```

#### 注意点

（1）严格模式

类和模块的内部，默认就是严格模式，所以不需要使用`use strict`指定运行模式。

（2）不存在提升, 类不存在变量提升（`hoist`），这一点与 `ES5` 完全不同。

```js
new Foo(); // ReferenceError
class Foo {}
```

（3）name 属性, 由于本质上，`ES6` 的类只是 `ES5` 的构造函数的一层包装，所以函数的许多特性都被`Class`继承，包括`name`属性。

```js
class Point {}
Point.name // "Point"
```

（4）`Generator` 方法, 如果某个方法之前加上星号（`*`）`，就表示该方法是一个 `Generator` 函数。

```js
class Foo {
  constructor(...args) {
    this.args = args;
  }
  * [Symbol.iterator]() {
    for (let arg of this.args) {
      yield arg;
    }
  }
}

for (let x of new Foo('hello', 'world')) {
  console.log(x);
}
// hello
// world
```

（5）`this` 的指向, 类的方法内部如果含有`this`，它默认指向类的实例

```js
class Logger {
  printName(name = 'there') {
    this.print(`Hello ${name}`);
  }

  print(text) {
    console.log(text);
  }
}

const logger = new Logger();
const { printName } = logger;
printName(); // TypeError: Cannot read property 'print' of undefined
```

### 静态方法

类相当于实例的原型，所有在类中定义的方法，都会被实例继承。如果在一个方法前，加上`static`关键字，就表示该方法不会被实例继承，而是直接通过类来调用，这就称为“静态方法”。

```js
class Foo {
  static classMethod() {
    return 'hello';
  }
}

Foo.classMethod() // 'hello'

var foo = new Foo();
foo.classMethod()
// TypeError: foo.classMethod is not a function
```

注意，如果静态方法包含`this`关键字，这个`this`指的是类，而不是实例。

```js
class Foo {
  static bar() {
    this.baz();
  }
  static baz() {
    console.log('hello');
  }
  baz() {
    console.log('world');
  }
}

Foo.bar() // hello
```

父类的静态方法，可以被子类继承。

```js
class Foo {
  static classMethod() {
    return 'hello';
  }
}

class Bar extends Foo {
}

Bar.classMethod() // 'hello'
```

### 实例属性的新写法

实例属性除了定义在`constructor()`方法里面的`this`上面，也可以定义在类的最顶层。

```js
class IncreasingCounter {
  constructor() {
    this._count = 0;
  }
  get value() {
    console.log('Getting the current value!');
    return this._count;
  }
  increment() {
    this._count++;
  }
}
```

另一种写法是，这个属性也可以定义在类的最顶层，其他都不变。

```js
class IncreasingCounter {
  _count = 0;
  get value() {
    console.log('Getting the current value!');
    return this._count;
  }
  increment() {
    this._count++;
  }
}
```

### 静态属性

静态属性指的是 `Class` 本身的属性，即`Class.propName`，而不是定义在实例对象（`this`）上的属性。

```js
class Foo {
}

Foo.prop = 1;
Foo.prop // 1
```

### 私有方法和私有属性

#### 现有的解决方案

私有方法和私有属性，是只能在类的内部访问的方法和属性，外部不能访问。这是常见需求，有利于代码的封装，但 `ES6` 不提供，只能通过变通方法模拟实现。

一种做法是在命名上加以区别。

```js
class Widget {

  // 公有方法
  foo (baz) {
    this._bar(baz);
  }

  // 私有方法
  _bar(baz) {
    return this.snaf = baz;
  }

  // ...
}
```

上面代码中，_bar方法前面的下划线，表示这是一个只限于内部使用的私有方法。但是，这种命名是不保险的

另一种方法就是索性将私有方法移出模块，因为模块内部的所有方法都是对外可见的。

```js
class Widget {
  foo (baz) {
    bar.call(this, baz);
  }

  // ...
}

function bar(baz) {
  return this.snaf = baz;
}
```

还有一种方法是利用`Symbol`值的唯一性，将私有方法的名字命名为一个Symbol值。

```js
const bar = Symbol('bar');
const snaf = Symbol('snaf');

export default class myClass{

  // 公有方法
  foo(baz) {
    this[bar](baz);
  }

  // 私有方法
  [bar](baz) {
    return this[snaf] = baz;
  }

  // ...
};
```

#### 私有属性的提案

目前，有一个提案，为`class`加了私有属性。方法是在属性名之前，使用`#`表示。

```js
class IncreasingCounter {
  #count = 0;
  get value() {
    console.log('Getting the current value!');
    return this.#count;
  }
  increment() {
    this.#count++;
  }
}
```

#### new.target 属性

`new`是从构造函数生成实例对象的命令。`ES6` 为`new`命令引入了一个`new.target`属性，该属性一般用在构造函数之中，返回`new`命令作用于的那个构造函数。

如果构造函数不是通过`new`命令或`Reflect.construct()`调用的，`new.target`会返回`undefined`，因此这个属性可以用来确定构造函数是怎么调用的

```js
function Person(name) {
  if (new.target !== undefined) {
    this.name = name;
  } else {
    throw new Error('必须使用 new 命令生成实例');
  }
}

// 另一种写法
function Person(name) {
  if (new.target === Person) {
    this.name = name;
  } else {
    throw new Error('必须使用 new 命令生成实例');
  }
}

var person = new Person('张三'); // 正确
var notAPerson = Person.call(person, '张三');  // 报错
```

## Class 的继承

### 简介

`Class` 可以通过`extends`关键字实现继承，这比 `ES5` 的通过修改原型链实现继承，要清晰和方便很多。

```js
class Point {
}

class ColorPoint extends Point {
}
```

```js
class ColorPoint extends Point {
  constructor(x, y, color) {
    super(x, y); // 调用父类的constructor(x, y)
    this.color = color;
  }

  toString() {
    return this.color + ' ' + super.toString(); // 调用父类的toString()
  }
}
```

`super`关键字表示父类的构造函数，用来新建父类的`this`对象, 在子类的构造函数中，只有调用`super`之后，才可以使用`this`关键字，否则会报错

父类的静态方法，也会被子类继承。

```js
class A {
  static hello() {
    console.log('hello world');
  }
}

class B extends A {
}

B.hello()  // hello world
```

### Object.getPrototypeOf()

`Object.getPrototypeOf`方法可以用来从子类上获取父类。

```js
Object.getPrototypeOf(ColorPoint) === Point
// true
```

因此，可以使用这个方法判断，一个类是否继承了另一个类

### super 关键字

`super`这个关键字，既可以当作函数使用，也可以当作对象使用。在这两种情况下，它的用法完全不同。

第一种情况，`super`作为函数调用时，代表父类的构造函数。`ES6` 要求，子类的构造函数必须执行一次`super`函数。

```js
class A {}

class B extends A {
  constructor() {
    super();
  }
}
```

作为函数时，`super()`只能用在子类的构造函数之中，用在其他地方就会报错。

```js
class A {}

class B extends A {
  m() {
    super(); // 报错
  }
}
```

### 类的 prototype 属性和__proto__属性

大多数浏览器的 `ES5` 实现之中，每一个对象都有`__proto__`属性，指向对应的构造函数的`prototype`属性。`Class` 作为构造函数的语法糖，同时有`prototype`属性和`__proto__`属性，因此同时存在两条继承链。

（1）子类的`__proto__`属性，表示构造函数的继承，总是指向父类。

（2）子类`prototype`属性的`__proto__`属性，表示方法的继承，总是指向父类的`prototype`属性。

```js
class A {
}

class B extends A {
}

B.__proto__ === A // true
B.prototype.__proto__ === A.prototype // true
```

### 原生构造函数的继承

原生构造函数是指语言内置的构造函数，通常用来生成数据结构。`ECMAScript` 的原生构造函数大致有下面这些。

- `Boolean()`
- `Number()`
- `String()`
- `Array()`
- `Date()`
- `Function()`
- `RegExp()`
- `Error()`
- `Object()`

`ES6` 允许继承原生构造函数定义子类，因为 `ES6` 是先新建父类的实例对象`this`，然后再用子类的构造函数修饰`this`，使得父类的所有行为都可以继承。下面是一个继承`Array`的例子。

```js
class MyArray extends Array {
  constructor(...args) {
    super(...args);
  }
}

var arr = new MyArray();
arr[0] = 12;
arr.length // 1

arr.length = 0;
arr[0] // undefined
```

### Mixin 模式的实现

`Mixin` 指的是多个对象合成一个新的对象，新对象具有各个组成成员的接口。它的最简单实现如下。

```js
const a = {
  a: 'a'
};
const b = {
  b: 'b'
};
const c = {...a, ...b}; // {a: 'a', b: 'b'}
```

下面是一个更完备的实现，将多个类的接口“混入”（`mix in`）另一个类。

```js
function mix(...mixins) {
  class Mix {
    constructor() {
      for (let mixin of mixins) {
        copyProperties(this, new mixin()); // 拷贝实例属性
      }
    }
  }

  for (let mixin of mixins) {
    copyProperties(Mix, mixin); // 拷贝静态属性
    copyProperties(Mix.prototype, mixin.prototype); // 拷贝原型属性
  }

  return Mix;
}

function copyProperties(target, source) {
  for (let key of Reflect.ownKeys(source)) {
    if ( key !== 'constructor'
      && key !== 'prototype'
      && key !== 'name'
    ) {
      let desc = Object.getOwnPropertyDescriptor(source, key);
      Object.defineProperty(target, key, desc);
    }
  }
}
```

## Module 的语法

### 概述

历史上，`JavaScript` 一直没有模块（module）体系，无法将一个大程序拆分成互相依赖的小文件, 在 `ES6` 之前，社区制定了一些模块加载方案，最主要的有 `CommonJS` 和 `AMD` 两种。`ES6` 在语言标准的层面上，实现了模块功能, 成为浏览器和服务器通用的模块解决方案。

`ES6` 模块的设计思想是尽量的静态化，使得编译时就能确定模块的依赖关系，以及输入和输出的变量。

`ES6` 模块不是对象，而是通过`export`命令显式指定输出的代码，再通过`import`命令输入。

```js
// ES6模块
import { stat, exists, readFile } from 'fs';
```

### 严格模式

`ES6` 的模块自动采用严格模式，不管你有没有在模块头部加上"use strict";。

严格模式主要有以下限制。

- 变量必须声明后再使用
- 函数的参数不能有同名属性，否则报错
- 不能使用`with`语句
- 不能对只读属性赋值，否则报错
- 不能使用前缀 `0` 表示八进制数，否则报错
- 不能删除不可删除的属性，否则报错
- 不能删除变量`delete prop`，会报错，只能删除属性`delete global[prop]`
- `eval`不会在它的外层作用域引入变量
- `eval`和`arguments`不能被重新赋值
- `arguments`不会自动反映函数参数的变化
- 不能使用`arguments.callee`
- 不能使用`arguments.caller`
- 禁止`this`指向全局对象
- 不能使用`fn.caller`和`fn.arguments`获取函数调用的堆栈
- 增加了保留字（比如`protected`、`static`和`interface`）

### export 命令

模块功能主要由两个命令构成：`export`和`import`。`export`命令用于规定模块的对外接口，`import`命令用于输入其他模块提供的功能。

一个模块就是一个独立的文件。该文件内部的所有变量，外部无法获取。如果你希望外部能够读取模块内部的某个变量，就必须使用`export`关键字输出该变量。下面是一个 `JS` 文件，里面使用`export`命令输出变量。

```js
// profile.js
export var firstName = 'Michael';
export var lastName = 'Jackson';
export var year = 1958;
```

`export`的写法，除了像上面这样，还有另外一种。

```js
// profile.js
var firstName = 'Michael';
var lastName = 'Jackson';
var year = 1958;

export { firstName, lastName, year };
```

### import 命令

使用`export`命令定义了模块的对外接口以后，其他 `JS` 文件就可以通过`import`命令加载这个模块。

```js
// main.js
import { firstName, lastName, year } from './profile.js';

function setName(element) {
  element.textContent = firstName + ' ' + lastName;
}
```

如果想为输入的变量重新取一个名字，`import`命令要使用`as`关键字，将输入的变量重命名。

```js
import { lastName as surname } from './profile.js';
```

### 模块的整体加载

除了指定加载某个输出值，还可以使用整体加载，即用星号（`*`）指定一个对象，所有输出值都加载在这个对象上面。

```js
import * as circle from './circle';

console.log('圆面积：' + circle.area(4));
console.log('圆周长：' + circle.circumference(14));
```

### export default 命令

`export default`命令，为模块指定默认输出。

```js
// export-default.js
export default function () {
  console.log('foo');
}
```

### import()

`ES2020`提案 引入`import()`函数，支持动态加载模块。

```js
import(specifier)
```

`import()`返回一个 `Promise` 对象。下面是一个例子。

```js
const main = document.querySelector('main');

import(`./section-modules/${someVariable}.js`)
  .then(module => {
    module.loadPageInto(main);
  })
  .catch(err => {
    main.textContent = err.message;
  });
```

## 编程风格

### 块级作用域

#### let 取代 var

`ES6` 提出了两个新的声明变量的命令：`let`和`const`。其中，`let`完全可以取代`var`，因为两者语义相同，而且`let`没有副作用。

```js
'use strict';

if (true) {
  let x = 'hello';
}

for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

`var`命令存在变量提升效用，`let`命令没有这个问题。

```js
'use strict';

if (true) {
  console.log(x); // ReferenceError
  let x = 'hello';
}
```

所以，建议不再使用`var`命令，而是使用`let`命令取代。

#### 全局常量和线程安全

在`let`和`const`之间，建议优先使用`const`，尤其是在全局环境，不应该设置变量，只应设置常量

```js
// bad
var a = 1, b = 2, c = 3;

// good
const a = 1;
const b = 2;
const c = 3;

// best
const [a, b, c] = [1, 2, 3];
```

### 字符串

静态字符串一律使用单引号或反引号，不使用双引号。动态字符串使用反引号。

```js
// bad
const a = "foobar";
const b = 'foo' + a + 'bar';

// acceptable
const c = `foobar`;

// good
const a = 'foobar';
const b = `foo${a}bar`;
```

### 解构赋值

使用数组成员对变量赋值时，优先使用解构赋值。

```js
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```

函数的参数如果是对象的成员，优先使用解构赋值。

```js
// bad
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;
}

// good
function getFullName(obj) {
  const { firstName, lastName } = obj;
}

// best
function getFullName({ firstName, lastName }) {
}
```

如果函数返回多个值，优先使用对象的解构赋值，而不是数组的解构赋值。这样便于以后添加返回值，以及更改返回值的顺序。

```js
// bad
function processInput(input) {
  return [left, right, top, bottom];
}

// good
function processInput(input) {
  return { left, right, top, bottom };
}

const { left, right } = processInput(input);
```

### 对象

单行定义的对象，最后一个成员不以逗号结尾。多行定义的对象，最后一个成员以逗号结尾。

```js
// bad
const a = { k1: v1, k2: v2, };
const b = {
  k1: v1,
  k2: v2
};

// good
const a = { k1: v1, k2: v2 };
const b = {
  k1: v1,
  k2: v2,
};
```

对象尽量静态化，一旦定义，就不得随意添加新的属性。如果添加属性不可避免，要使用`Object.assign`方法。

```js
// bad
const a = {};
a.x = 3;

// if reshape unavoidable
const a = {};
Object.assign(a, { x: 3 });

// good
const a = { x: null };
a.x = 3;
```

如果对象的属性名是动态的，可以在创造对象的时候，使用属性表达式定义。

```js
// bad
const obj = {
  id: 5,
  name: 'San Francisco',
};
obj[getKey('enabled')] = true;

// good
const obj = {
  id: 5,
  name: 'San Francisco',
  [getKey('enabled')]: true,
};
```

另外，对象的属性和方法，尽量采用简洁表达法，这样易于描述和书写。

```js
var ref = 'some value';

// bad
const atom = {
  ref: ref,

  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  ref,

  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```

### 数组

使用扩展运算符（`...`）拷贝数组。

```js
// bad
const len = items.length;
const itemsCopy = [];
let i;

for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```

使用 `Array.from` 方法，将类似数组的对象转为数组。

```js
const foo = document.querySelectorAll('.foo');
const nodes = Array.from(foo);
```

### 函数

立即执行函数可以写成箭头函数的形式。

```js
(() => {
  console.log('Welcome to the Internet.');
})();
```

那些使用匿名函数当作参数的场合，尽量用箭头函数代替。因为这样更简洁，而且绑定了 `this`。

```js
// bad
[1, 2, 3].map(function (x) {
  return x * x;
});

// good
[1, 2, 3].map((x) => {
  return x * x;
});

// best
[1, 2, 3].map(x => x * x);
```

箭头函数取代`Function.prototype.bind`，不应再用 `self/_this/that` 绑定 `this`。

```js
// bad
const self = this;
const boundMethod = function(...params) {
  return method.apply(self, params);
}

// acceptable
const boundMethod = method.bind(this);

// best
const boundMethod = (...params) => method.apply(this, params);
```

简单的、单行的、不会复用的函数，建议采用箭头函数。如果函数体较为复杂，行数较多，还是应该采用传统的函数写法。

所有配置项都应该集中在一个对象，放在最后一个参数，布尔值不可以直接作为参数。

```js
// bad
function divide(a, b, option = false ) {
}

// good
function divide(a, b, { option = false } = {}) {
}
```

不要在函数体内使用 `arguments` 变量，使用 `rest` 运算符（`...`）代替。因为 `rest` 运算符显式表明你想要获取参数，而且 `arguments` 是一个类似数组的对象，而 `rest` 运算符可以提供一个真正的数组。

```js
// bad
function concatenateAll() {
  const args = Array.prototype.slice.call(arguments);
  return args.join('');
}

// good
function concatenateAll(...args) {
  return args.join('');
}
```

使用默认值语法设置函数参数的默认值。

```js
// bad
function handleThings(opts) {
  opts = opts || {};
}

// good
function handleThings(opts = {}) {
  // ...
}
```

### Map 结构

注意区分 `Object` 和 `Map`，只有模拟现实世界的实体对象时，才使用 `Object`。如果只是需要`key: value`的数据结构，使用 `Map` 结构。因为 `Map` 有内建的遍历机制。

```js
let map = new Map(arr);

for (let key of map.keys()) {
  console.log(key);
}

for (let value of map.values()) {
  console.log(value);
}

for (let item of map.entries()) {
  console.log(item[0], item[1]);
}
```

### Class

总是用 `Class`，取代需要 `prototype` 的操作。因为 `Class` 的写法更简洁，更易于理解。

```js
// bad
function Queue(contents = []) {
  this._queue = [...contents];
}
Queue.prototype.pop = function() {
  const value = this._queue[0];
  this._queue.splice(0, 1);
  return value;
}

// good
class Queue {
  constructor(contents = []) {
    this._queue = [...contents];
  }
  pop() {
    const value = this._queue[0];
    this._queue.splice(0, 1);
    return value;
  }
}
```

使用`extends`实现继承，因为这样更简单，不会有破坏`instanceof`运算的危险。

```js
// bad
const inherits = require('inherits');
function PeekableQueue(contents) {
  Queue.apply(this, contents);
}
inherits(PeekableQueue, Queue);
PeekableQueue.prototype.peek = function() {
  return this._queue[0];
}

// good
class PeekableQueue extends Queue {
  peek() {
    return this._queue[0];
  }
}
```

### 模块

首先，`Module` 语法是 `JavaScript` 模块的标准写法，坚持使用这种写法。使用`import`取代`require`。

```js
// bad
const moduleA = require('moduleA');
const func1 = moduleA.func1;
const func2 = moduleA.func2;

// good
import { func1, func2 } from 'moduleA';
```

使用`export`取代`module.exports`。

```js
// commonJS的写法
var React = require('react');

var Breadcrumbs = React.createClass({
  render() {
    return <nav />;
  }
});

module.exports = Breadcrumbs;

// ES6的写法
import React from 'react';

class Breadcrumbs extends React.Component {
  render() {
    return <nav />;
  }
};

export default Breadcrumbs;
```

如果模块只有一个输出值，就使用`export default`，如果模块有多个输出值，就不使用`export default`，`export default`与普通的`export`不要同时使用。

不要在模块输入中使用通配符。因为这样可以确保你的模块之中，有一个默认输出（`export default`）。

```js
// bad
import * as myObject from './importModule';

// good
import myObject from './importModule';
```

如果模块默认输出一个函数，函数名的首字母应该小写。

```js
function makeStyleGuide() {
}

export default makeStyleGuide;
```

如果模块默认输出一个对象，对象名的首字母应该大写。

```js
const StyleGuide = {
  es6: {
  }
};

export default StyleGuide;
```

## 异步遍历器

### 同步遍历器的问题

`Iterator` 接口是一种数据遍历的协议，只要调用遍历器对象的`next`方法，就会得到一个对象，表示当前遍历指针所在的那个位置的信息。`next`方法返回的对象的结构是`{value, done}`，其中value表示当前的数据的值，`done`是一个布尔值，表示遍历是否结束

```js
function idMaker() {
  let index = 0;

  return {
    next: function() {
      return { value: index++, done: false };
    }
  };
}

const it = idMaker();

it.next().value // 0
it.next().value // 1
it.next().value // 2
// ...
```

上面的代码中，`it.next()`方法必须是同步的，只要调用就必须立刻返回值。也就是说，一旦执行`it.next()`方法，就必须同步地得到`value`和`done`这两个属性, 如果`next()`方法返回的是一个 `Promise` 对象，这样就不行，不符合 `Iterator` 协议，只要代码里面包含异步操作都不行。也就是说，`Iterator` 协议里面`next()`方法只能包含同步操作。

目前的解决方法是，将异步操作包装成 `Thunk` 函数或者 `Promise` 对象，即`next()`方法返回值的`value`属性是一个 `Thunk` 函数或者 `Promise` 对象，等待以后返回真正的值，而`done`属性则还是同步产生的

```js
function idMaker() {
  let index = 0;

  return {
    next: function() {
      return {
        value: new Promise(resolve => setTimeout(() => resolve(index++), 1000)),
        done: false
      };
    }
  };
}

const it = idMaker();

it.next().value.then(o => console.log(o)) // 1
it.next().value.then(o => console.log(o)) // 2
it.next().value.then(o => console.log(o)) // 3
// ...
```

但上面的写法太繁琐，为此`ES2018` 引入了“异步遍历器”（`Async Iterator`），为异步操作提供原生的遍历器接口，即`value`和`done`这两个属性都是异步产生

### 异步遍历的接口

异步遍历器的最大的语法特点，就是调用遍历器的`next`方法，返回的是一个 `Promise` 对象。

```js
asyncIterator
  .next()
  .then(
    ({ value, done }) => /* ... */
  );
```

`asyncIterator`是一个异步遍历器，调用`next`方法以后，返回一个 `Promise` 对象。因此，可以使用`then`方法指定，这个 `Promise` 对象的状态变为`resolve`以后的回调函数。回调函数的参数，则是一个具有`value`和`done`两个属性的对象，这个跟同步遍历器是一样的

一个对象的同步遍历器的接口，部署在`Symbol.iterator`属性上面。同样地，对象的异步遍历器接口，部署在`Symbol.asyncIterator`属性上面

```js
const asyncIterable = createAsyncIterable(['a', 'b']);
const asyncIterator = asyncIterable[Symbol.asyncIterator]();

asyncIterator
.next()
.then(iterResult1 => {
  console.log(iterResult1); // { value: 'a', done: false }
  return asyncIterator.next();
})
.then(iterResult2 => {
  console.log(iterResult2); // { value: 'b', done: false }
  return asyncIterator.next();
})
.then(iterResult3 => {
  console.log(iterResult3); // { value: undefined, done: true }
});
```

由于异步遍历器的`next`方法，返回的是一个 `Promise` 对象。因此，可以把它放在`await`命令后面

```js
async function f() {
  const asyncIterable = createAsyncIterable(['a', 'b']);
  const asyncIterator = asyncIterable[Symbol.asyncIterator]();
  console.log(await asyncIterator.next());
  // { value: 'a', done: false }
  console.log(await asyncIterator.next());
  // { value: 'b', done: false }
  console.log(await asyncIterator.next());
  // { value: undefined, done: true }
}
```

### for await...of
前面介绍过，`for...of`循环用于遍历同步的 `Iterator` 接口。新引入的`for await...of`循环，则是用于遍历异步的 `Iterator` 接口。

```js
async function f() {
  for await (const x of createAsyncIterable(['a', 'b'])) {
    console.log(x);
  }
}
// a
// b
```

`for await...of`循环的一个用途，是部署了 `asyncIterable` 操作的异步接口，可以直接放入这个循环。

```js
let body = '';

async function f() {
  for await(const data of req) body += data;
  const parsed = JSON.parse(body);
  console.log('got', parsed);
}
```

注意，`for await...of`循环也可以用于同步遍历器。

```js
(async function () {
  for await (const x of ['a', 'b']) {
    console.log(x);
  }
})();
// a
// b
```

### 异步 Generator 函数

就像 `Generator` 函数返回一个同步遍历器对象一样，异步 `Generator` 函数的作用，是返回一个异步遍历器对象。

在语法上，异步 `Generator` 函数就是`async`函数与 `Generator` 函数的结合。

```js
async function* gen() {
  yield 'hello';
}
const genObj = gen();
genObj.next().then(x => console.log(x));
// { value: 'hello', done: false }
```

异步遍历器的设计目的之一，就是 `Generator` 函数处理同步操作和异步操作时，能够使用同一套接口。

```js
// 同步 Generator 函数
function* map(iterable, func) {
  const iter = iterable[Symbol.iterator]();
  while (true) {
    const {value, done} = iter.next();
    if (done) break;
    yield func(value);
  }
}

// 异步 Generator 函数
async function* map(iterable, func) {
  const iter = iterable[Symbol.asyncIterator]();
  while (true) {
    const {value, done} = await iter.next();
    if (done) break;
    yield func(value);
  }
}
```

### yield* 语句

`yield*`语句也可以跟一个异步遍历器。

```js
async function* gen1() {
  yield 'a';
  yield 'b';
  return 2;
}

async function* gen2() {
  // result 最终会等于 2
  const result = yield* gen1();
}
```

## ArrayBuffer

`ArrayBuffer`对象、`TypedArray`视图和`DataView`视图是 `JavaScript` 操作二进制数据的一个接口，`ES6` 将它们纳入了 `ECMAScript` 规格，并且增加了新的方法。它们都是以数组的语法处理二进制数据，所以统称为二进制数组

二进制数组由三类对象组成。

（1）`ArrayBuffer`对象：代表内存之中的一段二进制数据，可以通过“视图”进行操作。“视图”部署了数组接口，这意味着，可以用数组的方法操作内存。

（2）`TypedArray`视图：共包括 `9` 种类型的视图，比如`Uint8Array`（无符号 `8` 位整数）数组视图, `Int16Array`（`16` 位整数）数组视图, `Float32Array`（`32` 位浮点数）数组视图等等。

（3）`DataView`视图：可以自定义复合格式的视图，比如第一个字节是 `Uint8`（无符号 `8` 位整数）、第二、三个字节是 `Int16`（`16` 位整数）、第四个字节开始是 `Float32`（`32` 位浮点数）等等，此外还可以自定义字节序

简单说，`ArrayBuffer`对象代表原始的二进制数据，`TypedArray`视图用来读写简单类型的二进制数据，`DataView`视图用来读写复杂类型的二进制数据。

`TypedArray`视图支持的数据类型一共有 `9` 种（`DataView`视图支持除`Uint8C`以外的其他 `8` 种）。

| 数据类型 | 字节长度 |	含义 | 对应的 C 语言类型 |
| ---- | ---- | ---- | ---- |
| Int8 | 1 | 8位带符号整数 | signed char |
| Uint8 |	1 |	8位不带符号整数 |	unsigned char |
| Uint8C | 1 | 8位不带符号整数（自动过滤溢出） | unsigned char |
| Int16 |	2 |	16位带符号整数 | short |
| Uint16 | 2 | 16位不带符号整数 |	unsigned short |
| Int32 | 4 | 32位带符号整数 | int |
| Uint32 | 4 | 32位不带符号的整数 |	unsigned int |
| Float32 | 4 | 32位浮点数 | float |
| Float64 | 8 | 64位浮点数 | double |

很多浏览器操作的 API，用到了二进制数组操作二进制数据，下面是其中的几个。

- `Canvas`
- `Fetch API`
- `File API`
- `WebSockets`
- `XMLHttpRequest`

### ArrayBuffer 对象

#### 概述

`ArrayBuffer`对象代表储存二进制数据的一段内存，它不能直接读写，只能通过视图（`TypedArray`视图和`DataView`视图)来读写，视图的作用是以指定格式解读二进制数据。

`ArrayBuffer`也是一个构造函数，可以分配一段可以存放数据的连续内存区域。

```js
const buf = new ArrayBuffer(32);
```

上面的代码创建了一段可读写内容的内存区域，为了读写这段内容，需要为它指定视图。`DataView`视图的创建，需要提供`ArrayBuffer`对象实例作为参数

```js
const buf = new ArrayBuffer(32);
const dataView = new DataView(buf);
dataView.getUint8(0) // 0
```

另一种`TypedArray`视图，与`DataView`视图的一个区别是，它不是一个构造函数，而是一组构造函数，代表不同的数据格式。

```js
const buffer = new ArrayBuffer(12);

const x1 = new Int32Array(buffer);
x1[0] = 1;
const x2 = new Uint8Array(buffer);
x2[0]  = 2;

x1[0] // 2
```

`TypedArray`视图的构造函数，除了接受`ArrayBuffer`实例作为参数，还可以接受普通数组作为参数，直接分配内存生成底层的`ArrayBuffer`实例，并同时完成对这段内存的赋值。

```js
const typedArray = new Uint8Array([0,1,2]);
typedArray.length // 3

typedArray[0] = 5;
typedArray // [5, 1, 2]
```

#### ArrayBuffer.prototype.byteLength

`ArrayBuffer`实例的`byteLength`属性，返回所分配的内存区域的字节长度。

```js
const buffer = new ArrayBuffer(32);
buffer.byteLength
// 32
```

#### ArrayBuffer.prototype.slice()

`ArrayBuffer`实例有一个`slice`方法，允许将内存区域的一部分，拷贝生成一个新的`ArrayBuffer`对象。

```js
const buffer = new ArrayBuffer(8);
const newBuffer = buffer.slice(0, 3);
```

除了`slice`方法，`ArrayBuffer`对象不提供任何直接读写内存的方法，只允许在其上方建立视图，然后通过视图读写

#### ArrayBuffer.isView()

`ArrayBuffer`有一个静态方法`isView`，返回一个布尔值，表示参数是否为`ArrayBuffer`的视图实例。这个方法大致相当于判断参数，是否为`TypedArray`实例或`DataView`实例。

```js
const buffer = new ArrayBuffer(8);
ArrayBuffer.isView(buffer) // false

const v = new Int32Array(buffer);
ArrayBuffer.isView(v) // true
```

### TypedArray 视图

#### 概述

`ArrayBuffer`对象作为内存区域，可以存放多种类型的数据。同一段内存，不同数据有不同的解读方式，这就叫做“视图”（`view`）。`ArrayBuffer`有两种视图，一种是`TypedArray`视图，另一种是`DataView`视图。前者的数组成员都是同一个数据类型，后者的数组成员可以是不同的数据类型。

目前，`TypedArray`视图一共包括 `9` 种类型，每一种视图都是一种构造函数。

- `Int8Array`：8 位有符号整数，长度 1 个字节。
- `Uint8Array`：8 位无符号整数，长度 1 个字节。
- `Uint8ClampedArray`：8 位无符号整数，长度 1 个字节，溢出处理不同。
- `Int16Array`：16 位有符号整数，长度 2 个字节。
- `Uint16Array`：16 位无符号整数，长度 2 个字节。
- `Int32Array`：32 位有符号整数，长度 4 个字节。
- `Uint32Array`：32 位无符号整数，长度 4 个字节。
- `Float32Array`：32 位浮点数，长度 4 个字节。
- `Float64Array`：64 位浮点数，长度 8 个字节。

这 `9` 个构造函数生成的数组，统称为`TypedArray`视图。它们很像普通数组，都有`length`属性，都能用方括号运算符（`[]`）获取单个元素，所有数组的方法，在它们上面都能使用。普通数组与 `TypedArray` 数组的差异主要在以下方面。

- `TypedArray` 数组的所有成员，都是同一种类型。
- `TypedArray` 数组的成员是连续的，不会有空位。
- `TypedArray` 数组成员的默认值为 `0`。比如，`new Array(10)`返回一个普通数组，里面没有任何成员，只是 `10` 个空位；`new Uint8Array(10)`返回一个 `TypedArray` 数组，里面 `10` 个成员都是 `0`。
- `TypedArray` 数组只是一层视图，本身不储存数据，它的数据都储存在底层的`ArrayBuffer`对象之中，要获取底层对象必须使用`buffer`属性

#### 构造函数

`TypedArray` 数组提供 `9` 种构造函数，用来生成相应类型的数组实例。

构造函数有多种用法。

（1）`TypedArray(buffer, byteOffset=0, length?)`

同一个`ArrayBuffer`对象之上，可以根据不同的数据类型，建立多个视图。

```js
// 创建一个8字节的ArrayBuffer
const b = new ArrayBuffer(8);

// 创建一个指向b的Int32视图，开始于字节0，直到缓冲区的末尾
const v1 = new Int32Array(b);

// 创建一个指向b的Uint8视图，开始于字节2，直到缓冲区的末尾
const v2 = new Uint8Array(b, 2);

// 创建一个指向b的Int16视图，开始于字节2，长度为2
const v3 = new Int16Array(b, 2, 2);
```

视图的构造函数可以接受三个参数：

- 第一个参数（必需）：视图对应的底层`ArrayBuffer`对象。
- 第二个参数（可选）：视图开始的字节序号，默认从 `0` 开始。
- 第三个参数（可选）：视图包含的数据个数，默认直到本段内存区域结束。

（2）`TypedArray(length)`

视图还可以不通过`ArrayBuffer`对象，直接分配内存而生成。

```js
const f64a = new Float64Array(8);
f64a[0] = 10;
f64a[1] = 20;
f64a[2] = f64a[0] + f64a[1];
```

（3）`TypedArray(typedArray)`

`TypedArray` 数组的构造函数，可以接受另一个`TypedArray`实例作为参数。

```js
const typedArray = new Int8Array(new Uint8Array(4));
```

（4）`TypedArray(arrayLikeObject)`

构造函数的参数也可以是一个普通数组，然后直接生成`TypedArray`实例。

```js
const typedArray = new Uint8Array([1, 2, 3, 4]);
```

#### 数组方法

普通数组的操作方法和属性，对 `TypedArray` 数组完全适用。

- `TypedArray.prototype.copyWithin(target, start[, end = this.length])`
- `TypedArray.prototype.entries()`
- `TypedArray.prototype.every(callbackfn, thisArg?)`
- `TypedArray.prototype.fill(value, start=0, end=this.length)`
- `TypedArray.prototype.filter(callbackfn, thisArg?)`
- `TypedArray.prototype.find(predicate, thisArg?)`
- `TypedArray.prototype.findIndex(predicate, thisArg?)`
- `TypedArray.prototype.forEach(callbackfn, thisArg?)`
- `TypedArray.prototype.indexOf(searchElement, fromIndex=0)`
- `TypedArray.prototype.join(separator)`
- `TypedArray.prototype.keys()`
- `TypedArray.prototype.lastIndexOf(searchElement, fromIndex?)`
- `TypedArray.prototype.map(callbackfn, thisArg?)`
- `TypedArray.prototype.reduce(callbackfn, initialValue?)`
- `TypedArray.prototype.reduceRight(callbackfn, initialValue?)`
- `TypedArray.prototype.reverse()`
- `TypedArray.prototype.slice(start=0, end=this.length)`
- `TypedArray.prototype.some(callbackfn, thisArg?)`
- `TypedArray.prototype.sort(comparefn)`
- `TypedArray.prototype.toLocaleString(reserved1?, reserved2?)`
- `TypedArray.prototype.toString()`
- `TypedArray.prototype.values()`

注意，`TypedArray` 数组没有`concat`方法。如果想要合并多个 `TypedArray` 数组，可以用下面这个函数。

```js
function concatenate(resultConstructor, ...arrays) {
  let totalLength = 0;
  for (let arr of arrays) {
    totalLength += arr.length;
  }
  let result = new resultConstructor(totalLength);
  let offset = 0;
  for (let arr of arrays) {
    result.set(arr, offset);
    offset += arr.length;
  }
  return result;
}

concatenate(Uint8Array, Uint8Array.of(1, 2), Uint8Array.of(3, 4))
// Uint8Array [1, 2, 3, 4]
```

