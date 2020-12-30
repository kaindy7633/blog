# Nestjs起步：概述

## 介绍

`Nest` 是一个用于构建高效，可扩展的 `Node.js` 服务器端应用程序的框架。它使用渐进式 JavaScript，内置并完全支持 TypeScript, 并结合了 `OOP`（面向对象编程），`FP`（函数式编程）和 `FRP`（函数式响应编程）的元素。

`Nest` 提供了一个开箱即用的应用程序架构，允许开发人员和团队创建高度可测试，可扩展，松散耦合且易于维护的应用程序。

## 安装

官方提供了三种安装方式：

- 使用 `CLI` 安装

- 使用 `Git` 安装

- 手动创建

这里仅说明一下使用 `CLI` 的安装方式，其他方式很少使用，可参考官方文档 (<a href="https://docs.nestjs.cn/7/introduction?id=%e5%ae%89%e8%a3%85" target="_blank">安装</a>)

使用 `npm`

```bash
# 全局安装 @nestjs/cli 目前还不清楚是否可以使用 npx 进行安装
$ npm i -g @nestjs/cli

# 使用全局功能函数 nest 进行项目创建
$ nest new project-name
```

使用 `yarn`

```bash
$ yarn global add @nestjs/cli
$ nest new project-name
```

安装完成之后打开浏览器并导航到 `http://localhost:3000/`

## 语言

`Nest` 完美支持 `Typescript`，后面的文档和开发都使用 `Typescript`，故不再降级使用 `JavaScript`。

## 系统支持

请确保系统安装了 `Node.js`， 并保持其版本在 10.13.0 以上， 不需要安装拓展，不需要额外安装 `nginx/apache`

## 项目结构

在创建好的项目中，我们关注 `src` 开发目录，其中结构如下：

```
src
├── app.controller.spec.ts
├── app.controller.ts
├── app.module.ts
├── app.service.ts
└── main.ts
```

| --- | --- |
| `app.controller.spec.ts` | app控制器的单元测试文件 |
| `app.controller.ts` |	带有单个路由的基本控制器示例。 |
| `app.module.ts` |	应用程序的根模块。 |
| `app.service.ts` | 被注入的Service |
| `main.ts` |	应用程序入口文件。它使用 `NestFactory` 用来创建 `Nest` 应用实例。 |

`main.ts` 包含一个异步函数，它负责引导我们的应用程序：

```ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```

## 平台

`Nest` 可以在创建适配器后使用任何 `Node HTTP `框架。 有两个支持开箱即用的 `HTTP` 平台：`Express`(默认) 和 `Fastify`

## 运行

一般我们会使用 `npm run start:dev` 或 `yarn start:dev` 来启动开发

