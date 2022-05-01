# Getting started with NestJS

## Node.js ecosystem
- node by design has minimilistic setup and developers are incharge of setting up
- developer can handle routing, API calls, setting up web sockets, code organization, etc
- There are many frameworks built on top of Node.js (most notably Express.js), but there is still alot of developer effort required
- Thus, the ultimate flexibility can be a bit of double edged sword.
### How is NestJS helping in this situation
- NestJS tries to tackle some of these problems by creating an abstraction or overall Framework around Node.js
- It provides an out of the box application architecture that allows developers and teams to create highly testable, scalable, loosely coupled, and easily maintainable.
- Nest uses **Express** by default under the hood, but it can be replaced with other frameworks such as **fastify**
## Key features of NestJS
- It is a layer above Node.js, abstracting away difficult tasks, tools, and boilerplate code
- It also provides a full fledged toolkit for the application development
- We can built Rest API's, MVC applications, microservices, GraphQL applications, web sockets, and even CLI's and cron jobs.
- It also provides a **dependency Injection** system which lets developer abstracting dependencies easily

## Installing NestJS CLI
- Get `current version` or `latest LTS version` of node in your system
- Install NestJS CLI from below command
```
npm i -g @nestjs/cli
```
- check if Nest is installed correctly
```
nest --version
```
### What is Nest CLI
- It is companion tool for NestJS that helps it generate run, compile and bundle our applications
- `nest --help` to see all commands of `Nest CLI`

## Generating our first NestJS Application
- Nest CLI will do alot of heavy working for us, for example file structuring, installation, configuration and so on...
- to create our first application
```
nest new
```
- then Nest CLI will ask us to give a name of the project
- In this pathway we will be creating a REST API related to coffee, so let's give it name, `iluvcoffee`
- Then select preffered package manager
- Now it will take some time as Nest is generating required files for us to run the project
- Once the installation is complete then change the directory to `cd iluvcoffee`
- to run the application created just run the following command
```
npm run start
```
- This command will start our app, firing an `HTTP server` listening on `por

## What's inside a NestJS Application
- Core of our application lives inside our `src` AKA `source` directory
### Inside Source Directory
- Our entire application starts with `main.ts` file
- the app is created with following syntax
```
const app = await NestFactory.create(AppModule);
```
- Here app is created by NestFactory which is taking an `AppModule`.
- With this application reference we can listen and bootstrap our application on port 3000
- In this entry point of our application alot of root level work is done
### What is AppModule
- It is the `root module` for our application containing everything our app needs to run.
- This root module can also contain other small modules and features themselves when brought together inside the AppModule we get our complete application
- Don't get overwhelmed with this, all of these will be covered in depth later on.
#### Exploring AppModule
- `ctrl + click` the `AppModule` to goto the `app.module.ts` file
- you will see that is is regular class with NestJS `@Module` typescript decorator on the top of it
    - Decorators are simply functions that apply logic
    - Decorators can be applied to classes, methods, properties and even parameters.
    - NestJS utilizes decorators extensively.
- Inside @Module we have encapsulated everthing important to this module's context
- You can see that we have `controllers` and `providers` included with the starter NestJS application
#### Exploring AppController
- `ctrl + click` the `AppController` to goto `app.controller.ts` file
- Similar to the module, `NestJS controller` is also just a `class` but with differnt `@Controller` decorator on the top.
- We will see controllers in depth in future, for now just know that controllers handle specific request of our application.
- In this file we can see that it is depending on `AppService` provider to seperate out the `business logic` from controller.
- This `AppController` class is handling a Get request that is setup for us.
    - This get request utilizes `appService` to call `getHello()`
- If we goto `app.service.ts`, i.e, `AppService` Provider for the application, we can see that `getHello()` is returning a 'Hello World!' string.
- This is a very simple application but as we will grow this application we'll see how Nests' modular project architecture encourages us to group features such as routes, services, etc. into their own modules.
    - This helps us maintain high level of reusability, testability and helps to reduce dis-organized code in our applications.