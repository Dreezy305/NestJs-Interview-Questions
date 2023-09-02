# NestJs-Interview-Questions

Pls give this project a :star: if you like it. Pull Request are highly appreciated. You can follow me on twitter [@miles_slades](https://twitter.com/miles_slades) for updates.

Note: This project is specific to nestjs.

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
| 9   | [What are Controllers in Nestjs](#What-are-controllers-in-Nestjs)                                                               |
| 10   | [What is a Request Object](#What-is-a-request-object)                                                               |

### What is Nestjs

Nest (NestJS) is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with and fully supports TypeScript (yet still enables developers to code in pure JavaScript) and combines elements of OOP (Object Oriented Programming), FP (Functional Programming), and FRP (Functional Reactive Programming).

### What are the major comppnents of Nestjs

The main components of a NestjS application are the controller, service, and module.

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
  // IF YOU WANT TO USE EXPRESS
  const app = await NestFactory.create<NestExpressApplication>(AppModule);

  // IF YOU WANT TO USE FASTIFY
  const app = await NestFactory.create<NestFastifyApplication>(AppModule);
  await app.listen(3000);
}
bootstrap();
```

### What is responsible for handling incoming requests in Nestjs

In Nestjs, Controllers are responsible for handling incoming requests and returning responses to the client. The routing mechanism controls which controller receives which requests. Frequently, each controller has more than one route, and different routes can perform different actions.

### What are Decorators in Nestjs

Decorators are responsibled for associating classes with required metadata. Hence, enabling Nest to create a routing map

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
}
```

### What is a Request object

The req object represents the HTTP request and has properties for the request query string, parameters, body, HTTP headers etc. In other words it contain client request details.

# Disclaimer

The primary purpose of setting up this project is for you to get an insight into how nestjs questions might be structured. This doesn't neccessarily represent the nature of nestjs interviews across various companies and neither is it a standard that represents nestjs questions.

Goodluck in your interview :blush:
