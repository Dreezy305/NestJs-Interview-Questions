# NestJs-Interview-Questions

Please give this project a :star: if you like it. Pull Request are highly appreciated. You can follow me on twitter [@miles_slades](https://twitter.com/miles_slades) for more updates.

Note => This project is specific to NestJS.

# Table of Contents

| No  | Question                                                                                                                      |
| --- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is Nestjs](#what-is-nestjs)                                                                                             |
| 2   | [What are the major features of Nestjs](#what-are-the-major-features-of-nestjs)                                               |
| 3   | [How does Nestjs work](#How-does-nestjs-work)                                                                                 |
| 4   | [What are the HTTP Frameworks supported by Nestjs](#What-are-the-HTTP-Frameworks-supported-by-Nestjs)                         |
| 5   | [What default Framework is used by Nestjs](#What-default-framwork-is-used-by-Nestjs)                                          |
| 6   | [How can you specify the Framework to use in Nestjs](#How-can-you-specify-the-Framework-to-use-in-Nestjs)                     |
| 7   | [What is responsible for handling incoming requests in Nestjs](#What-is-responsible-for-handling-incoming-requests-in-Nestjs) |
| 8   | [What are Decorators in Nestjs](#What-are-decorators-in-Nestjs)                                                               |
| 9   | [What are Controllers in Nestjs](#What-are-controllers-in-Nestjs)                                                             |
| 10  | [What is a Request object](#What-is-a-request-object)                                                                         |
| 11  | [How do we access Request object in Nestjs](#How-do-we-access-request-object-in-nestjs)                                       |
| 12  | [How do we access properties of Request object in Nestjs](#How-do-we-access-properties-of-request-object-in-nestjs)           |
| 13  | [What are providers in Nestjs](#What-are-providers-in-nestjs)                                                                 |
| 14  | [What is Dependency Injection](#What-is-dependency-injection)                                                                 |
| 15  | [What are the key concepts of Dependency Injection](#What-are-the-key-concepts-of-dependency-injection)                       |
| 16  | [How do we create modules in Nestjs](#How-do-we-create-modules-in-Nestjs)                                                     |
| 17  | [What are modules in Nestjs](#What-are-modules-in-Nestjs)                                                                     |
| 18  | [What are the fatures of modules in Nestjs](#What-are-the-features-of-modules-in-Nestjs)                                      |
| 18  | [What are the fatures of modules in Nestjs](#What-are-the-features-of-modules-in-Nestjs)                                      |
| 19  | [What is circular dependency in Nestjs](#What-is-circular-dependency-in-Nestjs)                                               |
| 20  | [What is forward Ref in Nestjs](#What-is-forward-ref-in-Nestjs)                                                               |
| 21  | [What is forward Ref in Nestjs](#What-is-forward-ref-in-Nestjs)                                                               |

### What is Nestjs

Nest (NestJS) is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with and fully supports TypeScript (yet still enables developers to code in pure JavaScript) and combines elements of OOP (Object Oriented Programming), FP (Functional Programming), and FRP (Functional Reactive Programming).

### What are the major components of Nestjs

The main components of a NestJS application are the controller, service, and module.

### What are the HTTP Frameworks supported by Nestjs

Out of the box, Nestjs supports 2 frameworks which are fastify and express. As a developer, you can choose to use any one of frameworks that suits your use case

### What default Framework is used by Nestjs

Under the hood, Nest makes use of express by default and optionally can be configured to use Fastify as well.

### How can you specify the Framework to use in Nestjs

In your `main.ts` file, create a NestJS application using the `NestFactory` method:

```typescript
import { NestFactory } from "@nestjs/core";
import { NestExpressApplication } from "@nestjs/platform-express";
import { AppModule } from "./app.module";

async function bootstrap() {
  // IF YOU WANT TO USE EXPRESS, DO THIS.
  const app = await NestFactory.create<NestExpressApplication>(AppModule);

  // IF YOU WANT TO USE FASTIFY
  const app = await NestFactory.create<NestFastifyApplication>(AppModule);
  await app.listen(3000);
}
bootstrap();
```

### What is responsible for handling incoming requests in Nestjs

In NestJS, Controllers are responsible for handling incoming requests and returning responses to the client. The routing mechanism controls which controller receives which requests. Frequently, each controller has more than one route, and different routes can perform different actions.

### What are Decorators in Nestjs

Decorators are responsible for associating classes with required metadata. Hence, enabling Nest to create a routing map

### What are Controllers in Nestjs

Controllers are responsible for handling incoming requests and returning responses to the client.

```typescript
import { Controller, Get } from "@nestjs/common";

@Controller("auth")
export class AuthController {
  @Get()
  findAllUsers(): string {
    return "This controller returns users";
  }
```

### What is a Request object

The req object represents the HTTP request and has properties for the request query string, parameters, body, HTTP headers etc. In other words it contain client request details.

### How do we access Request object in Nestjs

Request object can be accessed by adding the @Req() decorator to the handler's signature.

```typescript
import { Controller, Get, Req } from "@nestjs/common";
import { Request } from "express";

@Controller("users")
export class CatsController {
  @Get()
  findAllUsers(@Req() request: Request): string {
    return "This returns all users";
  }
}
```

### What are providers in Nestjs

Providers are classes that are used to encapsulate and provide specific functionalities or services within an application. They are a fundamental concept in NestJS dependency injection system, which allows for the efficient management of dependencies and the modularization of code.

### What is Dependency Injection

It's a technique where by a the output of a class is the input of another class. in other words, a class or object provides dependencies needed by another class. It allows for better separation of concerns, making code more modular, testable, and maintainable.

### What are the key concepts of Dependency Injection

The key concepts of Dependency Injection include:

1. Dependency: A class or service that another class relies on. For example, if a class A needs an instance of class B to function, B is a dependency of A
2. Client: It is the class that will receive the injected dependency.
3. Injector: The injector is responsible for providing the necessary dependencies to the client. It acts as an intermediary, resolving and injecting the dependencies into the client class.

### How do we create modules in Nestjs

```typescript
nest g module users
```

### What are modules in Nestjs

A module is class anotated with `@Module()` decorator. It serves as a way to organize your code into distinct, cohesive units, each responsible for a particular feature of your application. Modules encapsulate providers, controllers, and other modules, promoting a modular architecture and separation of concerns.

### What are the fatures of modules in Nestjs

1. Providers: Services, repositories, or any other class that should be injected via dependency injection.
2. Controllers: The classes that handle incoming requests and return responses to the client.
3. Exports: The providers that are available to other modules when imported.
4. Imports: Other modules that are required by the current module.

### What is circular dependency in Nestjs
It occurs when two classes depend on one another. e.g class A needs class B, and class B also need class A

# Disclaimer

The primary purpose of setting up this project is for you to get an insight into how nestjs questions might be structured. This doesn't necessarily represent the nature of nestjs interviews across various companies and neither is it a standard that represents nestjs questions.

Goodluck in your interview! :blush:
